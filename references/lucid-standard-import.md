# Lucid Standard Import — Format Constraints & Recipe

Guidance for generating diagrams **natively in Lucidchart** via the Lucid MCP, rather than as `.drawio` files.

> **Read this before writing any Lucid JSON.** None of the constraints below are documented in the `lucid://diagram-specification` resource. Assuming Lucid behaves like draw.io reliably produces overlapping shapes, collapsed line breaks, and inconsistent font sizes.

---

## 1. Hard constraints

### Text

| Constraint | Consequence | Required approach |
|---|---|---|
| **`\n` is silently ignored** | `"A\nB\nC"` renders as `A B C`, reflowed and wrapped mid-phrase | **One text shape per visual line.** Never put multiple bullets in one shape. |
| **`fontSize` does not exist** | No font-size control anywhere in the format | Accept it. Plan for a manual pass (see §6). |
| **`style` accepts only `fill`, `stroke`, `textColor`** | No font family, weight, alignment, or size | Convey hierarchy through colour and box size only |
| **`text`-type shapes reject `style` entirely** | Standalone text is always default dark grey | Use `rectangle` if you need coloured text |
| **Text auto-fits to the bounding box, driven by WIDTH** | A short string in a wide box renders huge; a long string in a narrow box renders tiny | Keep sibling text shapes at similar width **and** similar string length |
| **Box height is a weak lever** | Raising detail text from `h=18` to `h=26` barely changed rendered size | Do not try to fix type size by growing boxes |
| **No emoji** | Renders as black boxes | Use words. Ignore `icon-mapping.md` — it is emoji-based and draw.io-only. |

### Layout

- **`assistedLayout: false` on every container, AND `use_assisted_layout: false` at the top level.** Otherwise the layout engine reflows your hand-computed absolute coordinates and shapes land on top of each other. This is the single most common cause of a broken diagram.
- **Container titles render ABOVE / overlapping the container's top edge.** Leave a **~60px vertical gutter** between vertically stacked containers, and between horizontally adjacent containers whose titles could meet.
- Every child bounding box must fit **strictly** inside its parent.
- For `swimLanes`, usable interior starts below `titleBar.height`.
- For **vertical** `swimLanes`, `titleBar.height` is where the **lane titles** render. The swimlane's own `text` property does **not** visibly appear — add a separate label shape if you need a group title.
- Endpoint `position: {x, y}` (0–1 fractions) must be present on **BOTH** endpoints or **NEITHER**. Mixing them throws.

### Shape types that work

`rectangle`, `text`, `roundedRectangleContainer`, `rectangleContainer`, `swimLanes`

---

## 2. Layout pattern: horizontal bands

**Use bands. Do not use a side rail of tool boxes.**

A right-hand column of cross-cutting tools (orchestration, BI, governance) sits at the same y-range as the main platform content, which forces long diagonal connectors straight through your containers and is the top cause of unreadable output.

```
+---------------------------------------------------+
| BAND 1: Orchestration & Identity                  |   dbt, Airflow, AD/SCIM
+---------------------------------------------------+
                        |  (short vertical drops)
+----------+  +-------------------------------------+
| Sources  |  | Platform (Snowflake)                |
|          |  |  +-------------------------------+  |
|          |  |  | swimLanes: medallion layers   |  |
|          |  |  +-------------------------------+  |
|          |  |  +-------------------------------+  |
|          |  |  | nested container: sub-platform|  |
|          |  |  +-------------------------------+  |
+----------+  +-------------------------------------+
                        |  (short vertical drops)
+---------------------------------------------------+
| BAND 3: Consumption & Governance                  |   BI, catalog, marketplace
+---------------------------------------------------+
```

**Place each consumer directly beneath its producer** so every cross-band connector is a short vertical drop rather than a diagonal.

---

## 3. Geometry recipe

Proven numbers. Start here and scale.

```
Canvas             ~1740 x 1080

Band 1 (top)       x=40   y=70   w=1660  h=145
Left column        x=40   y=270  w=280   h=600
Main container     x=380  y=270  w=1320  h=600     <- 60px gutter from left column
  swimLanes        x=400  y=300  w=1280  h=250     titleBar.height=36
                   lanes: N lanes, widths summing EXACTLY to container w
  nested container x=400  y=595  w=1280  h=250     <- 45px below swimlane bottom
    inner group    x=1025 y=615  w=640   h=215     <- fits strictly inside
Band 3 (bottom)    x=40   y=930  w=1660  h=150     <- 60px below main container
```

**Card + detail-text unit** (repeat this everywhere):

```
title card    x=X      y=Y       w=W      h=40    type: rectangle, styled
detail line 1 x=X+6    y=Y+46    w=W-12   h=26    type: text
detail line 2 x=X+6    y=Y+74    w=W-12   h=26    type: text
detail line 3 x=X+6    y=Y+102   w=W-12   h=26    type: text
```

- Detail text: `h=26`, **28px y-spacing**, inset 6px, width `-12px` from parent card.
- Keep detail strings to **2–4 words**. Long strings shrink; short strings in the same-width box stay consistent.

---

## 4. Colour mapping

Same palette as `style-guide.md`, expressed as Lucid `style` objects.

```json
// Snowflake internal
"style": {"fill": {"type":"color","color":"#FFFFFF"},
          "stroke":{"color":"#29B5E8","width":2,"style":"solid"},
          "textColor":"#11567F"}

// External / third-party
"style": {"fill": {"type":"color","color":"#FFFFFF"},
          "stroke":{"color":"#FF9F36","width":2,"style":"solid"},
          "textColor":"#E07800"}

// Accent (sparingly, max 1-2 elements)
"style": {"fill": {"type":"color","color":"#E8DCFF"},
          "stroke":{"color":"#7254A3","width":2,"style":"solid"},
          "textColor":"#7254A3"}
```

Container fills: `#F5FBFE` platform, `#FFF8ED` external bands, `#F3EEFF` accent containers.
Swimlane headers: `headerFill: "#11567F"`, `laneFill: "#F5FBFE"`.
Connectors: `#29B5E8` internal, `#FF9F36` external, `width: 3` for major flows, `style: "dashed"` for control/orchestration.

---

## 5. API mechanics

- Read the `lucid://diagram-specification` resource **before every** create call.
- Required params: `standard_import_json` (NOT `document_json`) and `product: "lucidchart"`.
- **Intermittent HTTP 500 with no useful message — retry the identical payload.** This is not a payload bug; do not waste turns bisecting the JSON.

---

## 6. Verification loop — mandatory

**Do not report success on a diagram you have not looked at.**

1. Create the document.
2. Call `mcp_lucidcharts_lucid_export_document_as_PNG` with the returned `documentId`.
3. **Inspect the returned image.** Check specifically for: overlapping shapes, container titles colliding with neighbours, connectors crossing through containers, text overflowing its container, and text-size inconsistency.
4. Fix and repeat before handing off.

Skipping this step is how a diagram with two unreadable layers gets described as "clean."

---

## 7. Handoff — state the font limitation up front

Because `fontSize` is unreachable, the delivered diagram will have correct structure but uneven text size. **Tell the user this when you deliver, not after they notice:**

> Structure is final. Lucid's import format has no font-size control, so to even out the type: open the edit link, `Cmd+A`, and set the font size to 10pt in the toolbar. Roughly 30 seconds.

Also note which `style-guide.md` rules are **not achievable** in Lucid, so their absence reads as a known tradeoff rather than an oversight:

| style-guide rule | Lucid status |
|---|---|
| Typography table (all `fontSize` values) | **Unachievable** — no font-size field |
| Header bar, 22px bold white title | Achievable as a styled `rectangle`; text size not controllable |
| Footer legend with swatches | Achievable as small styled rectangles |
| Font: Helvetica / Courier New | **Unachievable** — no font-family field |
| 10px grid snap | Achievable — keep all coordinates on multiples of 10 where practical |
| Emoji icons | **Do not use** — renders as black boxes |
