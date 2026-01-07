# Scan Existing Diagram Workflow

**Read an existing .drawio file and reconstruct the business state for continued work.**

---

## Purpose

When user has been working on a Business X-Ray diagram and wants to continue with AI assistance, this workflow:
1. Reads the .drawio XML
2. Extracts what's already mapped
3. Identifies gaps and incomplete sections
4. Presents a summary so the session can continue

---

## Trigger Phrases

- "scan my diagram"
- "read my business map"
- "what do I have so far"
- "continue from my diagram"
- "load my .drawio file"

---

## Process

### Step 1: Get the File

> "I can scan your existing Business X-Ray diagram. Please either:
> - Paste the file path (e.g., `diagrams/Business Map.drawio`)
> - Or paste the XML content directly"

*[wait for response]*

### Step 2: Read and Parse

Read the .drawio file and extract:

#### From Page Structure
- List all pages (diagram names)
- Identify which standard pages exist:
  - Business Overview (Bow-Tie + Business Map on Page 1)
  - Process swimlanes (Content, Sales, Fulfillment, etc.)
  - Action Roadmap

#### From Business Overview Page
Look for 7 columns and extract content:

| Column | Look For | Extract |
|--------|----------|---------|
| TRAFFIC | Header "TRAFFIC" or "Traffic Sources" | List of sources (YouTube, LinkedIn, etc.) |
| CONVERTERS | Header "CONVERTERS" | Landing pages, lead magnets |
| PRODUCTS | Header "PRODUCTS" | Product names + prices |
| FUNNELS | Header "FUNNELS" | Email sequences, sales flows |
| MATH | Header "MATH" or "INCOME/EXPENSES" | Revenue, expenses, profit |
| TEAM | Header "TEAM" | Roles listed |
| GOALS | Header "GOALS" | Performance goals |

#### From Bow-Tie Section (top of Page 1)
Extract the 7 stages:
- Awareness sources
- Nurturing mechanisms
- Consideration touchpoints
- Commit/conversion point
- Onboarding steps
- Launch activities
- Results/outcomes

#### From Process Swimlanes
For each process page:
- Process name
- Lanes defined (Owner, AI, VA, Output)
- Steps mapped
- Annotations applied (Red/Orange/Green borders)
- Opportunities flagged

#### From Roadmap Page
- Month 1/2/3 tasks
- Priority order
- Completion status

### Step 3: Identify Gaps

Check for incomplete sections:

**Business Map gaps:**
- Empty columns (no items)
- Missing calculations in MATH
- No goals defined

**Bow-Tie gaps:**
- Stages with no content
- Missing connections

**Process gaps:**
- Processes mentioned but not expanded
- Swimlanes without annotations (review pass not done)
- No opportunities identified

### Step 4: Present Summary

> "Here's what I found in your Business X-Ray:
>
> **Page 1 - Business Overview:**
> - [x] Bow-Tie Funnel (top section)
> - [x] Business Map (bottom section)
>
> **Process Pages:**
> - [ ] Content Creation (not expanded yet)
> - [x] Sales Process
>
> **Roadmap:**
> - [ ] Action Roadmap (not created yet)
>
> **Business Map Status:**
> - TRAFFIC: YouTube, LinkedIn, Substack
> - CONVERTERS: Lead magnet exists
> - PRODUCTS: Coaching ($5K), Course ($497)
> - FUNNELS: Welcome sequence
> - MATH: $15K/month, expenses unknown
> - TEAM: Solo
> - GOALS: Not defined yet
>
> **Bow-Tie:** Complete (7 stages mapped)
>
> **Expanded Processes:**
> - Sales Process: Mapped + annotated, 2 opportunities flagged
>
> **Gaps to Address:**
> 1. Goals column is empty
> 2. Content Creation not expanded yet
> 3. No roadmap created
>
> **What would you like to work on?**
> A) Fill in the Goals (Performance Goals)
> B) Expand Content Creation process
> C) Create the 90-Day Roadmap
> D) Something else"

*[wait for user choice]*

### Step 5: Continue with Appropriate Workflow

Based on user choice, route to:
- Goals → Continue in progressive-interview.md (just the GOALS column)
- Expand process → expand-process.md
- Roadmap → generate-roadmap.md

---

## XML Parsing Patterns

### Find Pages
```xml
<diagram name="Business Overview" id="page-1">  <!-- Contains Bow-Tie + Business Map -->
<diagram name="Content Creation" id="page-2">
<diagram name="Sales Process" id="page-3">
```

### Find Column Headers
Look for text cells with column names:
```xml
<mxCell value="TRAFFIC" style="...fontStyle=1..."
<mxCell value="PRODUCTS" style="...fontStyle=1..."
```

### Find Items Under Columns
Items are positioned below headers (higher y value, similar x range)

### Find Annotations
Check stroke colors:
- `strokeColor=#FF6B6B` = Bottleneck (Red)
- `strokeColor=#FFA500` = Automate (Orange)
- `strokeColor=#90EE90` = High Value (Green)
- `dashed=1` = Automation opportunity

### Find Swimlane Structure
```xml
<mxCell value="Process Name" style="swimlane;horizontal=0..."
<mxCell value="Owner" style="swimlane;horizontal=0..." parent="pool-id"
```

---

## Cross-Platform Notes

### Claude Code
- Read file directly with Read tool
- Parse XML in context

### Claude Web / ChatGPT
- User pastes XML content
- Same parsing logic applies

---

## Resume State Generation

After scanning, generate a YAML progress block:

```yaml
# Business X-Ray Progress - Reconstructed from diagram
stage: process_expansion
business_type: [inferred from products/traffic]
business_map_complete: [true if all 7 columns have content]
bowtie_complete: [true if Bow-Tie page exists with content]
pain_points: [inferred from annotations]
selected_process: null
expanded_processes: [list of process pages found]
pending: [list of gaps identified]
opportunities_flagged: [count of annotated steps]
last_updated: [current date]
```

---

## Example Scan Output

> "I've scanned your Business X-Ray. Here's the current state:
>
> **Business Type:** Online coaching (based on products)
>
> **Business Map (6/7 complete):**
> | Column | Status | Content |
> |--------|--------|---------|
> | TRAFFIC | Complete | YouTube, LinkedIn |
> | CONVERTERS | Complete | Free guide, Landing page |
> | PRODUCTS | Complete | 1:1 Coaching $5K, Group $2K |
> | FUNNELS | Complete | Welcome, Nurture sequences |
> | MATH | Partial | Income: $12K/mo, Expenses: ? |
> | TEAM | Complete | Solo + 1 VA |
> | GOALS | Empty | Not yet defined |
>
> **Bow-Tie Funnel:** Complete
>
> **Process Swimlanes:**
> - Sales Process: Mapped + 3 opportunities flagged
> - Content Creation: Not started
>
> **Roadmap:** Not created yet
>
> **Recommended next step:** Define your Performance Goals (actions that drive your funnel), then expand Content Creation.
>
> What would you like to focus on?"

---

## Error Handling

### File Not Found
> "I couldn't find that file. Please check the path and try again, or paste the XML content directly."

### Invalid XML
> "The file doesn't appear to be a valid .drawio file. Make sure it's the right file and try again."

### Empty Diagram
> "This diagram appears to be empty or just starting. Would you like to begin the Business X-Ray interview from scratch?"

### Unrecognized Structure
> "I found content but it doesn't match the standard Business X-Ray layout. I can see [X pages]. Would you like me to describe what I found, or start fresh with the standard template?"
