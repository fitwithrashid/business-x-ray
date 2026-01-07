# Generate Roadmap Workflow

**Create a prioritized 90-day action plan from all identified opportunities.**

---

## Purpose

After process expansion is complete, this workflow:
1. Aggregates all opportunities across expanded processes
2. Prioritizes using impact + effort framework
3. Generates 90-day roadmap with reasoning
4. Allows user to shuffle order
5. Outputs actionable .drawio page

---

## Prerequisites

Before running this workflow:
- [ ] Business Map complete
- [ ] Bow-Tie Funnel complete
- [ ] At least one process expanded with opportunities

---

## Step 1: Aggregate Opportunities

### Collect All Flagged Items

From each expanded process, gather:

| Category | Symbol | Source |
|----------|--------|--------|
| Bottlenecks | 🔴 | Red-annotated steps |
| Automate | 🟠 | Orange-annotated steps |
| Digital Assets | 🟣 | Gaps identified in interview |
| High Value | 🟢 | Green steps needing protection |

### Present Summary

> "Here are all the opportunities we've identified:
>
> **🔴 BOTTLENECKS (slowing you down)**
> 1. [Process A: Step X] - takes [X] hours/week
> 2. [Process B: Step Y] - causing delays
>
> **🟠 AUTOMATE (AI/tools could help)**
> 1. [Process A: Step Z] - repetitive, rule-based
> 2. [Process C: Step W] - lookup/research work
>
> **🟣 DIGITAL ASSETS (need to build)**
> 1. [Lead magnet landing page] - missing from funnel
> 2. [Email sequence] - not set up yet
>
> **🟢 PROTECT (high-value time)**
> 1. [Creative work] - getting squeezed by admin
>
> Does this capture everything?"

---

## Step 2: Priority Scoring

### Impact vs Effort Framework

For each opportunity, assess:

| Factor | Question | Score 1-3 |
|--------|----------|-----------|
| **Impact** | How much will this improve the business? | 1=Low, 3=High |
| **Effort** | How hard/time-consuming to implement? | 1=High effort, 3=Easy |
| **Dependency** | Does other stuff depend on this? | 1=No, 3=Blocks others |

**Priority Score = Impact + Effort + Dependency**

### Priority Matrix

| Score | Priority | When to Do |
|-------|----------|------------|
| 7-9 | **Critical** | Month 1, Week 1-2 |
| 5-6 | **Important** | Month 1-2 |
| 3-4 | **Nice-to-have** | Month 3 |
| 1-2 | **Later** | After 90 days |

### Present Suggested Order

> "Based on impact and effort, here's my suggested priority:
>
> **MONTH 1: Foundation**
> Week 1-2: 🔴 [Bottleneck 1] - Score 8 (high impact, enables everything else)
> Week 3-4: 🟠 [Automation 1] - Score 7 (quick win, immediate time savings)
>
> **MONTH 2: Build**
> Week 5-6: 🟣 [Digital Asset] - Score 6 (enables scale)
> Week 7-8: 🔴 [Bottleneck 2] - Score 5 (secondary issue)
>
> **MONTH 3: Optimize**
> Week 9-10: 🟠 [Automation 2] - Score 5 (refinement)
> Week 11-12: 🟢 [Protect time] - Score 4 (sustainability)
>
> **Want to shuffle this order? Tell me which items to move.**"

---

## Step 3: User Adjusts Order

### Allow Reordering

If user wants to adjust:

> "No problem! Let me reorder:
>
> You said: '[User's preference]'
>
> Updated order:
> 1. [New priority 1] - moved because [reason]
> 2. [New priority 2] - moved because [reason]
> ...
>
> Does this look right?"

### Validate Dependencies

If user moves something that has dependencies:

> "Quick note: [Item X] depends on [Item Y] being done first. If you do X before Y, you might hit blockers.
>
> Do you want to:
> A) Keep the order you specified (knowing this risk)
> B) Do Y first, then X"

---

## Step 4: Generate Roadmap Page

### Simple Prioritized Checklist

The roadmap is a **single-column prioritized list** with checkboxes. No complex grids or timelines.

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
│  ☐ 🔴 Streamline client onboarding                          │
│     Create intake form + welcome sequence                    │
│                                                              │
│  DO LATER                                                    │
│  ────────                                                    │
│  ☐ 🟠 Set up social scheduling                              │
│     Batch create + schedule with Buffer/Later                │
│                                                              │
│  ☐ 🟢 Protect creative time                                 │
│     Block 2-hour focus sessions on calendar                  │
│                                                              │
└─────────────────────────────────────────────────────────────┘
```

### Checklist Item Format

Each item has:
- **Checkbox** (☐) - User checks off when done
- **Icon** (🔴🟠🟣🟢) - Category at a glance
- **Title** - What to do (bold, one line)
- **Description** - How to do it (1 line, smaller text)

### Priority Sections

| Section | Meaning | Typical Items |
|---------|---------|---------------|
| **DO FIRST** | Critical blockers, quick wins | 1-3 items |
| **DO NEXT** | Important but not urgent | 2-4 items |
| **DO LATER** | Nice-to-have, refinements | 2-3 items |

### Color Reference (for draw.io)

| Type | Icon | Border | Fill |
|------|------|--------|------|
| Bottleneck Fix | 🔴 | #FF6B6B | #fff5f5 |
| Automation | 🟠 | #FFA500 | #fff8e6 |
| Digital Asset | 🟣 | #9370DB | #f5f0ff |
| Protect Time | 🟢 | #90EE90 | #f0fff0 |

---

## Step 5: Add to .drawio File

### For Claude Code

Add as new page to existing Business X-Ray file:

```xml
<diagram name="90-Day Roadmap" id="page-roadmap">
    <!-- Roadmap content from references/drawio-standards.md -->
</diagram>
```

### For Web/ChatGPT

Output XML:

> "Add this as the final page of your Business X-Ray:
>
> ```xml
> [Roadmap XML]
> ```
>
> 1. Open your .drawio file
> 2. Insert new page at the end
> 3. Name it '90-Day Roadmap'
> 4. Paste this XML"

---

## Step 6: Actionable Next Steps

### Week 1 Actions

> "Here's what to do THIS WEEK:
>
> **🔴 [Task 1 Title]**
> 1. [Specific action step 1]
> 2. [Specific action step 2]
> 3. [Specific action step 3]
>
> **Estimated time:** [X] hours
> **Tools needed:** [list]
> **Output:** [what success looks like]
>
> Once you complete this, come back and we can:
> - Check it off and move to Week 2
> - Troubleshoot if you're stuck
> - Adjust the plan if priorities changed"

---

## Roadmap Completion Message

> "Your Business X-Ray is complete:
>
> 📊 **Business Map** - Your 7-column snapshot
> 🎯 **Bow-Tie Funnel** - Customer journey from awareness to results
> 🔄 **[X] Process Swimlanes** - Detailed flows with opportunities marked
> 📅 **90-Day Roadmap** - Prioritized action plan
>
> **Your .drawio file has [X] pages** - use the tabs at the bottom to navigate.
>
> **What's next?**
> Start with Week 1 of your roadmap. When you've made progress, come back and we can:
> - Expand more processes
> - Adjust priorities
> - Deep-dive on implementation
>
> Good luck!"

---

## Resume Block

```yaml
# Business X-Ray Progress - COMPLETE
stage: roadmap_complete
business_type: [type]
business_map_complete: true
bowtie_complete: true
pain_points: [all identified]
expanded_processes: [list]
opportunities_flagged: [count]
roadmap_created: true
roadmap_items: [count]
last_updated: [date]
```

---

## Follow-Up Sessions

When user returns after implementing:

> "Welcome back! Last time we created your 90-Day Roadmap.
>
> What progress have you made?
>
> A) Completed Week 1-2 tasks - let's review and move to next phase
> B) Got stuck on something - let's troubleshoot
> C) Priorities changed - let's update the roadmap
> D) Ready to expand another process"

### Progress Tracking

If user completed tasks:

> "Great work! Let me update your roadmap:
>
> ✅ [Completed task 1]
> ✅ [Completed task 2]
>
> **Next up (Week 3-4):**
> - [ ] [Next task]
>
> Want me to give you the specific steps for this one?"

---

## Alternative: Quick Roadmap

If user only completed Business Map + Bow-Tie (no process expansion):

> "We haven't expanded any processes yet, but I can still create a starter roadmap based on the pain points you mentioned:
>
> **Month 1:**
> - Expand [highest pain process] swimlane
> - Identify specific automation opportunities
>
> **Month 2:**
> - Implement [obvious quick wins]
> - Build [missing digital asset]
>
> **Month 3:**
> - Expand [second pain process]
> - Optimize based on results
>
> This is a lighter roadmap. Want to go deeper by expanding a process first?"
