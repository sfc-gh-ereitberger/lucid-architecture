---
name: lucid-architecture
description: "Generate polished Snowflake-branded architecture diagrams, natively in Lucidchart (default) or as draw.io files. Use when: $LucidArchitecture, architecture diagram, lucid, lucidchart, draw.io, reference architecture, demo diagram, solution architecture. Auto-analyzes session context to detect Snowflake objects and generates production-quality diagrams with official brand colors."
---

# LucidArchitecture

Generate polished, Snowflake-branded architecture diagrams from session context — natively in Lucidchart or as a draw.io file.

## When to Use

- User invokes `$LucidArchitecture`
- User asks for an architecture diagram, reference architecture, Lucid diagram, or draw.io file
- End of a demo-building session when the user wants a visual summary

## Output target

**Default to Lucidchart.** Choose draw.io only when precise typography matters more than a native Lucid document.

| Target | Choose when | Tradeoff |
|---|---|---|
| **Lucidchart** (default) | Sharing, collaborative editing, or presenting from Lucid | No `fontSize` control — needs a ~30s manual font pass on delivery |
| draw.io | Exact font sizes / typography are required in the artifact | A local file, not a Lucid document |

If the target is genuinely unclear, ask once as part of the Step 2 stopping point rather than as a separate question.

## Workflow

```
Start
  |
Step 1: Analyze Session Context
  |
Step 2: Recommend Diagram Style (+ confirm output target)
  |  <- STOPPING POINT: user confirms or customizes
Step 3: Gather Component Details
  |  <- STOPPING POINT: user confirms component list
Step 4: Generate diagram
  |    4A -> Lucidchart via MCP   (default)
  |    4B -> .drawio file
  |
Step 5: Verify render, then offer refinements
  |  <- STOPPING POINT: iterate or done
Done
```

---

### Step 1: Analyze Session Context

**Goal:** Detect what was built in this Cortex Code session.

**Actions:**

1. **Scan conversation history** for Snowflake objects created or referenced:

| Category | Look For |
|----------|----------|
| Storage | CREATE TABLE, CREATE VIEW, CREATE STAGE, CREATE ICEBERG TABLE, database names |
| Cortex AI | CREATE CORTEX SEARCH SERVICE, Cortex Analyst, Cortex Agent, semantic views |
| Data Engineering | CREATE TASK, CREATE STREAM, CREATE PIPE, Snowpipe, Dynamic Tables |
| Integrations | CREATE EXTERNAL ACCESS INTEGRATION, MCP, API integrations, external URLs |
| Applications | Streamlit apps, Snowsight dashboards, Notebooks |
| Governance | Masking policies, row access policies, tags, network policies |

2. **Identify external dependencies**: third-party APIs, cloud services, SaaS tools, web scrapers, data providers.

3. **Count components** to determine complexity:
   - Simple (3-5 components)
   - Medium (6-10 components)  
   - Detailed (10+ components)

4. **Summarize findings** for the user.

**Output:** Component inventory with internal/external classification.

---

### Step 2: Recommend Diagram Style

**Goal:** Suggest the best diagram layout based on what was detected.

**Actions:**

1. **Select recommended grouping** using this logic:

| Session Pattern | Recommended Template | Why |
|----------------|---------------------|-----|
| Agent + tools + data + UI | `use-case-architecture` | Shows end-to-end use case flow |
| Multiple Snowflake services, no single agent focus | `service-focused` | Groups by service category |
| ETL/pipeline focus (pipes, streams, tasks) | `technical-architecture` | Shows data flow through zones |
| Multiple user personas or consumer-facing | `end-user-led` | Starts from user needs |
| **Default / unclear** | `use-case-architecture` | Most versatile layout |

2. **Present recommendation with all options:**

**STOPPING POINT** — Ask the user:

```
Based on your session, I detected [N] components ([list key ones]).

I recommend: **[Template Name]** — [one-line reason]

Available layouts:
1. Use Case Architecture — Data → Tools → Agent → Interface (best for agent demos)
2. Technical Architecture — Sources → Ingestion → Storage → Processing → Consumption
3. Service Focused — Grouped by Snowflake service: Cortex AI, Data Eng, Storage, Apps
4. End User Led — Personas → Interfaces → Processing → Data (right-to-left)

Complexity: Simple / Medium / Detailed

Which layout? (or confirm recommendation)
```

**Wait for user response. Do NOT proceed without confirmation.**

---

### Step 3: Gather Component Details

**Goal:** Map detected objects to template placeholders.

**Actions:**

1. **Load the selected template** from `templates/`:
   - `use-case-architecture.drawio`
   - `technical-architecture.drawio`
   - `service-focused.drawio`
   - `end-user-led.drawio`

2. **Load reference files** for styling guidance:
   - `references/style-guide.md` — Brand colors and layout rules (**both** targets)
   - `references/lucid-standard-import.md` — **REQUIRED for Lucid target.** Format constraints and geometry recipe.
   - `references/drawio-components.md` — Parameterized XML snippets (draw.io target only)
   - `references/icon-mapping.md` — Icon selection (draw.io target only; emoji break in Lucid)

3. **Map session objects to placeholders.** Build a mapping table:

| Placeholder | Value | Color Category |
|-------------|-------|---------------|
| `{{USE_CASE_TITLE}}` | From session context | — |
| `{{DATABASE_NAME}}` | Detected DB name | Internal (blue) |
| `{{TABLE_1}}` ... `{{TABLE_N}}` | Detected tables | Internal (blue) |
| `{{AGENT_NAME}}` | Agent name if exists | Internal (dark blue) |
| `{{EXTERNAL_1_NAME}}` | Third-party service | External (orange) |
| ... | ... | ... |

4. **Present component mapping:**

**STOPPING POINT** — Show the user the proposed component list and ask for confirmation:

```
Here's what I'll include in the diagram:

INTERNAL (Snowflake Blue):
- [list internal components]

EXTERNAL (Valencia Orange):
- [list external components]

AGENT/CORE (Mid Blue):
- [agent details if applicable]

Title: "[Use Case Title] | Reference Architecture"

Shall I proceed, or would you like to adjust?
```

**Wait for user confirmation.**

---

### Step 4A: Generate Lucidchart Diagram (default)

**Goal:** Produce a native Lucid document via the Lucid MCP.

**Read `references/lucid-standard-import.md` first.** It is not optional — the format has undocumented constraints (newlines ignored, no `fontSize`, text auto-fits to width, assisted layout overrides coordinates) that will otherwise cost several rebuild cycles.

**Actions:**

1. Read the `lucid://diagram-specification` resource (required before every create call).
2. **Lay out in horizontal bands**, per §2 of the Lucid reference. Do not use a side rail of tool boxes.
3. Build geometry from the §3 recipe. Set **`assistedLayout: false` on every container** and `use_assisted_layout: false` at the top level.
4. **One text shape per visual line** — `h=26`, 28px spacing. Never rely on `\n`.
5. Apply colours from §4. No emoji.
6. Route connectors with explicit `position` anchors on **both** endpoints; place each consumer beneath its producer.
7. Call `mcp_lucidcharts_lucid_create_diagram_from_specification` with `standard_import_json` and `product: "lucidchart"`. On HTTP 500, retry the identical payload.

**Output:** Lucid document ID, plus view and edit URLs.

---

### Step 4B: Generate .drawio File

**Goal:** Produce the final draw.io XML file.

**Actions:**

1. **Start from the selected template** file as the base structure.

2. **Replace all `{{PLACEHOLDER}}` values** with the confirmed component details.

3. **Apply color rules strictly:**

| Component Type | Border | Fill Accent | Icon BG | Title Color |
|---------------|--------|-------------|---------|-------------|
| Snowflake internal | `#29B5E8` | `#E8F6FC` | `#E8F6FC` | `#11567F` |
| External / third-party | `#FF9F36` | `#FFF8ED` | `#FFF8ED` | `#E07800` |
| Core agent / processing | `#11567F` | `#1A6B94` | `#11567F` | `#FFFFFF` |
| Accent (sparingly) | `#7254A3` | `#E8DCFF` | `#E8DCFF` | `#7254A3` |

4. **Adjust template as needed:**
   - Add/remove table rows to match actual table count
   - Add/remove component cards to match complexity
   - Add/remove capability rows in agent container
   - Adjust layer widths if components need more/less space
   - Recompute x/y positions when adding/removing elements (10px grid)

5. **Ensure all arrows connect logically** between components with descriptive labels.

6. **Add/remove layers** to match the component count:
   - Simple: 3 layers (collapse middle layers)
   - Medium: 4 layers (standard template)
   - Detailed: 5+ layers (split layers or add sub-sections)

7. **Write the file** to the user's working directory:
   - Default: `./architecture.drawio`
   - Or user-specified path

8. **Validate XML** is well-formed (all tags closed, IDs unique).

**Output:** Complete `.drawio` file written to disk.

---

### Step 5: Verify Render, Then Offer Refinements

**Goal:** Confirm the diagram actually renders correctly, then let the user iterate.

**For the Lucid target, verification is mandatory before presenting:**

1. Call `mcp_lucidcharts_lucid_export_document_as_PNG` with the returned `documentId`.
2. **Inspect the image.** Check for overlapping shapes, container titles colliding with neighbours, connectors crossing through containers, text overflowing, and text-size inconsistency.
3. Fix and re-verify before handing off.

**Never describe a diagram as clean without having looked at the render.**

**STOPPING POINT** — Present the result and ask:

```
Architecture diagram: [Lucid view/edit URLs, or file path]

[Lucid only] Lucid's import format has no font-size control, so to even out the
type: open the edit link, Cmd+A, set font size to 10pt. About 30 seconds.

Would you like to:
1. Adjust components (add/remove/rename)
2. Change layout style
3. Modify colors or styling
4. Done — looks good!
```

**If user requests changes:** Return to the relevant step and regenerate.
**If user is satisfied:** Workflow complete.

---

## Styling Rules (Quick Reference)

These are NON-NEGOTIABLE for the **draw.io** target. For the **Lucid** target, see the achievability table in §7 of `references/lucid-standard-import.md` — font sizes, font family, and emoji icons are not reachable through Lucid's import format, and text auto-fits to its box.

- **Header**: Full-width bar `#29B5E8`, snowflake logo in white circle, title 22px bold white
- **Layers**: `#F5FBFE` bg, `#11567F` 2px border, badge in `#11567F`
- **Internal cards**: White bg, `#29B5E8` 2px border, title `#11567F`
- **External cards**: White bg, `#FF9F36` 2px border, title `#E07800`
- **Agent layer**: Dark `#11567F` bg, inner cards `#1A6B94`
- **Purple accent**: `#7254A3` — use ONLY for special highlights, max 1-2 elements
- **Arrows**: `#29B5E8` internal, `#FF9F36` external, 2px stroke, classic endArrow
- **Footer**: Color legend with 4 brand swatches, divider line `#E0E0E0`
- **Icons**: Emoji by default (zero dependencies). See `references/icon-mapping.md`
- **Grid**: 10px snap. All positions must align to 10px grid.
- **Font**: Helvetica. Code/paths in Courier New.

---

## Stopping Points Summary

- **Step 2**: After recommending layout — wait for user to confirm or choose
- **Step 3**: After presenting component mapping — wait for user to confirm
- **Step 5**: After generating file — wait for user to iterate or approve

**Resume rule:** On user approval, proceed directly to next step.

---

## Output

A production-quality diagram — a Lucid document (default) or a `.drawio` XML file — that:
- Opens cleanly in Lucidchart, or in draw.io / the VS Code draw.io extension
- Uses official Snowflake brand colors
- Shows clear left-to-right (or right-to-left for end-user-led) data flow
- Distinguishes internal (blue) from external (orange) components
- Includes header, layer containers, component cards, arrows, and footer legend
