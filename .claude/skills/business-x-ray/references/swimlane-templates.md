# Swimlane Templates

**Pre-built process templates for fast swimlane generation.**

Use these as starting points - adjust based on user's actual process during expansion.

---

## How to Use

1. Identify which template matches user's process
2. Present template as inference: "Based on what you described, here's the typical flow..."
3. User confirms or adjusts
4. Generate swimlane using the confirmed structure

---

## Template 1: Content Creation

**Common for:** Coaches, Course Creators, Creators

### Default Lanes

| Lane | Owner | Typical Activities |
|------|-------|-------------------|
| **Strategy** | Owner | Topic ideation, content calendar, trend research |
| **Creation** | Owner/AI | Writing, recording, editing, design |
| **Publishing** | Owner/VA/Tool | Scheduling, posting, cross-platform distribution |
| **Engagement** | Owner/VA | Comments, DMs, community interaction |

### Default Flow

```
START → Topic Research → Content Brief → Draft/Record → Edit → Review → Schedule → Publish → Engage → END
```

### Common Swimlane Structure

```
┌─────────────────────────────────────────────────────────────────────────────────┐
│ CONTENT CREATION                                                                 │
├──────────┬──────────────────────────────────────────────────────────────────────┤
│ Owner    │ [Research] → [Brief] → [Draft] → [Review] ─────────→ [Engage]       │
├──────────┼──────────────────────────────────────────────────────────────────────┤
│ AI/Tool  │              ↗ [AI Draft]    ↗ [AI Edit]                             │
├──────────┼──────────────────────────────────────────────────────────────────────┤
│ VA       │                                        → [Schedule] → [Publish]      │
├──────────┼──────────────────────────────────────────────────────────────────────┤
│ Output   │                                                        [Post Live]   │
└──────────┴──────────────────────────────────────────────────────────────────────┘
```

### Typical Bottlenecks (Red)
- Topic research taking too long
- Editing bottleneck
- Owner doing all scheduling

### Typical AI Opportunities (Orange)
- AI draft generation
- AI editing/polish
- Automated scheduling
- Repurposing to other formats

### XML Template

```xml
<mxCell id="cc-pool" value="Content Creation" style="swimlane;horizontal=0;whiteSpace=wrap;html=1;startSize=30;fillColor=#f5f5f5;strokeColor=#666666;fontStyle=1;fontSize=14;" vertex="1" parent="1">
    <mxGeometry x="40" y="40" width="900" height="400" as="geometry"/>
</mxCell>

<!-- Owner Lane -->
<mxCell id="cc-lane-owner" value="Owner" style="swimlane;horizontal=0;whiteSpace=wrap;html=1;startSize=80;fillColor=#dae8fc;strokeColor=#6c8ebf;fontStyle=1;" vertex="1" parent="cc-pool">
    <mxGeometry x="30" width="870" height="100" as="geometry"/>
</mxCell>

<!-- AI/Tool Lane -->
<mxCell id="cc-lane-ai" value="AI / Tool" style="swimlane;horizontal=0;whiteSpace=wrap;html=1;startSize=80;fillColor=#ffe6cc;strokeColor=#d79b00;fontStyle=1;" vertex="1" parent="cc-pool">
    <mxGeometry x="30" y="100" width="870" height="100" as="geometry"/>
</mxCell>

<!-- VA Lane -->
<mxCell id="cc-lane-va" value="VA" style="swimlane;horizontal=0;whiteSpace=wrap;html=1;startSize=80;fillColor=#e1d5e7;strokeColor=#9673a6;fontStyle=1;" vertex="1" parent="cc-pool">
    <mxGeometry x="30" y="200" width="870" height="100" as="geometry"/>
</mxCell>

<!-- Output Lane -->
<mxCell id="cc-lane-output" value="Output" style="swimlane;horizontal=0;whiteSpace=wrap;html=1;startSize=80;fillColor=#d5e8d4;strokeColor=#82b366;fontStyle=1;" vertex="1" parent="cc-pool">
    <mxGeometry x="30" y="300" width="870" height="100" as="geometry"/>
</mxCell>
```

---

## Template 2: Sales Process

**Common for:** Coaches, Agencies, Service Providers

### Default Lanes

| Lane | Owner | Typical Activities |
|------|-------|-------------------|
| **Lead Handling** | Owner/VA | Lead capture, qualification, booking |
| **Sales Calls** | Owner | Discovery, pitch, objection handling |
| **Follow-up** | Owner/VA/Tool | Proposals, reminders, closing |
| **Admin** | VA/Tool | Contracts, payments, CRM updates |

### Default Flow

```
Lead In → Qualify → Book Call → Discovery Call → <Decision> → Proposal → Follow-up → Close → Onboard
```

### Common Swimlane Structure

```
┌─────────────────────────────────────────────────────────────────────────────────┐
│ SALES PROCESS                                                                    │
├──────────┬──────────────────────────────────────────────────────────────────────┤
│ Lead     │ [Capture] → [Qualify] ──────────────────────────────────────────→    │
├──────────┼──────────────────────────────────────────────────────────────────────┤
│ Owner    │            ↗ [Book Call] → [Discovery] → <Fit?> → [Close]           │
├──────────┼──────────────────────────────────────────────────────────────────────┤
│ VA/Tool  │                                    ↗ [Proposal] → [Follow-up]        │
├──────────┼──────────────────────────────────────────────────────────────────────┤
│ Output   │                                                    → [Contract]      │
└──────────┴──────────────────────────────────────────────────────────────────────┘
```

### Typical Bottlenecks (Red)
- Discovery calls eating all time
- Proposal creation manual and slow
- Follow-up slipping through cracks

### Typical AI Opportunities (Orange)
- Lead qualification scoring
- Proposal generation
- Automated follow-up sequences
- Calendar booking automation

### XML Template

```xml
<mxCell id="sp-pool" value="Sales Process" style="swimlane;horizontal=0;whiteSpace=wrap;html=1;startSize=30;fillColor=#f5f5f5;strokeColor=#666666;fontStyle=1;fontSize=14;" vertex="1" parent="1">
    <mxGeometry x="40" y="40" width="900" height="400" as="geometry"/>
</mxCell>

<!-- Lead Lane -->
<mxCell id="sp-lane-lead" value="Lead" style="swimlane;horizontal=0;whiteSpace=wrap;html=1;startSize=80;fillColor=#d5e8d4;strokeColor=#82b366;fontStyle=1;" vertex="1" parent="sp-pool">
    <mxGeometry x="30" width="870" height="100" as="geometry"/>
</mxCell>

<!-- Owner Lane -->
<mxCell id="sp-lane-owner" value="Owner" style="swimlane;horizontal=0;whiteSpace=wrap;html=1;startSize=80;fillColor=#dae8fc;strokeColor=#6c8ebf;fontStyle=1;" vertex="1" parent="sp-pool">
    <mxGeometry x="30" y="100" width="870" height="100" as="geometry"/>
</mxCell>

<!-- VA/Tool Lane -->
<mxCell id="sp-lane-va" value="VA / Tool" style="swimlane;horizontal=0;whiteSpace=wrap;html=1;startSize=80;fillColor=#e1d5e7;strokeColor=#9673a6;fontStyle=1;" vertex="1" parent="sp-pool">
    <mxGeometry x="30" y="200" width="870" height="100" as="geometry"/>
</mxCell>

<!-- Output Lane -->
<mxCell id="sp-lane-output" value="Output" style="swimlane;horizontal=0;whiteSpace=wrap;html=1;startSize=80;fillColor=#f8cecc;strokeColor=#b85450;fontStyle=1;" vertex="1" parent="sp-pool">
    <mxGeometry x="30" y="300" width="870" height="100" as="geometry"/>
</mxCell>
```

---

## Template 3: Client Onboarding

**Common for:** All service-based businesses

### Default Lanes

| Lane | Owner | Typical Activities |
|------|-------|-------------------|
| **Client** | Client | Forms, access setup, orientation |
| **Owner** | Owner | Kickoff call, goals setting, relationship building |
| **System** | Tool/VA | Welcome emails, access provisioning, setup |
| **Delivery** | Owner/Team | First deliverable, quick win |

### Default Flow

```
Payment → Welcome → Intake Form → Access Setup → Kickoff Call → First Session/Deliverable → Check-in
```

### Common Swimlane Structure

```
┌─────────────────────────────────────────────────────────────────────────────────┐
│ CLIENT ONBOARDING                                                                │
├──────────┬──────────────────────────────────────────────────────────────────────┤
│ Client   │ [Payment] → [Intake Form] ──────────────→ [First Session] → [Win!]  │
├──────────┼──────────────────────────────────────────────────────────────────────┤
│ System   │          ↗ [Welcome Email] → [Access Setup] → [Reminders]           │
├──────────┼──────────────────────────────────────────────────────────────────────┤
│ Owner    │                           ↗ [Kickoff Call] → [Goals Set]            │
├──────────┼──────────────────────────────────────────────────────────────────────┤
│ Output   │                                              → [Client Ready]        │
└──────────┴──────────────────────────────────────────────────────────────────────┘
```

### Typical Bottlenecks (Red)
- Manual intake form review
- Access setup inconsistent
- Kickoff calls not scheduled quickly

### Typical AI Opportunities (Orange)
- Automated welcome sequence
- Self-service access provisioning
- Intake form processing
- Scheduling automation

### Digital Assets Needed (Purple)
- Welcome email template
- Intake form
- Onboarding checklist
- Getting started guide

### XML Template

```xml
<mxCell id="co-pool" value="Client Onboarding" style="swimlane;horizontal=0;whiteSpace=wrap;html=1;startSize=30;fillColor=#f5f5f5;strokeColor=#666666;fontStyle=1;fontSize=14;" vertex="1" parent="1">
    <mxGeometry x="40" y="40" width="900" height="400" as="geometry"/>
</mxCell>

<!-- Client Lane -->
<mxCell id="co-lane-client" value="Client" style="swimlane;horizontal=0;whiteSpace=wrap;html=1;startSize=80;fillColor=#d5e8d4;strokeColor=#82b366;fontStyle=1;" vertex="1" parent="co-pool">
    <mxGeometry x="30" width="870" height="100" as="geometry"/>
</mxCell>

<!-- System Lane -->
<mxCell id="co-lane-system" value="System" style="swimlane;horizontal=0;whiteSpace=wrap;html=1;startSize=80;fillColor=#ffe6cc;strokeColor=#d79b00;fontStyle=1;" vertex="1" parent="co-pool">
    <mxGeometry x="30" y="100" width="870" height="100" as="geometry"/>
</mxCell>

<!-- Owner Lane -->
<mxCell id="co-lane-owner" value="Owner" style="swimlane;horizontal=0;whiteSpace=wrap;html=1;startSize=80;fillColor=#dae8fc;strokeColor=#6c8ebf;fontStyle=1;" vertex="1" parent="co-pool">
    <mxGeometry x="30" y="200" width="870" height="100" as="geometry"/>
</mxCell>

<!-- Output Lane -->
<mxCell id="co-lane-output" value="Output" style="swimlane;horizontal=0;whiteSpace=wrap;html=1;startSize=80;fillColor=#f8cecc;strokeColor=#b85450;fontStyle=1;" vertex="1" parent="co-pool">
    <mxGeometry x="30" y="300" width="870" height="100" as="geometry"/>
</mxCell>
```

---

## Template 4: Fulfillment / Delivery

**Common for:** Coaches, Course Creators, Agencies

### Default Lanes

| Lane | Owner | Typical Activities |
|------|-------|-------------------|
| **Client** | Client | Engagement, feedback, completion |
| **Owner** | Owner | Core delivery, coaching, strategy |
| **Team/VA** | Team | Support, scheduling, admin |
| **System** | Tool | Automation, content delivery, tracking |

### Default Flow

```
Kickoff → Delivery Cycle [Prep → Execute → Review → Iterate] → Completion → Results Capture → Offboard
```

### Common Swimlane Structure

```
┌─────────────────────────────────────────────────────────────────────────────────┐
│ FULFILLMENT / DELIVERY                                                           │
├──────────┬──────────────────────────────────────────────────────────────────────┤
│ Client   │ [Engage] ────────────────→ [Complete Tasks] → [Give Feedback]        │
├──────────┼──────────────────────────────────────────────────────────────────────┤
│ Owner    │ [Prep] → [Deliver] → [Review] ──────────────→ [Capture Results]     │
├──────────┼──────────────────────────────────────────────────────────────────────┤
│ Team/VA  │        ↗ [Support] → [Schedule] → [Admin]                            │
├──────────┼──────────────────────────────────────────────────────────────────────┤
│ System   │ [Content Delivery] → [Progress Track] ─────→ [Completion Cert]       │
└──────────┴──────────────────────────────────────────────────────────────────────┘
```

### Typical Bottlenecks (Red)
- Client not engaging
- Prep work time-consuming
- Results not being captured

### Typical AI Opportunities (Orange)
- Automated content delivery
- Progress tracking
- Check-in reminders
- Results documentation

### XML Template

```xml
<mxCell id="fd-pool" value="Fulfillment / Delivery" style="swimlane;horizontal=0;whiteSpace=wrap;html=1;startSize=30;fillColor=#f5f5f5;strokeColor=#666666;fontStyle=1;fontSize=14;" vertex="1" parent="1">
    <mxGeometry x="40" y="40" width="900" height="400" as="geometry"/>
</mxCell>

<!-- Client Lane -->
<mxCell id="fd-lane-client" value="Client" style="swimlane;horizontal=0;whiteSpace=wrap;html=1;startSize=80;fillColor=#d5e8d4;strokeColor=#82b366;fontStyle=1;" vertex="1" parent="fd-pool">
    <mxGeometry x="30" width="870" height="100" as="geometry"/>
</mxCell>

<!-- Owner Lane -->
<mxCell id="fd-lane-owner" value="Owner" style="swimlane;horizontal=0;whiteSpace=wrap;html=1;startSize=80;fillColor=#dae8fc;strokeColor=#6c8ebf;fontStyle=1;" vertex="1" parent="fd-pool">
    <mxGeometry x="30" y="100" width="870" height="100" as="geometry"/>
</mxCell>

<!-- Team/VA Lane -->
<mxCell id="fd-lane-team" value="Team / VA" style="swimlane;horizontal=0;whiteSpace=wrap;html=1;startSize=80;fillColor=#e1d5e7;strokeColor=#9673a6;fontStyle=1;" vertex="1" parent="fd-pool">
    <mxGeometry x="30" y="200" width="870" height="100" as="geometry"/>
</mxCell>

<!-- System Lane -->
<mxCell id="fd-lane-system" value="System" style="swimlane;horizontal=0;whiteSpace=wrap;html=1;startSize=80;fillColor=#ffe6cc;strokeColor=#d79b00;fontStyle=1;" vertex="1" parent="fd-pool">
    <mxGeometry x="30" y="300" width="870" height="100" as="geometry"/>
</mxCell>
```

---

## Template 5: Admin / Operations

**Common for:** All businesses (often hidden but causing pain)

### Default Lanes

| Lane | Owner | Typical Activities |
|------|-------|-------------------|
| **Finance** | Owner/VA | Invoicing, bookkeeping, payments |
| **Client Mgmt** | Owner/VA | CRM, communication, scheduling |
| **Tools/Systems** | Owner/Tool | Software management, integrations |
| **Planning** | Owner | Calendar, priorities, strategy |

### Default Flow

```
Daily Check-in → Task Triage → Execute Tasks → Update Systems → End-of-day Review
```

### Common Swimlane Structure

```
┌─────────────────────────────────────────────────────────────────────────────────┐
│ ADMIN / OPERATIONS                                                               │
├──────────┬──────────────────────────────────────────────────────────────────────┤
│ Finance  │ [Invoices] → [Payments] → [Bookkeeping] → [Reports]                  │
├──────────┼──────────────────────────────────────────────────────────────────────┤
│ Client   │ [CRM Update] → [Communications] → [Scheduling]                       │
├──────────┼──────────────────────────────────────────────────────────────────────┤
│ Systems  │ [Tool Admin] → [Integrations] → [Backups]                            │
├──────────┼──────────────────────────────────────────────────────────────────────┤
│ Owner    │ [Priority Setting] ───────────────────→ [Week Review]                │
└──────────┴──────────────────────────────────────────────────────────────────────┘
```

### Typical Bottlenecks (Red)
- Owner doing all admin
- Manual invoicing
- Too many tools, no integration

### Typical AI Opportunities (Orange)
- Automated invoicing
- CRM auto-updates
- Scheduling automation
- Tool integration (Zapier, Make)

---

## Quick Reference: Lane Colors

| Lane Type | Fill | Stroke | Use For |
|-----------|------|--------|---------|
| Owner | `#dae8fc` | `#6c8ebf` | Business owner actions |
| AI/Tool | `#ffe6cc` | `#d79b00` | Automated or AI-assisted |
| VA/Team | `#e1d5e7` | `#9673a6` | Delegated to humans |
| Client | `#d5e8d4` | `#82b366` | Client/customer actions |
| System | `#ffe6cc` | `#d79b00` | Tool/platform actions |
| Output | `#f8cecc` | `#b85450` | Results/deliverables |

---

## Step Shape Reference

| Shape | Style | Use For |
|-------|-------|---------|
| Rounded Rectangle | `rounded=1` | Normal process steps |
| Diamond | `rhombus` | Decision points |
| Ellipse | `ellipse` | Start/End points |
| Rectangle | `rounded=0` | Data/Documents |

---

## Using Templates in expand-process.md

When user describes their process:

1. **Match to template** - Which template is closest?
2. **Present as inference:**
   > "Based on what you described, your [Process Name] probably looks something like this:
   > [Show ASCII diagram from template]
   > Is this roughly right, or should we adjust?"
3. **Adjust based on feedback** - Add/remove steps, change lane assignments
4. **Generate XML** - Use template structure with customized content
5. **Apply annotations** - Mark bottlenecks (red) and opportunities (orange) after mapping

