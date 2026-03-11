# Snowflake draw.io Style Guide

## Brand Colors

| Token | Hex | Usage |
|-------|-----|-------|
| Snowflake Blue | `#29B5E8` | Primary — internal Snowflake components, CTAs, arrows, header bar |
| Mid Blue | `#11567F` | Layer badges, dark containers, agent backgrounds, component titles |
| Valencia Orange | `#FF9F36` | **External** data sources, third-party integrations, external arrows |
| Dark Orange | `#E07800` | External component titles, orange accent text |
| Purple Moon | `#7254A3` | Accent — use **sparingly** for highlights, special callouts |
| Light Purple | `#E8DCFF` | Purple tint backgrounds (sparingly) |
| Medium Gray | `#5B5B5B` | Body text, descriptions |
| Light Gray | `#999999` | Footer text, muted labels |
| Star Blue | `#75CDD7` | Light accent highlights (sparingly) |

## Background Fills

| Fill | Hex | Usage |
|------|-----|-------|
| Layer background | `#F5FBFE` | Light blue wash for Snowflake layer containers |
| Card internal bg | `#E8F6FC` | Internal component icon backgrounds, highlight areas |
| Card external bg | `#FFF8ED` | External/orange component icon backgrounds |
| White | `#FFFFFF` | Card bodies, page background |
| Border accent | `#B8D4E8` | Table row borders inside database containers |

## Canvas & Layout

- **Page size**: 1800×900 (landscape)
- **Flow direction**: Left-to-right
- **Grid**: 10px grid, snapping enabled
- **Layers**: 3-5 vertical columns, each a rounded container
- **Margin**: 30px from page edges
- **Layer gap**: 40px between layer containers
- **Card gap**: 20px between cards within a layer

## Header Bar

```
Style: rounded=0;fillColor=#29B5E8;strokeColor=none
Position: x=0, y=0, width=full_page_width, height=70
```

- Snowflake logo: white circle (46×46) with ❄ symbol in `#29B5E8`
- Title: fontSize=22, fontStyle=1 (bold), fontColor=#FFFFFF, Helvetica
- Subtitle: fontSize=14, fontColor=#FFFFFF, opacity=80, right-aligned

## Layer Containers

```
Style: rounded=1;fillColor=#F5FBFE;strokeColor=#11567F;strokeWidth=2;arcSize=3
```

- **Badge**: `fillColor=#11567F;fontColor=#FFFFFF;fontSize=12;fontStyle=1;rounded=1`
- Badge position: top-left corner, overlapping container border by ~15px

## Component Cards

### Internal (Snowflake) Card
```
Container: rounded=1;fillColor=#FFFFFF;strokeColor=#29B5E8;strokeWidth=2;arcSize=8
Icon bg: rounded=1;fillColor=#E8F6FC;strokeColor=#29B5E8;strokeWidth=1
Title: fontSize=14;fontStyle=1;fontColor=#11567F;Helvetica
Type badge: fillColor=#29B5E8;fontColor=#FFFFFF;fontSize=9;rounded=1
Description: fontSize=9;fontColor=#5B5B5B
```

### External Card
```
Container: rounded=1;fillColor=#FFFFFF;strokeColor=#FF9F36;strokeWidth=2;arcSize=8
Icon bg: rounded=1;fillColor=#FFF8ED;strokeColor=#FF9F36;strokeWidth=1
Title: fontSize=14;fontStyle=1;fontColor=#E07800;Helvetica
Type badge: fillColor=#FF9F36;fontColor=#FFFFFF;fontSize=9;rounded=1
Description: fontSize=9;fontColor=#5B5B5B
```

### Accent Card (use sparingly)
```
Container: rounded=1;fillColor=#FFFFFF;strokeColor=#7254A3;strokeWidth=2;arcSize=8
Icon bg: rounded=1;fillColor=#E8DCFF;strokeColor=#7254A3;strokeWidth=1
Title: fontSize=14;fontStyle=1;fontColor=#7254A3;Helvetica
Type badge: fillColor=#7254A3;fontColor=#FFFFFF;fontSize=9;rounded=1
```

## Numbered Badges (for tools/steps)

```
Style: ellipse;fillColor=#29B5E8;strokeColor=none;fontColor=#FFFFFF;fontSize=14;fontStyle=1
Size: 26×26
```
Use orange fill (`#FF9F36`) for external tool numbers.

## Data Flow Arrows

| Type | Style |
|------|-------|
| Internal flow | `strokeWidth=2;strokeColor=#29B5E8;endArrow=classic` |
| External flow | `strokeWidth=2;strokeColor=#FF9F36;endArrow=classic` |
| Major flow | `strokeWidth=3;strokeColor=#29B5E8;endArrow=classic` |
| Bidirectional | `strokeWidth=3;strokeColor=#11567F;endArrow=classic;startArrow=classic` |
| Arrow labels | `fontSize=8;fontColor=#29B5E8` (or `#FF9F36` for external) |

## Sub-section Boxes

Used to group related items within a layer (e.g., "Internal Data" vs "External Data"):

### Internal sub-section
```
rounded=1;fillColor=#FFFFFF;strokeColor=#29B5E8;strokeWidth=2;arcSize=5
Label: fillColor=#29B5E8;fontColor=#FFFFFF;fontSize=10;fontStyle=1;rounded=1
```

### External sub-section
```
rounded=1;fillColor=#FFFFFF;strokeColor=#FF9F36;strokeWidth=2;arcSize=5
Label: fillColor=#FF9F36;fontColor=#FFFFFF;fontSize=10;fontStyle=1;rounded=1
```

## Table Rows (inside database containers)

```
Style: rounded=0;fillColor=#FFFFFF;strokeColor=#B8D4E8;fontSize=9;fontColor=#11567F;align=left;spacingLeft=8;fontStyle=1
Size: 140×24 (each row)
```

## Footer

- Divider line: `strokeColor=#E0E0E0;strokeWidth=1` at y=740
- Color legend: small 18×18 color swatches with 8px labels
- Version text: right-aligned, `fontSize=9;fontColor=#999999`

## Typography Summary

| Element | Size | Weight | Color |
|---------|------|--------|-------|
| Main title | 22 | Bold | #FFFFFF (on header) |
| Subtitle | 14 | Normal | #FFFFFF opacity 80 |
| Layer badge | 12 | Bold | #FFFFFF |
| Component title | 14 | Bold | #11567F / #E07800 |
| Type badge | 9 | Normal | #FFFFFF |
| Description | 9 | Normal | #5B5B5B |
| Object name | 9 | Bold | #11567F |
| Code/path text | 8 | Normal | #8BCCE4 (Courier New) |
| Footer | 9 | Normal | #999999 |
