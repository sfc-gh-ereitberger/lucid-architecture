# draw.io Component Library

Parameterized XML snippets for building Snowflake architecture diagrams.
Replace `{{PLACEHOLDERS}}` with actual values. All positions use absolute x/y coordinates.

---

## Header Bar

```xml
<mxCell id="header-bar" value="" style="rounded=0;whiteSpace=wrap;html=1;fillColor=#29B5E8;strokeColor=none;" vertex="1" parent="1">
  <mxGeometry x="0" y="0" width="{{PAGE_WIDTH}}" height="70" as="geometry" />
</mxCell>
<mxCell id="sf-logo-bg" value="" style="ellipse;whiteSpace=wrap;html=1;fillColor=#FFFFFF;strokeColor=none;" vertex="1" parent="1">
  <mxGeometry x="25" y="12" width="46" height="46" as="geometry" />
</mxCell>
<mxCell id="sf-logo" value="&#10052;" style="text;html=1;strokeColor=none;fillColor=none;align=center;verticalAlign=middle;whiteSpace=wrap;rounded=0;fontSize=28;fontColor=#29B5E8;fontStyle=1;" vertex="1" parent="1">
  <mxGeometry x="25" y="12" width="46" height="46" as="geometry" />
</mxCell>
<mxCell id="title" value="{{TITLE}}" style="text;html=1;strokeColor=none;fillColor=none;align=left;verticalAlign=middle;whiteSpace=wrap;rounded=0;fontSize=22;fontStyle=1;fontColor=#FFFFFF;fontFamily=Helvetica;" vertex="1" parent="1">
  <mxGeometry x="85" y="17" width="550" height="36" as="geometry" />
</mxCell>
<mxCell id="subtitle" value="{{SUBTITLE}}" style="text;html=1;strokeColor=none;fillColor=none;align=right;verticalAlign=middle;whiteSpace=wrap;rounded=0;fontSize=14;fontColor=#FFFFFF;fontFamily=Helvetica;opacity=80;" vertex="1" parent="1">
  <mxGeometry x="{{SUBTITLE_X}}" y="20" width="230" height="30" as="geometry" />
</mxCell>
```

---

## Layer Container

```xml
<mxCell id="{{LAYER_ID}}" value="" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#F5FBFE;strokeColor=#11567F;strokeWidth=2;arcSize=3;" vertex="1" parent="1">
  <mxGeometry x="{{X}}" y="100" width="{{WIDTH}}" height="{{HEIGHT}}" as="geometry" />
</mxCell>
<mxCell id="{{LAYER_ID}}-label" value="{{LAYER_NAME}}" style="text;html=1;strokeColor=none;fillColor=#11567F;align=center;verticalAlign=middle;whiteSpace=wrap;rounded=1;fontSize=12;fontStyle=1;fontColor=#FFFFFF;fontFamily=Helvetica;spacingLeft=12;spacingRight=12;" vertex="1" parent="1">
  <mxGeometry x="{{X}}" y="85" width="{{LABEL_WIDTH}}" height="26" as="geometry" />
</mxCell>
```

### Dark Layer (for agent/core processing)

```xml
<mxCell id="{{LAYER_ID}}" value="" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#11567F;strokeColor=#0A3D59;strokeWidth=2;arcSize=3;" vertex="1" parent="1">
  <mxGeometry x="{{X}}" y="100" width="{{WIDTH}}" height="{{HEIGHT}}" as="geometry" />
</mxCell>
<mxCell id="{{LAYER_ID}}-label" value="{{LAYER_NAME}}" style="text;html=1;strokeColor=none;fillColor=#29B5E8;align=center;verticalAlign=middle;whiteSpace=wrap;rounded=1;fontSize=12;fontStyle=1;fontColor=#FFFFFF;fontFamily=Helvetica;spacingLeft=12;spacingRight=12;" vertex="1" parent="1">
  <mxGeometry x="{{X}}" y="85" width="{{LABEL_WIDTH}}" height="26" as="geometry" />
</mxCell>
```

---

## Sub-section Box

### Internal sub-section
```xml
<mxCell id="{{ID}}" value="" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#FFFFFF;strokeColor=#29B5E8;strokeWidth=2;arcSize=5;" vertex="1" parent="1">
  <mxGeometry x="{{X}}" y="{{Y}}" width="{{WIDTH}}" height="{{HEIGHT}}" as="geometry" />
</mxCell>
<mxCell id="{{ID}}-label" value="{{LABEL}}" style="text;html=1;strokeColor=none;fillColor=#29B5E8;align=center;verticalAlign=middle;whiteSpace=wrap;rounded=1;fontSize=10;fontStyle=1;fontColor=#FFFFFF;fontFamily=Helvetica;spacingLeft=8;spacingRight=8;" vertex="1" parent="1">
  <mxGeometry x="{{X}}" y="{{LABEL_Y}}" width="{{LABEL_WIDTH}}" height="22" as="geometry" />
</mxCell>
```

### External sub-section
```xml
<mxCell id="{{ID}}" value="" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#FFFFFF;strokeColor=#FF9F36;strokeWidth=2;arcSize=5;" vertex="1" parent="1">
  <mxGeometry x="{{X}}" y="{{Y}}" width="{{WIDTH}}" height="{{HEIGHT}}" as="geometry" />
</mxCell>
<mxCell id="{{ID}}-label" value="{{LABEL}}" style="text;html=1;strokeColor=none;fillColor=#FF9F36;align=center;verticalAlign=middle;whiteSpace=wrap;rounded=1;fontSize=10;fontStyle=1;fontColor=#FFFFFF;fontFamily=Helvetica;spacingLeft=8;spacingRight=8;" vertex="1" parent="1">
  <mxGeometry x="{{X}}" y="{{LABEL_Y}}" width="{{LABEL_WIDTH}}" height="22" as="geometry" />
</mxCell>
```

---

## Database Container (with table list)

```xml
<mxCell id="{{ID}}-container" value="" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#E8F6FC;strokeColor=#29B5E8;strokeWidth=1;arcSize=8;" vertex="1" parent="1">
  <mxGeometry x="{{X}}" y="{{Y}}" width="160" height="{{HEIGHT}}" as="geometry" />
</mxCell>
<mxCell id="{{ID}}-icon" value="" style="shape=cylinder3;whiteSpace=wrap;html=1;boundedLbl=1;backgroundOutline=1;size=10;fillColor=#29B5E8;strokeColor=#11567F;strokeWidth=2;" vertex="1" parent="1">
  <mxGeometry x="{{ICON_X}}" y="{{ICON_Y}}" width="40" height="35" as="geometry" />
</mxCell>
<mxCell id="{{ID}}-title" value="{{DB_NAME}}" style="text;html=1;strokeColor=none;fillColor=none;align=center;verticalAlign=middle;whiteSpace=wrap;rounded=0;fontSize=9;fontStyle=1;fontColor=#11567F;fontFamily=Helvetica;" vertex="1" parent="1">
  <mxGeometry x="{{X_5}}" y="{{TITLE_Y}}" width="150" height="16" as="geometry" />
</mxCell>
<mxCell id="{{ID}}-type" value="Snowflake Database" style="text;html=1;strokeColor=none;fillColor=#11567F;align=center;verticalAlign=middle;whiteSpace=wrap;rounded=1;fontSize=8;fontColor=#FFFFFF;fontFamily=Helvetica;" vertex="1" parent="1">
  <mxGeometry x="{{TYPE_X}}" y="{{TYPE_Y}}" width="110" height="14" as="geometry" />
</mxCell>
```

### Table row (repeat for each table)
```xml
<mxCell id="{{TABLE_ID}}" value="{{TABLE_NAME}}" style="rounded=0;whiteSpace=wrap;html=1;fillColor=#FFFFFF;strokeColor=#B8D4E8;fontSize=9;fontColor=#11567F;align=left;spacingLeft=8;fontStyle=1;" vertex="1" parent="1">
  <mxGeometry x="{{X}}" y="{{Y}}" width="140" height="24" as="geometry" />
</mxCell>
```

---

## Internal Component Card (Snowflake service)

```xml
<mxCell id="{{ID}}-box" value="" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#FFFFFF;strokeColor=#29B5E8;strokeWidth=2;arcSize=8;shadow=0;" vertex="1" parent="1">
  <mxGeometry x="{{X}}" y="{{Y}}" width="230" height="150" as="geometry" />
</mxCell>
<mxCell id="{{ID}}-num" value="{{NUMBER}}" style="ellipse;whiteSpace=wrap;html=1;fillColor=#29B5E8;strokeColor=none;fontColor=#FFFFFF;fontSize=14;fontStyle=1;" vertex="1" parent="1">
  <mxGeometry x="{{NUM_X}}" y="{{NUM_Y}}" width="26" height="26" as="geometry" />
</mxCell>
<mxCell id="{{ID}}-icon-bg" value="" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#E8F6FC;strokeColor=#29B5E8;strokeWidth=1;" vertex="1" parent="1">
  <mxGeometry x="{{ICON_X}}" y="{{ICON_Y}}" width="50" height="40" as="geometry" />
</mxCell>
<mxCell id="{{ID}}-icon" value="{{ICON}}" style="text;html=1;strokeColor=none;fillColor=none;align=center;verticalAlign=middle;whiteSpace=wrap;rounded=0;fontSize=22;" vertex="1" parent="1">
  <mxGeometry x="{{ICON_X}}" y="{{ICON_Y2}}" width="50" height="36" as="geometry" />
</mxCell>
<mxCell id="{{ID}}-title" value="{{COMPONENT_NAME}}" style="text;html=1;strokeColor=none;fillColor=none;align=center;verticalAlign=middle;whiteSpace=wrap;rounded=0;fontSize=14;fontStyle=1;fontColor=#11567F;fontFamily=Helvetica;" vertex="1" parent="1">
  <mxGeometry x="{{TITLE_X}}" y="{{TITLE_Y}}" width="210" height="22" as="geometry" />
</mxCell>
<mxCell id="{{ID}}-type" value="{{TYPE_LABEL}}" style="text;html=1;strokeColor=none;fillColor=#29B5E8;align=center;verticalAlign=middle;whiteSpace=wrap;rounded=1;fontSize=9;fontColor=#FFFFFF;fontFamily=Helvetica;" vertex="1" parent="1">
  <mxGeometry x="{{TYPE_X}}" y="{{TYPE_Y}}" width="110" height="16" as="geometry" />
</mxCell>
<mxCell id="{{ID}}-desc" value="{{DESCRIPTION}}" style="text;html=1;strokeColor=none;fillColor=none;align=center;verticalAlign=middle;whiteSpace=wrap;rounded=0;fontSize=9;fontColor=#5B5B5B;fontFamily=Helvetica;" vertex="1" parent="1">
  <mxGeometry x="{{DESC_X}}" y="{{DESC_Y}}" width="210" height="35" as="geometry" />
</mxCell>
```

---

## External Component Card

Same structure as internal but with orange styling:

```xml
<mxCell id="{{ID}}-box" value="" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#FFFFFF;strokeColor=#FF9F36;strokeWidth=2;arcSize=8;shadow=0;" vertex="1" parent="1">
  <mxGeometry x="{{X}}" y="{{Y}}" width="230" height="{{HEIGHT}}" as="geometry" />
</mxCell>
<mxCell id="{{ID}}-num" value="{{NUMBER}}" style="ellipse;whiteSpace=wrap;html=1;fillColor=#FF9F36;strokeColor=none;fontColor=#FFFFFF;fontSize=14;fontStyle=1;" vertex="1" parent="1">
  <mxGeometry x="{{NUM_X}}" y="{{NUM_Y}}" width="26" height="26" as="geometry" />
</mxCell>
<mxCell id="{{ID}}-icon-bg" value="" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#FFF8ED;strokeColor=#FF9F36;strokeWidth=1;" vertex="1" parent="1">
  <mxGeometry x="{{ICON_X}}" y="{{ICON_Y}}" width="50" height="40" as="geometry" />
</mxCell>
<mxCell id="{{ID}}-icon" value="{{ICON}}" style="text;html=1;strokeColor=none;fillColor=none;align=center;verticalAlign=middle;whiteSpace=wrap;rounded=0;fontSize=22;" vertex="1" parent="1">
  <mxGeometry x="{{ICON_X}}" y="{{ICON_Y2}}" width="50" height="36" as="geometry" />
</mxCell>
<mxCell id="{{ID}}-title" value="{{COMPONENT_NAME}}" style="text;html=1;strokeColor=none;fillColor=none;align=center;verticalAlign=middle;whiteSpace=wrap;rounded=0;fontSize=14;fontStyle=1;fontColor=#E07800;fontFamily=Helvetica;" vertex="1" parent="1">
  <mxGeometry x="{{TITLE_X}}" y="{{TITLE_Y}}" width="210" height="22" as="geometry" />
</mxCell>
<mxCell id="{{ID}}-type" value="{{TYPE_LABEL}}" style="text;html=1;strokeColor=none;fillColor=#FF9F36;align=center;verticalAlign=middle;whiteSpace=wrap;rounded=1;fontSize=9;fontColor=#FFFFFF;fontFamily=Helvetica;" vertex="1" parent="1">
  <mxGeometry x="{{TYPE_X}}" y="{{TYPE_Y}}" width="110" height="16" as="geometry" />
</mxCell>
<mxCell id="{{ID}}-desc" value="{{DESCRIPTION}}" style="text;html=1;strokeColor=none;fillColor=none;align=center;verticalAlign=middle;whiteSpace=wrap;rounded=0;fontSize=9;fontColor=#5B5B5B;fontFamily=Helvetica;" vertex="1" parent="1">
  <mxGeometry x="{{DESC_X}}" y="{{DESC_Y}}" width="210" height="35" as="geometry" />
</mxCell>
```

---

## Accent Component Card (Purple — sparingly)

```xml
<mxCell id="{{ID}}-box" value="" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#FFFFFF;strokeColor=#7254A3;strokeWidth=2;arcSize=8;shadow=0;" vertex="1" parent="1">
  <mxGeometry x="{{X}}" y="{{Y}}" width="230" height="150" as="geometry" />
</mxCell>
<mxCell id="{{ID}}-icon-bg" value="" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#E8DCFF;strokeColor=#7254A3;strokeWidth=1;" vertex="1" parent="1">
  <mxGeometry x="{{ICON_X}}" y="{{ICON_Y}}" width="50" height="40" as="geometry" />
</mxCell>
<mxCell id="{{ID}}-title" value="{{COMPONENT_NAME}}" style="text;html=1;strokeColor=none;fillColor=none;align=center;verticalAlign=middle;whiteSpace=wrap;rounded=0;fontSize=14;fontStyle=1;fontColor=#7254A3;fontFamily=Helvetica;" vertex="1" parent="1">
  <mxGeometry x="{{TITLE_X}}" y="{{TITLE_Y}}" width="210" height="22" as="geometry" />
</mxCell>
<mxCell id="{{ID}}-type" value="{{TYPE_LABEL}}" style="text;html=1;strokeColor=none;fillColor=#7254A3;align=center;verticalAlign=middle;whiteSpace=wrap;rounded=1;fontSize=9;fontColor=#FFFFFF;fontFamily=Helvetica;" vertex="1" parent="1">
  <mxGeometry x="{{TYPE_X}}" y="{{TYPE_Y}}" width="110" height="16" as="geometry" />
</mxCell>
```

---

## Agent Container (inside dark layer)

```xml
<mxCell id="{{ID}}-main" value="" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#1A6B94;strokeColor=#29B5E8;strokeWidth=2;arcSize=5;" vertex="1" parent="1">
  <mxGeometry x="{{X}}" y="{{Y}}" width="230" height="{{HEIGHT}}" as="geometry" />
</mxCell>
<mxCell id="{{ID}}-icon-ring" value="" style="ellipse;whiteSpace=wrap;html=1;fillColor=#11567F;strokeColor=#29B5E8;strokeWidth=3;" vertex="1" parent="1">
  <mxGeometry x="{{RING_X}}" y="{{RING_Y}}" width="100" height="100" as="geometry" />
</mxCell>
<mxCell id="{{ID}}-icon" value="&#10052;" style="text;html=1;strokeColor=none;fillColor=none;align=center;verticalAlign=middle;whiteSpace=wrap;rounded=0;fontSize=40;fontColor=#29B5E8;" vertex="1" parent="1">
  <mxGeometry x="{{ICON_X}}" y="{{ICON_Y}}" width="60" height="60" as="geometry" />
</mxCell>
<mxCell id="{{ID}}-title" value="{{AGENT_NAME}}" style="text;html=1;strokeColor=none;fillColor=none;align=center;verticalAlign=middle;whiteSpace=wrap;rounded=0;fontSize=16;fontStyle=1;fontColor=#FFFFFF;fontFamily=Helvetica;" vertex="1" parent="1">
  <mxGeometry x="{{TITLE_X}}" y="{{TITLE_Y}}" width="190" height="45" as="geometry" />
</mxCell>
<mxCell id="{{ID}}-path" value="{{OBJECT_PATH}}" style="text;html=1;strokeColor=none;fillColor=none;align=center;verticalAlign=middle;whiteSpace=wrap;rounded=0;fontSize=8;fontColor=#8BCCE4;fontFamily=Courier New;" vertex="1" parent="1">
  <mxGeometry x="{{PATH_X}}" y="{{PATH_Y}}" width="190" height="14" as="geometry" />
</mxCell>
```

### Agent Capability Row
```xml
<mxCell id="{{ID}}" value="{{CAPABILITY}}" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#11567F;strokeColor=#29B5E8;strokeWidth=1;fontSize=9;fontColor=#FFFFFF;align=center;" vertex="1" parent="1">
  <mxGeometry x="{{X}}" y="{{Y}}" width="190" height="32" as="geometry" />
</mxCell>
```

---

## Chat Interface / UI Card

```xml
<mxCell id="{{ID}}-box" value="" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#FFFFFF;strokeColor=#29B5E8;strokeWidth=2;arcSize=8;" vertex="1" parent="1">
  <mxGeometry x="{{X}}" y="{{Y}}" width="230" height="280" as="geometry" />
</mxCell>
<mxCell id="{{ID}}-icon-bg" value="" style="ellipse;whiteSpace=wrap;html=1;fillColor=#E8F6FC;strokeColor=#29B5E8;strokeWidth=2;" vertex="1" parent="1">
  <mxGeometry x="{{ICON_X}}" y="{{ICON_Y}}" width="80" height="60" as="geometry" />
</mxCell>
<mxCell id="{{ID}}-icon" value="&#128172;" style="text;html=1;strokeColor=none;fillColor=none;align=center;verticalAlign=middle;whiteSpace=wrap;rounded=0;fontSize=32;" vertex="1" parent="1">
  <mxGeometry x="{{ICON_X}}" y="{{ICON_Y2}}" width="80" height="50" as="geometry" />
</mxCell>
<mxCell id="{{ID}}-title" value="{{INTERFACE_NAME}}" style="text;html=1;strokeColor=none;fillColor=none;align=center;verticalAlign=middle;whiteSpace=wrap;rounded=0;fontSize=14;fontStyle=1;fontColor=#11567F;fontFamily=Helvetica;" vertex="1" parent="1">
  <mxGeometry x="{{TITLE_X}}" y="{{TITLE_Y}}" width="170" height="22" as="geometry" />
</mxCell>
```

### Feature Checklist Row
```xml
<mxCell id="{{ID}}" value="&#10003;  {{FEATURE}}" style="text;html=1;strokeColor=none;fillColor=none;align=left;verticalAlign=middle;whiteSpace=wrap;rounded=0;fontSize=10;fontColor=#5B5B5B;fontFamily=Helvetica;" vertex="1" parent="1">
  <mxGeometry x="{{X}}" y="{{Y}}" width="180" height="20" as="geometry" />
</mxCell>
```

---

## User Persona Card

```xml
<mxCell id="{{ID}}-box" value="" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#FFFFFF;strokeColor=#29B5E8;strokeWidth=2;arcSize=8;" vertex="1" parent="1">
  <mxGeometry x="{{X}}" y="{{Y}}" width="230" height="260" as="geometry" />
</mxCell>
<mxCell id="{{ID}}-icon-bg" value="" style="ellipse;whiteSpace=wrap;html=1;fillColor=#E8F6FC;strokeColor=#29B5E8;strokeWidth=2;" vertex="1" parent="1">
  <mxGeometry x="{{ICON_X}}" y="{{ICON_Y}}" width="80" height="60" as="geometry" />
</mxCell>
<mxCell id="{{ID}}-icon" value="&#128100;" style="text;html=1;strokeColor=none;fillColor=none;align=center;verticalAlign=middle;whiteSpace=wrap;rounded=0;fontSize=32;" vertex="1" parent="1">
  <mxGeometry x="{{ICON_X}}" y="{{ICON_Y2}}" width="80" height="50" as="geometry" />
</mxCell>
<mxCell id="{{ID}}-title" value="{{PERSONA_NAME}}" style="text;html=1;strokeColor=none;fillColor=none;align=center;verticalAlign=middle;whiteSpace=wrap;rounded=0;fontSize=14;fontStyle=1;fontColor=#11567F;fontFamily=Helvetica;" vertex="1" parent="1">
  <mxGeometry x="{{TITLE_X}}" y="{{TITLE_Y}}" width="170" height="22" as="geometry" />
</mxCell>
```

### Example Question Bubble
```xml
<mxCell id="{{ID}}" value="&quot;{{QUESTION}}&quot;" style="text;html=1;strokeColor=none;fillColor=#E8F6FC;align=left;verticalAlign=middle;whiteSpace=wrap;rounded=1;fontSize=9;fontColor=#11567F;fontFamily=Helvetica;spacingLeft=6;spacingRight=6;" vertex="1" parent="1">
  <mxGeometry x="{{X}}" y="{{Y}}" width="190" height="22" as="geometry" />
</mxCell>
```

---

## Data Flow Arrow

```xml
<mxCell id="{{ID}}" value="" style="endArrow=classic;html=1;strokeWidth={{STROKE_WIDTH}};strokeColor={{COLOR}};" edge="1" parent="1">
  <mxGeometry width="50" height="50" relative="1" as="geometry">
    <mxPoint x="{{SOURCE_X}}" y="{{SOURCE_Y}}" as="sourcePoint" />
    <mxPoint x="{{TARGET_X}}" y="{{TARGET_Y}}" as="targetPoint" />
  </mxGeometry>
</mxCell>
```

### Arrow with Label
```xml
<mxCell id="{{ID}}-label" value="{{LABEL}}" style="text;html=1;strokeColor=none;fillColor=none;align=center;verticalAlign=middle;whiteSpace=wrap;rounded=0;fontSize=8;fontColor={{COLOR}};fontFamily=Helvetica;" vertex="1" parent="1">
  <mxGeometry x="{{LABEL_X}}" y="{{LABEL_Y}}" width="60" height="14" as="geometry" />
</mxCell>
```

---

## Footer

```xml
<mxCell id="footer-line" value="" style="line;strokeWidth=1;fillColor=none;align=left;verticalAlign=middle;spacingTop=-1;spacingLeft=3;spacingRight=3;rotatable=0;labelPosition=right;points=[];portConstraint=eastwest;strokeColor=#E0E0E0;" vertex="1" parent="1">
  <mxGeometry x="30" y="740" width="{{LINE_WIDTH}}" height="10" as="geometry" />
</mxCell>
<mxCell id="legend-title" value="Brand Colors:" style="text;html=1;strokeColor=none;fillColor=none;align=left;verticalAlign=middle;whiteSpace=wrap;rounded=0;fontSize=9;fontStyle=1;fontColor=#5B5B5B;fontFamily=Helvetica;" vertex="1" parent="1">
  <mxGeometry x="30" y="755" width="80" height="16" as="geometry" />
</mxCell>
<mxCell id="color1" value="" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#29B5E8;strokeColor=none;" vertex="1" parent="1">
  <mxGeometry x="115" y="755" width="18" height="18" as="geometry" />
</mxCell>
<mxCell id="color1-label" value="#29B5E8 Snowflake Blue" style="text;html=1;strokeColor=none;fillColor=none;align=left;verticalAlign=middle;whiteSpace=wrap;rounded=0;fontSize=8;fontColor=#5B5B5B;fontFamily=Helvetica;" vertex="1" parent="1">
  <mxGeometry x="138" y="755" width="120" height="18" as="geometry" />
</mxCell>
<mxCell id="color2" value="" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#11567F;strokeColor=none;" vertex="1" parent="1">
  <mxGeometry x="270" y="755" width="18" height="18" as="geometry" />
</mxCell>
<mxCell id="color2-label" value="#11567F Mid Blue" style="text;html=1;strokeColor=none;fillColor=none;align=left;verticalAlign=middle;whiteSpace=wrap;rounded=0;fontSize=8;fontColor=#5B5B5B;fontFamily=Helvetica;" vertex="1" parent="1">
  <mxGeometry x="293" y="755" width="100" height="18" as="geometry" />
</mxCell>
<mxCell id="color3" value="" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#FF9F36;strokeColor=none;" vertex="1" parent="1">
  <mxGeometry x="405" y="755" width="18" height="18" as="geometry" />
</mxCell>
<mxCell id="color3-label" value="#FF9F36 Valencia Orange" style="text;html=1;strokeColor=none;fillColor=none;align=left;verticalAlign=middle;whiteSpace=wrap;rounded=0;fontSize=8;fontColor=#5B5B5B;fontFamily=Helvetica;" vertex="1" parent="1">
  <mxGeometry x="428" y="755" width="130" height="18" as="geometry" />
</mxCell>
<mxCell id="color4" value="" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#7254A3;strokeColor=none;" vertex="1" parent="1">
  <mxGeometry x="570" y="755" width="18" height="18" as="geometry" />
</mxCell>
<mxCell id="color4-label" value="#7254A3 Purple Moon" style="text;html=1;strokeColor=none;fillColor=none;align=left;verticalAlign=middle;whiteSpace=wrap;rounded=0;fontSize=8;fontColor=#5B5B5B;fontFamily=Helvetica;" vertex="1" parent="1">
  <mxGeometry x="593" y="755" width="120" height="18" as="geometry" />
</mxCell>
<mxCell id="footer-text" value="{{FOOTER_TEXT}}" style="text;html=1;strokeColor=none;fillColor=none;align=right;verticalAlign=middle;whiteSpace=wrap;rounded=0;fontSize=9;fontColor=#999999;fontFamily=Helvetica;" vertex="1" parent="1">
  <mxGeometry x="{{FOOTER_X}}" y="755" width="350" height="18" as="geometry" />
</mxCell>
```

---

## mxfile Wrapper

Every diagram must be wrapped in:

```xml
<mxfile host="app.diagrams.net" modified="{{TIMESTAMP}}" agent="Cortex Code" version="21.0.0" type="device">
  <diagram id="snowflake-architecture" name="{{DIAGRAM_NAME}}">
    <mxGraphModel dx="1434" dy="780" grid="1" gridSize="10" guides="1" tooltips="1" connect="1" arrows="1" fold="1" page="1" pageScale="1" pageWidth="{{PAGE_WIDTH}}" pageHeight="{{PAGE_HEIGHT}}" math="0" shadow="0" background="#FFFFFF">
      <root>
        <mxCell id="0" />
        <mxCell id="1" parent="0" />
        
        <!-- ALL COMPONENTS HERE -->
        
      </root>
    </mxGraphModel>
  </diagram>
</mxfile>
```
