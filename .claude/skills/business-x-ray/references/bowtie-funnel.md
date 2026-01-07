# Bow-Tie Funnel Reference (.drawio)

**Template and standards for generating bow-tie funnel diagrams in draw.io format.**

---

## Overview

The bow-tie funnel visualizes the complete customer journey:
- **Left side (narrowing)**: ACQUISITION - Traffic → Conversion
- **Center (the knot)**: COMMIT - The conversion moment
- **Right side (expanding)**: DELIVERY - Customer → Results

---

## Visual Structure (5 Rows)

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                     BOW-TIE FUNNEL: [Business Name]                         │  ROW 1: Title
│                 Customer Journey: Discovery → Conversion → Results          │
├──────────────────────────┬─────────────┬────────────────────────────────────┤
│       ACQUISITION        │   COMMIT    │            DELIVERY                │  ROW 2: Phase Labels
│   (green border)         │  (orange)   │         (green border)             │
├─────────┬────────┬───────┼─────────────┼──────────┬─────────┬───────────────┤
│AWARENESS│NURTURE │CONSID.│ CONVERSION  │ONBOARDING│ LAUNCH  │   RESULTS     │  ROW 3: Stage Headers
├─────────┼────────┼───────┼─────────────┼──────────┼─────────┼───────────────┤
│ [box]   │ [box]  │ [box] │   [box]     │  [box]   │  [box]  │    [box]      │  ROW 4: Activity Boxes
│ [box] →→│→[box]→→│→[box]→│→→ [box] →→→→│→→[box]→→→│→→[box]→→│→→→ [box]      │  (3-4 per column)
│ [box]   │ [box]  │ [box] │  PURCHASE   │  [box]   │  [box]  │    [box]      │
│         │        │       │  (Upsell)   │          │         │               │
├─────────┴────────┴───────┴─────────────┴──────────┴─────────┴───────────────┤
│  ←←←←←←←←←← Referrals loop back to Awareness ←←←←←←←←←←←←←←←←←←←←←←←←←←←   │  Feedback Loop
├─────────────────────────────────────────────────────────────────────────────┤
│                              KEY METRICS                                     │  ROW 5: Metrics
│ Impressions │Subscribers│Engagement│Conv. Rate│Activation│Time to Value│Ref│
│ [Increase]  │[Increase] │[Increase]│[Increase]│[Increase]│  [Reduce]   │[+]│
├─────────────────────────────────────────────────────────────────────────────┤
│ LEGEND: [Green]=Active [Yellow]=Decision [Blue]=Conversion [Teal]=Delivery  │  ROW 6: Legend
│         [Purple]=Planned                                                    │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

## Page Layout

### Canvas Settings

```xml
<mxGraphModel dx="992" dy="1139" grid="1" gridSize="10" guides="1"
              tooltips="1" connect="1" arrows="1" fold="1" page="0"
              pageScale="1" pageWidth="1600" pageHeight="900">
```

### Element Positioning

| Element | X Position | Y Position | Notes |
|---------|------------|------------|-------|
| Title | 300 | 20 | Centered, width 600 |
| Subtitle | 300 | 55 | Below title |
| Phase Labels | 80, 500, 720 | 90 | ACQUISITION, COMMIT, DELIVERY |
| Stage Headers | 80-1000 | 130 | 7 stages evenly spaced |
| Activity Boxes | 80-1130 | 160-310 | Within each stage column |
| Feedback Loop | Full width | 350-400 | Curved arrow bottom |
| Key Metrics Header | 80 | 430 | Full width bar |
| Metric Labels | 80-1000 | 460 | 7 metric labels (one per stage) |
| Metric Buttons | 80-1000 | 490 | Increase/Reduce badges |
| Legend | 80 | 540 | Bottom left |

### Stage Widths

```
Stage 1-3 (Acquisition): 130px each, x=80, 220, 360
Stage 4 (Commit/Knot): 130px, x=500 (with highlight box)
Stage 5-7 (Delivery): 130px each, x=720, 860, 1000
```

---

## The 7 Stages

### ACQUISITION (Left Side - Narrowing)

| Stage | Name | Purpose |
|-------|------|---------|
| 1 | **Awareness** | Where they discover you |
| 2 | **Nurturing** | How you build trust |
| 3 | **Consideration** | What moves them to evaluate |

### COMMIT (Center - The Knot)

| Stage | Name | Purpose |
|-------|------|---------|
| 4 | **Conversion** | The purchase moment |

### DELIVERY (Right Side - Expanding)

| Stage | Name | Purpose |
|-------|------|---------|
| 5 | **Onboarding** | Setting them up for success |
| 6 | **Launch** | First value / aha moment |
| 7 | **Results** | Outcomes + expansion |

---

## Color Coding

### Phase Colors

| Phase | Label Background | Label Color | Box Background |
|-------|-----------------|-------------|----------------|
| ACQUISITION | `#e3f2fd` | `#1565c0` | `#90EE90` (active) |
| COMMIT | `#fff3e0` | `#e65100` | `#FFD166` (decision) |
| DELIVERY | `#e8f5e9` | `#2e7d32` | `#d5e8d4` (delivery) |

### Activity Box Colors

| Status | Fill | Stroke | Use |
|--------|------|--------|-----|
| Active | `#90EE90` | `#82b366` | Working activities |
| Decision | `#FFD166` | `#f4a261` | Choice points in Commit |
| Delivery | `#d5e8d4` | `#82b366` | Post-purchase stages |
| Result | `#b2f2bb` | `#2f9e44` | Outcomes achieved |
| Planned | `#9370DB` | `#7B68EE` | Future/dashed |
| Conversion | `#4DA6FF` | `#3399FF` | Purchase action |

### Arrow Colors

| Connection | Color | Width |
|------------|-------|-------|
| Stage-to-stage | `#666666` | 2px |
| Into Commit | `#e65100` | 3px |
| Out of Commit | `#2e7d32` | 3px |
| Feedback loop | `#2f9e44` | 2px, dashed |

---

## XML Patterns

### Title Section

```xml
<mxCell id="bt-title" value="BOW-TIE FUNNEL: [Business Name]"
  style="text;html=1;strokeColor=none;fillColor=none;align=center;
         verticalAlign=middle;fontSize=24;fontStyle=1;fontColor=#1a1a2e;"
  vertex="1" parent="1">
    <mxGeometry x="300" y="20" width="600" height="40" as="geometry"/>
</mxCell>

<mxCell id="bt-subtitle" value="Customer Journey: Discovery → Results"
  style="text;html=1;strokeColor=none;fillColor=none;align=center;
         verticalAlign=middle;fontSize=12;fontColor=#666666;"
  vertex="1" parent="1">
    <mxGeometry x="300" y="55" width="600" height="20" as="geometry"/>
</mxCell>
```

### Phase Labels (3 sections)

```xml
<!-- ACQUISITION (stages 1-3) -->
<mxCell id="bt-acq-label" value="ACQUISITION"
  style="text;html=1;strokeColor=none;fillColor=#e3f2fd;align=center;
         verticalAlign=middle;fontSize=14;fontStyle=1;fontColor=#1565c0;rounded=1;"
  vertex="1" parent="1">
    <mxGeometry x="80" y="90" width="400" height="30" as="geometry"/>
</mxCell>

<!-- COMMIT (stage 4 - the knot) -->
<mxCell id="bt-commit-label" value="COMMIT"
  style="text;html=1;strokeColor=none;fillColor=#fff3e0;align=center;
         verticalAlign=middle;fontSize=14;fontStyle=1;fontColor=#e65100;rounded=1;"
  vertex="1" parent="1">
    <mxGeometry x="500" y="90" width="200" height="30" as="geometry"/>
</mxCell>

<!-- DELIVERY (stages 5-7) -->
<mxCell id="bt-delivery-label" value="DELIVERY"
  style="text;html=1;strokeColor=none;fillColor=#e8f5e9;align=center;
         verticalAlign=middle;fontSize=14;fontStyle=1;fontColor=#2e7d32;rounded=1;"
  vertex="1" parent="1">
    <mxGeometry x="720" y="90" width="400" height="30" as="geometry"/>
</mxCell>
```

### Stage Headers (7 columns)

```xml
<mxCell id="bt-stage1" value="AWARENESS"
  style="text;html=1;strokeColor=none;fillColor=none;align=center;
         verticalAlign=middle;fontSize=10;fontStyle=1;fontColor=#666666;"
  vertex="1" parent="1">
    <mxGeometry x="80" y="130" width="130" height="20" as="geometry"/>
</mxCell>
<!-- Repeat for: NURTURING, CONSIDERATION, CONVERSION, ONBOARDING, LAUNCH, RESULTS -->
```

### The Knot (Commit Highlight Box)

The center section gets a visual highlight box to emphasize the conversion moment:

```xml
<!-- Highlight box around Commit stage -->
<mxCell id="bt-cv-box" value=""
  style="rounded=1;whiteSpace=wrap;html=1;fillColor=#fff3e0;
         strokeColor=#e65100;strokeWidth=3;"
  vertex="1" parent="1">
    <mxGeometry x="540" y="155" width="130" height="150" as="geometry"/>
</mxCell>
```

### Activity Boxes

```xml
<!-- Active activity (green) -->
<mxCell id="bt-aw-1" value="YouTube Video"
  style="rounded=1;whiteSpace=wrap;html=1;fillColor=#90EE90;
         strokeColor=#82b366;fontSize=10;fontStyle=1;"
  vertex="1" parent="1">
    <mxGeometry x="80" y="160" width="130" height="35" as="geometry"/>
</mxCell>

<!-- Decision activity (yellow) - in Commit stage -->
<mxCell id="bt-cv-1" value="Click Product Link"
  style="rounded=1;whiteSpace=wrap;html=1;fillColor=#FFD166;
         strokeColor=#f4a261;fontSize=10;fontStyle=1;"
  vertex="1" parent="1">
    <mxGeometry x="555" y="165" width="100" height="40" as="geometry"/>
</mxCell>

<!-- Conversion action (blue) -->
<mxCell id="bt-cv-3" value="PURCHASE"
  style="rounded=1;whiteSpace=wrap;html=1;fillColor=#4DA6FF;
         strokeColor=#3399FF;fontColor=#ffffff;fontSize=11;fontStyle=1;"
  vertex="1" parent="1">
    <mxGeometry x="555" y="265" width="100" height="30" as="geometry"/>
</mxCell>

<!-- Delivery activity (light green) -->
<mxCell id="bt-on-1" value="Download&#xa;Skill/System"
  style="rounded=1;whiteSpace=wrap;html=1;fillColor=#d5e8d4;
         strokeColor=#82b366;fontSize=10;fontStyle=1;"
  vertex="1" parent="1">
    <mxGeometry x="720" y="170" width="130" height="40" as="geometry"/>
</mxCell>

<!-- Result activity (darker green) -->
<mxCell id="bt-re-1" value="Get Outcomes"
  style="rounded=1;whiteSpace=wrap;html=1;fillColor=#b2f2bb;
         strokeColor=#2f9e44;fontSize=10;fontStyle=1;"
  vertex="1" parent="1">
    <mxGeometry x="1000" y="165" width="130" height="45" as="geometry"/>
</mxCell>

<!-- Planned activity (purple, dashed) -->
<mxCell id="bt-on-3" value="(Future: Upsell)"
  style="rounded=1;whiteSpace=wrap;html=1;fillColor=#9370DB;
         strokeColor=#7B68EE;strokeWidth=2;dashed=1;fontSize=9;"
  vertex="1" parent="1">
    <mxGeometry x="720" y="270" width="130" height="40" as="geometry"/>
</mxCell>
```

### Stage Arrows

```xml
<!-- Standard connector -->
<mxCell id="bt-arrow1"
  style="edgeStyle=orthogonalEdgeStyle;rounded=0;orthogonalLoop=1;
         jettySize=auto;html=1;strokeColor=#666666;strokeWidth=2;"
  edge="1" parent="1">
    <mxGeometry relative="1" as="geometry">
        <mxPoint x="210" y="222" as="sourcePoint"/>
        <mxPoint x="220" y="222" as="targetPoint"/>
    </mxGeometry>
</mxCell>

<!-- Into Commit (orange, thicker) -->
<mxCell id="bt-arrow3"
  style="edgeStyle=orthogonalEdgeStyle;rounded=0;orthogonalLoop=1;
         jettySize=auto;html=1;strokeColor=#e65100;strokeWidth=3;"
  edge="1" parent="1">
    <mxGeometry relative="1" as="geometry">
        <mxPoint x="490" y="230" as="sourcePoint"/>
        <mxPoint x="540" y="230" as="targetPoint"/>
    </mxGeometry>
</mxCell>

<!-- Out of Commit (green, thicker) -->
<mxCell id="bt-arrow4"
  style="edgeStyle=orthogonalEdgeStyle;rounded=0;orthogonalLoop=1;
         jettySize=auto;html=1;strokeColor=#2e7d32;strokeWidth=3;"
  edge="1" parent="1">
    <mxGeometry relative="1" as="geometry">
        <mxPoint x="670" y="230" as="sourcePoint"/>
        <mxPoint x="720" y="230" as="targetPoint"/>
    </mxGeometry>
</mxCell>
```

### Feedback Loop

The curved arrow from Results back to Awareness:

```xml
<mxCell id="bt-loop" value=""
  style="curved=1;endArrow=classic;html=1;strokeColor=#2f9e44;
         strokeWidth=2;dashed=1;exitX=0.5;exitY=1;entryX=0.5;entryY=1;"
  edge="1" parent="1">
    <mxGeometry width="50" height="50" relative="1" as="geometry">
        <mxPoint x="1065" y="310" as="sourcePoint"/>
        <mxPoint x="145" y="310" as="targetPoint"/>
        <Array as="points">
            <mxPoint x="1065" y="370"/>
            <mxPoint x="600" y="370"/>
            <mxPoint x="145" y="370"/>
        </Array>
    </mxGeometry>
</mxCell>

<mxCell id="bt-loop-label" value="Referrals feed back to Awareness"
  style="text;html=1;strokeColor=none;fillColor=none;align=center;
         verticalAlign=middle;fontSize=9;fontStyle=2;fontColor=#2f9e44;"
  vertex="1" parent="1">
    <mxGeometry x="450" y="375" width="200" height="20" as="geometry"/>
</mxCell>
```

### Key Metrics Section

The metrics row shows the KPI for each stage with Increase/Reduce badges:

```xml
<!-- Key Metrics Header Bar -->
<mxCell id="bt-metrics-header" value="KEY METRICS"
  style="rounded=0;whiteSpace=wrap;html=1;fillColor=#1a1a2e;
         fontColor=#ffffff;fontSize=12;fontStyle=1;align=center;"
  vertex="1" parent="1">
    <mxGeometry x="80" y="430" width="1050" height="30" as="geometry"/>
</mxCell>

<!-- Metric Labels (one per stage) -->
<mxCell id="bt-metric-1" value="Impressions"
  style="text;html=1;strokeColor=none;fillColor=none;align=center;
         verticalAlign=middle;fontSize=10;fontStyle=2;"
  vertex="1" parent="1">
    <mxGeometry x="80" y="465" width="130" height="20" as="geometry"/>
</mxCell>
<!-- Repeat for: Subscribers, Engagement, Conv. Rate, Activation, Time to Value, Referrals -->

<!-- Metric Badges (Increase = green, Reduce = red) -->
<mxCell id="bt-metric-badge-1" value="Increase"
  style="rounded=1;whiteSpace=wrap;html=1;fillColor=#40c057;
         fontColor=#ffffff;fontSize=10;fontStyle=1;"
  vertex="1" parent="1">
    <mxGeometry x="95" y="490" width="100" height="25" as="geometry"/>
</mxCell>

<!-- Time to Value uses Reduce (red badge) -->
<mxCell id="bt-metric-badge-6" value="Reduce"
  style="rounded=1;whiteSpace=wrap;html=1;fillColor=#fa5252;
         fontColor=#ffffff;fontSize=10;fontStyle=1;"
  vertex="1" parent="1">
    <mxGeometry x="875" y="490" width="100" height="25" as="geometry"/>
</mxCell>
```

### Key Metrics by Stage

| Stage | Metric | Goal | Badge Color |
|-------|--------|------|-------------|
| Awareness | Impressions | Increase | Green |
| Nurturing | Subscribers | Increase | Green |
| Consideration | Engagement | Increase | Green |
| Conversion | Conv. Rate | Increase | Green |
| Onboarding | Activation | Increase | Green |
| Launch | Time to Value | **Reduce** | **Red** |
| Results | Referrals | Increase | Green |

---

### Legend

```xml
<mxCell id="bt-legend-box" value=""
  style="rounded=1;whiteSpace=wrap;html=1;fillColor=#f5f5f5;strokeColor=#e9ecef;"
  vertex="1" parent="1">
    <mxGeometry x="80" y="540" width="600" height="40" as="geometry"/>
</mxCell>

<mxCell id="bt-legend-title" value="LEGEND:"
  style="text;html=1;strokeColor=none;fillColor=none;align=left;
         verticalAlign=middle;fontSize=10;fontStyle=1;"
  vertex="1" parent="1">
    <mxGeometry x="90" y="550" width="60" height="20" as="geometry"/>
</mxCell>

<!-- Color swatches inline -->
<mxCell id="bt-leg-active" value=""
  style="rounded=1;whiteSpace=wrap;html=1;fillColor=#90EE90;strokeColor=#82b366;"
  vertex="1" parent="1">
    <mxGeometry x="150" y="552" width="15" height="15" as="geometry"/>
</mxCell>
<mxCell id="bt-leg-active-l" value="Active"
  style="text;html=1;strokeColor=none;fillColor=none;align=left;fontSize=9;"
  vertex="1" parent="1">
    <mxGeometry x="168" y="550" width="45" height="20" as="geometry"/>
</mxCell>

<mxCell id="bt-leg-decision" value=""
  style="rounded=1;whiteSpace=wrap;html=1;fillColor=#FFD166;strokeColor=#f4a261;"
  vertex="1" parent="1">
    <mxGeometry x="220" y="552" width="15" height="15" as="geometry"/>
</mxCell>
<mxCell id="bt-leg-decision-l" value="Decision"
  style="text;html=1;strokeColor=none;fillColor=none;align=left;fontSize=9;"
  vertex="1" parent="1">
    <mxGeometry x="238" y="550" width="50" height="20" as="geometry"/>
</mxCell>

<mxCell id="bt-leg-conversion" value=""
  style="rounded=1;whiteSpace=wrap;html=1;fillColor=#4DA6FF;strokeColor=#3399FF;"
  vertex="1" parent="1">
    <mxGeometry x="295" y="552" width="15" height="15" as="geometry"/>
</mxCell>
<mxCell id="bt-leg-conversion-l" value="Conversion"
  style="text;html=1;strokeColor=none;fillColor=none;align=left;fontSize=9;"
  vertex="1" parent="1">
    <mxGeometry x="313" y="550" width="60" height="20" as="geometry"/>
</mxCell>

<mxCell id="bt-leg-delivery" value=""
  style="rounded=1;whiteSpace=wrap;html=1;fillColor=#d5e8d4;strokeColor=#82b366;"
  vertex="1" parent="1">
    <mxGeometry x="380" y="552" width="15" height="15" as="geometry"/>
</mxCell>
<mxCell id="bt-leg-delivery-l" value="Delivery"
  style="text;html=1;strokeColor=none;fillColor=none;align=left;fontSize=9;"
  vertex="1" parent="1">
    <mxGeometry x="398" y="550" width="50" height="20" as="geometry"/>
</mxCell>

<mxCell id="bt-leg-results" value=""
  style="rounded=1;whiteSpace=wrap;html=1;fillColor=#b2f2bb;strokeColor=#2f9e44;"
  vertex="1" parent="1">
    <mxGeometry x="455" y="552" width="15" height="15" as="geometry"/>
</mxCell>
<mxCell id="bt-leg-results-l" value="Results"
  style="text;html=1;strokeColor=none;fillColor=none;align=left;fontSize=9;"
  vertex="1" parent="1">
    <mxGeometry x="473" y="550" width="45" height="20" as="geometry"/>
</mxCell>

<mxCell id="bt-leg-planned" value=""
  style="rounded=1;whiteSpace=wrap;html=1;fillColor=#9370DB;strokeColor=#7B68EE;dashed=1;"
  vertex="1" parent="1">
    <mxGeometry x="525" y="552" width="15" height="15" as="geometry"/>
</mxCell>
<mxCell id="bt-leg-planned-l" value="Planned"
  style="text;html=1;strokeColor=none;fillColor=none;align=left;fontSize=9;"
  vertex="1" parent="1">
    <mxGeometry x="543" y="550" width="45" height="20" as="geometry"/>
</mxCell>
```

---

## Business-Specific Activities

### By Business Type

When populating activities, use these patterns based on business type:

| Stage | Creator/Coach | SaaS | Agency |
|-------|---------------|------|--------|
| Awareness | YouTube, Substack, Social | SEO, LinkedIn, Content | Referrals, Case studies |
| Nurturing | Lead magnet, Newsletter | Free trial, Docs | Newsletter, Audits |
| Consideration | Binge content, See offers | Demo, Pricing page | Discovery call |
| Conversion | Checkout, Purchase | Subscribe, Contract | Proposal, Retainer |
| Onboarding | Download, Instructions | Setup, Training | Kickoff, Asset collection |
| Launch | First use, First win | Integration live | First deliverable |
| Results | Outcomes, Referral | ROI, Case study | Results, Renewal |

---

## ID Naming Convention

Use consistent prefixes for bow-tie elements:

```
bt-title          - Main title
bt-subtitle       - Subtitle
bt-acq-label      - Acquisition phase label
bt-commit-label   - Commit phase label
bt-delivery-label - Delivery phase label
bt-stage1         - Stage 1 header (through bt-stage7)
bt-aw-1           - Awareness activity 1
bt-nu-1           - Nurturing activity 1
bt-co-1           - Consideration activity 1
bt-cv-1           - Conversion activity 1
bt-cv-box         - Commit highlight box
bt-on-1           - Onboarding activity 1
bt-la-1           - Launch activity 1
bt-re-1           - Results activity 1
bt-arrow1         - Connector arrows (sequential)
bt-loop           - Feedback loop
bt-loop-label     - Feedback loop label
bt-metrics-header - Key Metrics header bar
bt-metric-1       - Metric label 1 (through bt-metric-7)
bt-metric-badge-1 - Metric badge 1 (through bt-metric-badge-7)
bt-legend-box     - Legend container
bt-leg-*          - Legend items (active, decision, conversion, delivery, results, planned)
```

---

## Generation Checklist

Before outputting a bow-tie:

**Structure:**
- [ ] Title reflects business name
- [ ] Subtitle: "Customer Journey: Discovery → Conversion → Results"
- [ ] All 7 stages have headers
- [ ] Each stage has 3-4 activities (vertically stacked)

**Phase Labels:**
- [ ] ACQUISITION spans stages 1-3 (green border)
- [ ] COMMIT spans stage 4 (orange border/fill)
- [ ] DELIVERY spans stages 5-7 (green border)

**Activity Boxes:**
- [ ] Active items use green
- [ ] Decision items use yellow (in Commit stage)
- [ ] PURCHASE box uses blue (key conversion action)
- [ ] Delivery items use teal/light green
- [ ] Results items use darker green
- [ ] Planned/future items use purple + dashed border

**Connections:**
- [ ] Arrows connect between stages (horizontal flow)
- [ ] Thicker orange arrows INTO Commit
- [ ] Thicker green arrows OUT OF Commit
- [ ] Feedback loop (dashed green) from Results back to Awareness

**Key Metrics Row:**
- [ ] Dark header bar labeled "KEY METRICS"
- [ ] 7 metric labels (one per stage)
- [ ] 7 metric badges below labels
- [ ] Most badges say "Increase" (green)
- [ ] "Time to Value" badge says "Reduce" (red)

**Legend:**
- [ ] Legend includes all 6 colors used (Active, Decision, Conversion, Delivery, Results, Planned)

---

**Created:** 2026-01-06
**Purpose:** Standard reference for generating bow-tie funnels in .drawio format
