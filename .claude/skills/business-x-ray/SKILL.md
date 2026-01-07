---
name: business-x-ray
description: Map, diagnose, and optimize business operations through progressive visual analysis. Creates Business Maps, Bow-Tie Funnels, and Process Swimlanes with 3-level drill-down.
---

# Business X-Ray

**Map, diagnose, and optimize business operations through progressive visual analysis.**

USE WHEN user says 'business x-ray', 'map my business', 'identify bottlenecks', 'process improvement', 'visualize my business', or wants to find operational improvements.

---

## Workflow Routing

### Start New X-Ray → `workflows/progressive-interview.md`

**When to use:**
- User says "business x-ray", "map my business", "let's do an x-ray"
- Starting fresh with new business
- User wants complete business overview

**Output:** Business Map + Bow-Tie Funnel (.drawio)

---

### Expand Process → `workflows/expand-process.md`

**When to use:**
- User says "drill down", "expand this", "show me more detail"
- Business Map exists, user wants to go deeper
- Specific process identified for optimization

**Output:** Process swimlane with annotations (.drawio page)

---

### Generate Roadmap → `workflows/generate-roadmap.md`

**When to use:**
- User says "what should I fix", "prioritize", "roadmap"
- Opportunities have been identified
- User ready for action plan

**Output:** 90-Day Roadmap (.drawio page)

---

### Resume Session

**When to use:**
- User pastes YAML progress state
- User says "continue where we left off"

**Process:** Parse YAML state, load to context, continue from that point

---

### Scan Existing Diagram → `workflows/scan-diagram.md`

**When to use:**
- User has an existing .drawio file they've been working on
- User says "scan my diagram", "read my business map", "what do I have so far"
- User uploads or provides path to .drawio file

**Process:**
1. Read the .drawio XML
2. Extract what's already mapped (Business Map columns, Bow-Tie stages, expanded processes)
3. Identify gaps and incomplete sections
4. Present summary: "Here's what I found... What would you like to work on?"

**Output:** Reconstructed business state + next steps

---

## Core Principles (Always Apply)

1. **Inference-first** - Claude guesses more, user confirms more (less typing)
2. **ONE question at a time** - Never bundle multiple questions
3. **Goals = Performance Goals** - Actions that drive the funnel (e.g., "Post 3x/week" not "Get 10K subs")
4. **Goals emerge** - Infer from pain points, don't ask directly
5. **Map first, annotate after** - Get process right, then flag opportunities
6. **Fix before moving on** - Actionable output at each checkpoint

---

## Annotation Colors

| Annotation | Border | Color | Meaning |
|------------|--------|-------|---------|
| **Bottleneck** | Solid thick | Red `#FF6B6B` | Slowing things down |
| **Automate** | Dashed | Orange `#FFA500` | AI/tool could do this |
| **High Value** | Solid thick | Green `#90EE90` | Human should keep doing |
| **Digital Asset** | Solid | Purple `#9370DB` | Needs to be built |

---

## Business Archetypes (Quick Reference)

| Type | Trigger Words | Typical Flow |
|------|---------------|--------------|
| **Coach** | coaching, consulting, clients, calls | YouTube → Email → Call → High-ticket |
| **Course Creator** | course, membership, students, launch | Content → Lead Magnet → Webinar → Course |
| **Agency** | agency, clients, retainer, projects | Referrals → Proposal → Retainer |
| **SaaS** | software, app, subscribers, MRR | Content → Trial → Subscription |
| **Service Provider** | services, done-for-you, monthly | Referrals → Call → Proposal → Retainer |
| **Creator** | content, audience, followers, views | Platform → Subscribe → Products |

For detailed patterns: `read references/business-archetypes.md`

---

## When to Activate This Skill

**Activate when:**
- User wants to visualize their business structure
- User wants to identify operational bottlenecks
- User wants to find automation/delegation opportunities
- User mentions "business map", "process improvement", "operations"

**Do NOT activate when:**
- User wants content creation → delegate to `write` skill
- User wants YouTube strategy → delegate to `youtube-strategy` skill
- User wants to track metrics → delegate to `metrics-tracking` skill

---

## References (Load On-Demand)

| Reference | Purpose |
|-----------|---------|
| [references/drawio-standards.md](references/drawio-standards.md) | XML patterns, colors, styles |
| [references/business-archetypes.md](references/business-archetypes.md) | Pre-built inference patterns |
| [references/swimlane-templates.md](references/swimlane-templates.md) | Common process templates |
| [references/opportunity-categories.md](references/opportunity-categories.md) | Fix options per category |

---

## Examples

| Example | Purpose |
|---------|---------|
| [examples/example-business-map.xml](examples/example-business-map.xml) | Complete 7-column Business Map |
| [examples/example-progress-state.yaml](examples/example-progress-state.yaml) | Resume format template |

---

## Output Format

All outputs go in a **single .drawio file** with multiple pages:

| Page | Content |
|------|---------|
| Business Overview | Bow-Tie Funnel (top) + 7-column Business Map (bottom) |
| [Area] Page | Main swimlane + sub-processes stacked vertically (scroll down) |
| Action Roadmap | Prioritized checklist (DO FIRST / DO NEXT / DO LATER) |

**Page structure:** Each area (Lead Gen, Sales, Fulfillment) gets ONE page with main process on top and sub-process details below. No tab jumping - scroll down for more detail.

**Why single file?** Works with Claude Web App (copy XML, save as .drawio), no file system dependencies.

---

## Sub-Agent Architecture (Keep Orchestrator Clean)

**CRITICAL:** Diagram generation is token-heavy. Spawn sub-agents to keep main context clean.

### When Generating Diagrams

```
Orchestrator (this conversation)
│
├── Conducts interview (inference-first)
├── Tracks progress state
├── Makes decisions about what to expand
│
└── SPAWNS sub-agent for diagram generation:

    Task tool call:
    - subagent_type: "general-purpose"
    - prompt: "Generate .drawio XML for [specific diagram]
               Data: [extracted business data]
               Template: read references/drawio-standards.md
               Output: Save to [file path]"
```

### Sub-Agent Prompts

**Business Overview (Page 1):**
```
Generate Business Overview .drawio page with:
- Bow-Tie Funnel (top): [7 stages with data]
- Business Map (bottom): [7 columns with data]
Read references/drawio-standards.md for XML patterns.
Save to: diagrams/[business-name]-x-ray.drawio
```

**Process Swimlane (Page 2+):**
```
Add [Process Name] page to existing .drawio file:
- Level 1: Process Flow with actor lanes (Owner | AI | Team | Output)
- Phases: [list of phases with actor assignments]
- Level 2 (if expanded): System Detail - which systems handle the phase
- Level 3 (case-by-case): Execution Detail - how the system works (with tool names)
- Apply annotations: [bottleneck/automate/high-value markers]
Read references/drawio-standards.md for XML patterns.
File: diagrams/[business-name]-x-ray.drawio
```

**Why sub-agents?**
- Diagram XML is verbose (2000+ tokens per page)
- Keeps orchestrator focused on interview + decisions
- Sub-agent has fresh context for accurate generation
- Orchestrator just tracks: "Page 2 generated ✓"

**Parallel sub-agents:** For larger updates (e.g., generating multiple pages or updating existing + adding new), spawn multiple sub-agents in parallel to speed up generation.

---

## Cross-Platform Mode

### Claude Code CLI
- **Use sub-agents** for diagram generation (keeps orchestrator clean)
- Save .drawio directly to `diagrams/` folder
- Resume by reading local file

### Claude Web App / ChatGPT
- Sub-agents not available - generate XML inline
- Output XML for user to copy-paste into diagrams.net
- Resume via YAML progress block
- GitHub integration available: diagrams.net → File → Save to → GitHub

---

**Created:** 2025-01-02
**Updated:** 2026-01-06
