# Draw.io Standards for Business X-Ray

**Technical reference for generating consistent, professional draw.io diagrams.**

---

## Annotation System (NEW)

**Apply annotations AFTER mapping the process (review pass).**

| Annotation | Border Style | Border Width | Color | Fill | Meaning |
|------------|--------------|--------------|-------|------|---------|
| **Bottleneck** | Solid | 3px | `#FF6B6B` | `#fff5f5` | Slowing things down |
| **Automate** | Dashed | 2px | `#FFA500` | `#fff8e6` | AI/tool could do this |
| **High Value** | Solid | 3px | `#90EE90` | `#f0fff0` | Human should keep doing |
| **Digital Asset** | Solid | 2px | `#9370DB` | `#f5f0ff` | Needs to be built |
| **Normal** | Solid | 1px | `#666666` | `#f5f5f5` | Standard step |

### Annotation XML Examples

```xml
<!-- Bottleneck (Red, solid thick) -->
<mxCell value="Step Name" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#fff5f5;strokeColor=#FF6B6B;strokeWidth=3;fontSize=10;" vertex="1" parent="1">
    <mxGeometry x="100" y="100" width="100" height="50" as="geometry"/>
</mxCell>

<!-- Automate (Orange, dashed) -->
<mxCell value="Step Name" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#fff8e6;strokeColor=#FFA500;strokeWidth=2;dashed=1;fontSize=10;" vertex="1" parent="1">
    <mxGeometry x="100" y="100" width="100" height="50" as="geometry"/>
</mxCell>

<!-- High Value (Green, solid thick) -->
<mxCell value="Step Name" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#f0fff0;strokeColor=#90EE90;strokeWidth=3;fontSize=10;" vertex="1" parent="1">
    <mxGeometry x="100" y="100" width="100" height="50" as="geometry"/>
</mxCell>

<!-- Digital Asset (Purple, solid) -->
<mxCell value="Step Name" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#f5f0ff;strokeColor=#9370DB;strokeWidth=2;fontSize=10;" vertex="1" parent="1">
    <mxGeometry x="100" y="100" width="100" height="50" as="geometry"/>
</mxCell>
```

---

## Page Linking (Navigation)

**Use clickable links to navigate between pages within the .drawio file.**

### Link Syntax

```xml
<!-- Link to another page (by page ID) -->
<mxCell value="Content Creation"
  style="rounded=1;fillColor=#4DA6FF;fontColor=#ffffff;fontStyle=1;"
  vertex="1" parent="1">
  <mxGeometry x="100" y="100" width="120" height="40" as="geometry"/>
  <!-- Add link attribute -->
  <UserObject label="Content Creation" link="data:page/id,page-2" id="nav-content"/>
</mxCell>

<!-- Alternative: Using link in style -->
<mxCell value="Content Creation"
  style="rounded=1;fillColor=#4DA6FF;fontColor=#ffffff;link=data:page/id,page-2;"
  vertex="1" parent="1">
  <mxGeometry x="100" y="100" width="120" height="40" as="geometry"/>
</mxCell>
```

### Back to Overview Link

Add on every detail page:

```xml
<mxCell value="← Back to Overview"
  style="rounded=1;fillColor=#f5f5f5;strokeColor=#666666;fontSize=10;link=data:page/id,page-1;"
  vertex="1" parent="1">
  <mxGeometry x="40" y="20" width="120" height="30" as="geometry"/>
</mxCell>
```

---

## File Structure

All Business X-Ray outputs go in a **single .drawio file** with multiple pages:

```xml
<mxfile host="app.diagrams.net">
    <diagram name="Business Overview" id="page-1">...</diagram>  <!-- Bow-Tie + Business Map -->
    <diagram name="Content Creation" id="page-2">...</diagram>   <!-- Process swimlane -->
    <diagram name="Lead Conversion Flow" id="page-3">...</diagram>
    <diagram name="Fulfillment Flow" id="page-4">...</diagram>
    <diagram name="Operations Flow" id="page-5">...</diagram>
    <diagram name="90-Day Roadmap" id="page-6">...</diagram>
</mxfile>
```

**Why single file?**
- Works with Claude Web App (users copy XML, save as .drawio)
- No file system dependencies
- All pages linked together for drill-down navigation

---

## Color Coding System

### Business Map Column Colors

**Quick Reference:**
```
TRAFFIC:  🟢 Organic (Green)  |  🔵 Owned (Blue)  |  🔴 Paid (Red)
PRODUCTS: 🔵 Blue
FUNNELS:  🟣 Purple
Active = Darker color  |  Planned = Lighter color + dashed border
```

#### TRAFFIC Sources (3 Types)

| Type | Status | Fill Color | Stroke Color | Font Color | Example |
|------|--------|------------|--------------|------------|---------|
| **Organic** | Active | `#90EE90` | `#82b366` | `#1a1a2e` | YouTube, Substack, SEO |
| **Organic** | Planned | `#d5e8d4` | `#82b366` | `#666666` | Podcast (future) |
| **Owned** | Active | `#4DA6FF` | `#3399FF` | `#ffffff` | Email List, SMS List |
| **Owned** | Planned | `#b3d9ff` | `#3399FF` | `#1a1a2e` | Community (future) |
| **Paid** | Active | `#FF6B6B` | `#FF4444` | `#ffffff` | Facebook Ads, Google Ads |
| **Paid** | Planned | `#ffb3b3` | `#FF4444` | `#1a1a2e` | YouTube Ads (future) |

#### PRODUCTS

| Status | Fill Color | Stroke Color | Font Color | Example |
|--------|------------|--------------|------------|---------|
| Active | `#4DA6FF` | `#3399FF` | `#ffffff` | Business X-Ray Skill |
| Planned | `#b3d9ff` | `#3399FF` | `#1a1a2e` | Community Offer |

#### FUNNELS

| Status | Fill Color | Stroke Color | Font Color | Example |
|--------|------------|--------------|------------|---------|
| Active | `#9370DB` | `#7B68EE` | `#ffffff` | Daily Newsletter |
| Planned | `#d4c4e8` | `#7B68EE` | `#1a1a2e` | Webinar Sequence |

### Annotation Colors (Process Flows)

| Status | Fill Color | Stroke Color | Font Color | Use For |
|--------|------------|--------------|------------|---------|
| Bottleneck | `#FF6B6B` | `#FF4444` | `#ffffff` | Steps that slow things down |
| AI Opportunity | `#4DA6FF` | `#3399FF` | `#ffffff` | Steps that can be automated |
| Value-Add | `#90EE90` | `#82b366` | `#2d6a4f` | Strategic, high-leverage work |
| Decision | `#FFD166` | `#f4a261` | `#1a1a2e` | Choice points in process |
| Neutral | `#f5f5f5` | `#666666` | `#333333` | Standard process steps |
| Digital Asset | `#9370DB` | `#7B68EE` | `#ffffff` | SOPs, templates to build |
| Complete/Done | `#b2f2bb` | `#2f9e44` | `#1a1a2e` | Completed outputs |

### Swimlane Colors

| Lane Type | Fill Color | Stroke Color | Use For |
|-----------|------------|--------------|---------|
| User/Owner | `#dae8fc` | `#6c8ebf` | Actions done by business owner |
| AI/Automation | `#ffe6cc` | `#d79b00` | Automated steps |
| Team/VA | `#e1d5e7` | `#9673a6` | Delegated to team |
| Output/Result | `#f8cecc` | `#b85450` | Final deliverables |
| Customer | `#d5e8d4` | `#82b366` | Customer-facing touchpoints |

---

## Shape Standards

### Process Step (Rounded Rectangle)
```xml
<mxCell value="Step Name" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#f5f5f5;strokeColor=#666666;fontSize=10;" vertex="1" parent="1">
    <mxGeometry x="100" y="100" width="100" height="50" as="geometry"/>
</mxCell>
```

### Decision Point (Diamond)
```xml
<mxCell value="Decision?" style="rhombus;whiteSpace=wrap;html=1;fillColor=#FFD166;strokeColor=#f4a261;fontSize=9;" vertex="1" parent="1">
    <mxGeometry x="100" y="100" width="60" height="45" as="geometry"/>
</mxCell>
```

### Start/End (Ellipse)
```xml
<mxCell value="START" style="ellipse;whiteSpace=wrap;html=1;fillColor=#38b000;strokeColor=#2d6a4f;fontColor=#ffffff;fontSize=10;fontStyle=1;" vertex="1" parent="1">
    <mxGeometry x="100" y="100" width="60" height="35" as="geometry"/>
</mxCell>
```

### Swimlane Pool (Native stackLayout - PREFERRED)

**Use draw.io's native swimlane with auto-stacking lanes:**

```xml
<!-- Pool with auto-stacking lanes -->
<mxCell id="pool-1" value="Process Name" style="swimlane;childLayout=stackLayout;resizeParent=1;resizeParentMax=0;horizontal=0;startSize=20;horizontalStack=0;html=1;fillColor=#f5f5f5;strokeColor=#666666;fontStyle=1;" vertex="1" parent="1">
    <mxGeometry x="40" y="40" width="800" height="400" as="geometry"/>
</mxCell>

<!-- Lanes auto-stack vertically - no manual y-coordinates needed! -->
<mxCell id="lane-1" value="Lane 1" style="swimlane;startSize=20;horizontal=0;html=1;fillColor=#dae8fc;strokeColor=#6c8ebf;" vertex="1" parent="pool-1">
    <mxGeometry x="20" width="780" height="100" as="geometry"/>
</mxCell>

<mxCell id="lane-2" value="Lane 2" style="swimlane;startSize=20;horizontal=0;html=1;fillColor=#ffe6cc;strokeColor=#d79b00;" vertex="1" parent="pool-1">
    <mxGeometry x="20" y="100" width="780" height="100" as="geometry"/>
</mxCell>

<mxCell id="lane-3" value="Lane 3" style="swimlane;startSize=20;horizontal=0;html=1;fillColor=#d5e8d4;strokeColor=#82b366;" vertex="1" parent="pool-1">
    <mxGeometry x="20" y="200" width="780" height="100" as="geometry"/>
</mxCell>
```

**Key properties:**
- `childLayout=stackLayout` - Lanes auto-stack vertically
- `resizeParent=1` - Pool auto-resizes when lanes change
- `startSize=20` - Compact lane label (vs 100 for wide labels)
- `horizontal=0` - Horizontal swimlane (lanes stack top-to-bottom)

**Benefits over manual positioning:**
- No manual y-coordinate math
- Adding/removing lanes doesn't break layout
- Resize handles work properly
- Matches draw.io UI behavior

### Swimlane Lane (Legacy - for reference only)
```xml
<mxCell value="Lane Name" style="swimlane;horizontal=0;whiteSpace=wrap;html=1;startSize=100;fillColor=#dae8fc;strokeColor=#6c8ebf;fontStyle=1;" vertex="1" parent="pool-id">
    <mxGeometry x="30" width="730" height="130" as="geometry"/>
</mxCell>
```

### Connector Arrow
```xml
<mxCell style="edgeStyle=orthogonalEdgeStyle;rounded=0;orthogonalLoop=1;jettySize=auto;html=1;strokeColor=#666666;strokeWidth=2;" edge="1" parent="1" source="source-id" target="target-id">
    <mxGeometry relative="1" as="geometry"/>
</mxCell>
```

### Expansion Link (Dashed)
```xml
<mxCell value="Expands to" style="edgeStyle=orthogonalEdgeStyle;rounded=0;orthogonalLoop=1;jettySize=auto;html=1;strokeColor=#d79b00;strokeWidth=3;dashed=1;fontStyle=1;labelBackgroundColor=#ffffff;" edge="1" parent="1" source="source-id" target="target-id">
    <mxGeometry relative="1" as="geometry"/>
</mxCell>
```

---

## Page Templates

### Page 1: Business Overview (Bow-Tie + Business Map)

Layout: Bow-Tie funnel on top, 7-column Business Map below

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                              BOW-TIE FUNNEL                                  │
│                                                                              │
│  [Awareness] → [Nurture] → [Consider] → [COMMIT] → [Onboard] → [Launch] → [Results]  │
│                                    ↑                                         │
│                              (the knot)                                      │
├─────────────────────────────────────────────────────────────────────────────┤
│                              BUSINESS MAP                                    │
│                                                                              │
│  TRAFFIC | CONVERTERS | PRODUCTS | FUNNELS | MATH | TEAM | GOALS            │
│  --------|------------|----------|---------|------|------|-------           │
│  Sources | Landing    | Offers   | Sequences| P&L | Who  | Performance      │
│          | pages      | + prices |          |      |      | Goals           │
└─────────────────────────────────────────────────────────────────────────────┘
```

Standard dimensions:
- Page width: ~1300px
- Bow-Tie section: y=40, height ~150px
- Business Map section: y=220, height ~400px
- Column headers: 100-150px wide, 30px tall
- Content boxes: 100px wide, 40-50px tall
- Start x: 40

### Pages 2+: Process Flow Swimlanes

Layout: Horizontal swimlanes, left-to-right flow

```
┌─────────────────────────────────────────────────────────┐
│ PROCESS NAME                                             │
├─────────┬───────────────────────────────────────────────┤
│ Owner   │ [Step] → [Step] → [Decision] → [Step]        │
├─────────┼───────────────────────────────────────────────┤
│ AI      │           [Step] → [Step]                     │
├─────────┼───────────────────────────────────────────────┤
│ Output  │                              [Result]         │
└─────────┴───────────────────────────────────────────────┘
```

Standard dimensions:
- Pool: 760px wide, 400px tall
- Lane height: 95-130px each
- Step boxes: 100px wide, 50px tall
- Start x: 40, y: 40

### Page 6: Action Roadmap

Layout: Simple prioritized checklist (single column, vertical list)

```
┌─────────────────────────────────────────────────────────────┐
│                    ACTION ROADMAP                            │
│                                                              │
│  DO FIRST                                                    │
│  ────────                                                    │
│  ☐ 🔴 Fix content bottleneck                                │
│     Create batch workflow for weekly content                 │
│                                                              │
│  ☐ 🟠 Automate email follow-ups                             │
│     Set up ConvertKit sequences                              │
│                                                              │
│  DO NEXT                                                     │
│  ────────                                                    │
│  ☐ 🟣 Build lead magnet landing page                        │
│     Create opt-in page with Carrd or similar                 │
│                                                              │
│  DO LATER                                                    │
│  ────────                                                    │
│  ☐ 🟠 Set up social scheduling                              │
│     Batch create + schedule with Buffer/Later                │
└─────────────────────────────────────────────────────────────┘
```

Standard dimensions:
- Page width: 400px
- Section header: fontSize=14, fontStyle=1 (bold)
- Task title: fontSize=11, with checkbox prefix
- Task description: fontSize=9, indented, gray text
- Spacing: 60px between items, 80px between sections

---

## ID Naming Conventions

Use consistent, descriptive IDs for all elements:

```
Page 1 (Business Overview):
- p1-header-traffic, p1-header-converters, etc.
- p1-traffic-1, p1-traffic-2, etc.
- p1-income-title, p1-income-r1c1, etc.

Page 1 (Bow-Tie section):
- p1-bowtie-title
- p1-bt-awareness, p1-bt-nurture, p1-bt-consider, p1-bt-commit
- p1-bt-onboard, p1-bt-launch, p1-bt-results
- p1-bt-arrow-1, p1-bt-arrow-2, etc.

Page 2+ (Process Flows):
- p2-pool, p2-lane-owner, p2-lane-ai, p2-lane-output
- p2-step-1, p2-step-2, p2-decision-1
- p2-arrow-1, p2-arrow-2

Last Page (Roadmap):
- p6-title, p6-section-first, p6-section-next, p6-section-later
- p6-task-1, p6-task-2, p6-task-3
- p6-desc-1, p6-desc-2, p6-desc-3
```

---

## Multi-Level Drill-Down Pattern

To link a high-level step to a detailed sub-process:

1. **On the high-level page:** Add an expansion arrow pointing off-page
```xml
<mxCell value="Expands to Page 3" style="...dashed=1..." edge="1" source="step-id">
    <mxGeometry relative="1" as="geometry">
        <mxPoint x="800" y="200" as="targetPoint"/>
    </mxGeometry>
</mxCell>
```

2. **Use consistent naming:**
   - High-level: "Content Creation"
   - Detail page name: "Content Creation - Detail"
   - Sub-detail: "Content Creation - Thread Writing"

3. **Add "Back to Overview" link** on detail pages

---

## Table Patterns (For MATH Section)

### Income Table
```xml
<!-- Title Row -->
<mxCell value="INCOME" style="text;fillColor=#2d6a4f;fontColor=#ffffff;fontStyle=1;..." />

<!-- Header Row -->
<mxCell value="Product" style="text;fillColor=#e8f5e9;fontStyle=1;..." />
<mxCell value="Price" style="text;fillColor=#e8f5e9;fontStyle=1;..." />
<mxCell value="Cap" style="text;fillColor=#e8f5e9;fontStyle=1;..." />
<mxCell value="$/Month" style="text;fillColor=#e8f5e9;fontStyle=1;..." />
<mxCell value="$/Year" style="text;fillColor=#e8f5e9;fontStyle=1;..." />

<!-- Data Rows (alternating white/#f9f9f9) -->
<mxCell value="Product Name" style="text;fillColor=#ffffff;align=left;..." />
<mxCell value="$X" style="text;fillColor=#ffffff;align=center;..." />
...

<!-- Total Row -->
<mxCell value="TOTAL" style="text;fillColor=#2d6a4f;fontColor=#ffffff;fontStyle=1;..." />
```

### Expense Table
Same pattern but with:
- Title: `fillColor=#c62828` (red)
- Headers: `fillColor=#ffebee` (light red)

---

## Legend Box Pattern

Include on process flow pages:

```xml
<mxCell value="" style="rounded=1;fillColor=#f5f5f5;strokeColor=#e9ecef;" vertex="1">
    <mxGeometry x="540" y="530" width="170" height="100" as="geometry"/>
</mxCell>
<mxCell value="LEGEND" style="text;fontStyle=1;fontSize=10;" />
<!-- Color swatches with labels -->
<mxCell value="" style="ellipse;fillColor=#FF6B6B;" /> <!-- Bottleneck -->
<mxCell value="" style="rounded=1;fillColor=#4DA6FF;" /> <!-- AI Opportunity -->
<mxCell value="" style="rhombus;fillColor=#FFD166;" /> <!-- Decision -->
```

---

## XML Template (Complete File Structure)

```xml
<mxfile host="app.diagrams.net">
    <diagram name="Business Overview" id="page-1">
        <mxGraphModel dx="1260" dy="1067" grid="1" gridSize="10" guides="1" tooltips="1" connect="1" arrows="1" fold="1" page="0" pageScale="1" pageWidth="1600" pageHeight="900" math="0" shadow="0">
            <root>
                <mxCell id="0"/>
                <mxCell id="1" parent="0"/>
                <!-- Business Overview content here -->
            </root>
        </mxGraphModel>
    </diagram>
    <diagram name="Lead Generation Flow" id="page-2">
        <mxGraphModel ...>
            <root>
                <mxCell id="0"/>
                <mxCell id="1" parent="0"/>
                <!-- Lead Gen swimlane content here -->
            </root>
        </mxGraphModel>
    </diagram>
    <!-- Additional pages... -->
</mxfile>
```

---

## Quality Checklist

Before outputting any diagram:

- [ ] All elements have unique, descriptive IDs
- [ ] Colors follow the standard (bottleneck=red, AI=blue, etc.)
- [ ] Swimlanes have consistent heights
- [ ] Arrows connect properly (source/target IDs exist)
- [ ] Text is readable (fontSize >= 8)
- [ ] Page names are descriptive
- [ ] Expansion links use dashed style
- [ ] Tables have proper alignment
