# Business X-Ray

**Map, diagnose, and optimize your business operations through progressive visual analysis.**

Transform your business into clear visual diagrams that reveal bottlenecks, automation opportunities, and growth paths.

---

## What You Get

| Output | Description |
|--------|-------------|
| **Business Map** | 7-column snapshot of your entire business (Traffic, Converters, Products, Funnels, Math, Team, Goals) |
| **Bow-Tie Funnel** | Customer journey from Awareness → Conversion → Results with key metrics |
| **Process Swimlanes** | 3-level drill-down showing WHO does WHAT with WHICH systems |
| **Opportunity Roadmap** | Prioritized action plan based on identified bottlenecks |

---

## Quick Start (Claude Web App)

### Step 1: Duplicate This Repo

Click **"Use this template"** or **Fork** this repository to your GitHub account.

### Step 2: Connect to Draw.io

1. Go to [app.diagrams.net](https://app.diagrams.net)
2. Click **File → Open from → GitHub**
3. Authorize with your GitHub account
4. Select this repository
5. Your diagrams will sync automatically!

### Step 3: Start Your X-Ray

1. Go to [claude.ai](https://claude.ai)
2. Start a new conversation
3. Upload the `.claude/skills/business-x-ray.zip` file (or copy the SKILL.md content)
4. Say: **"Let's do a business x-ray"**

Claude will guide you through the interview process and generate diagrams you can paste into Draw.io.

---

## How It Works

### The Interview Process

Claude acts as a business consultant, asking one question at a time:

1. **Business Map** - Extracts your traffic sources, products, funnels, team, and goals
2. **Bow-Tie Funnel** - Maps your customer journey from discovery to results
3. **Lead Gen Process** - Drills into how you generate and qualify leads
4. **Sales Process** - Maps discovery → presentation → proposal → close
5. **Fulfillment** - Maps onboarding → delivery → support → results

### 3-Level Drill-Down

| Level | Shows | Example |
|-------|-------|---------|
| **Level 1** | WHO does the work | Owner creates content, AI distributes, Team handles support |
| **Level 2** | WHICH systems handle it | ConvertKit for email, Calendly for booking, Notion for CRM |
| **Level 3** | HOW each system works | Step-by-step execution with tool names |

### Opportunity Discovery

As you map your business, Claude identifies:

- **Bottlenecks** (Red) - Steps slowing everything down
- **Automate** (Orange) - AI/tools could handle this
- **High Value** (Green) - Keep doing this yourself
- **Digital Assets** (Purple) - Templates/SOPs needed

---

## Folder Structure

```
business-x-ray/
├── README.md                    ← You are here
├── diagrams/                    ← Your .drawio files go here (syncs with Draw.io)
│   └── .gitkeep
└── .claude/
    └── skills/
        └── business-x-ray/
            ├── SKILL.md         ← Main skill file
            ├── references/      ← Supporting docs
            │   ├── bowtie-funnel.md
            │   ├── business-archetypes.md
            │   ├── drawio-standards.md
            │   ├── opportunity-categories.md
            │   └── swimlane-templates.md
            ├── workflows/       ← Step-by-step guides
            │   ├── progressive-interview.md
            │   ├── expand-process.md
            │   ├── generate-roadmap.md
            │   └── scan-diagram.md
            └── examples/        ← Templates
                ├── example-business-map.xml
                └── example-progress-state.yaml
```

---

## Using with Claude Web App

### Option A: Upload the ZIP

1. Download `business-x-ray.zip` from this repo
2. Upload it to Claude at the start of your conversation
3. Say "Let's do a business x-ray"

### Option B: Copy SKILL.md Content

1. Open `.claude/skills/business-x-ray/SKILL.md`
2. Copy the entire content
3. Paste it into Claude with: "Use this skill to help me map my business"

### Saving Diagrams

When Claude generates XML for a diagram:

1. Copy the XML code block
2. Go to [app.diagrams.net](https://app.diagrams.net)
3. File → New → Create
4. Arrange → Insert → Advanced → XML
5. Paste the XML
6. File → Save to → GitHub
7. Select your repo's `diagrams/` folder

---

## Resume Later

Claude provides a YAML progress block you can save:

```yaml
# Business X-Ray Progress - Copy this to resume later
stage: phase_3_process
business_type: coach
business_map_complete: true
bowtie_complete: true
pain_points: [content_creation, sales_calls]
selected_process: lead_generation
expanded_processes: []
pending: [sales_process, fulfillment]
opportunities_flagged: 3
last_updated: 2024-01-15
```

To resume:
1. Start a new Claude conversation
2. Paste the progress block
3. Say "Continue my Business X-Ray"

---

## For Developers (Claude Code CLI)

If you have Claude Code installed:

```bash
# Clone the repo
git clone https://github.com/YOUR_USERNAME/business-x-ray.git
cd business-x-ray

# Start the X-Ray
claude "Let's do a business x-ray"
```

Claude Code will:
- Generate .drawio files directly in `diagrams/`
- Track progress automatically
- Use sub-agents for efficient diagram generation

---

## Business Types Supported

| Type | Typical Flow |
|------|--------------|
| **Coach** | YouTube → Email → Call → High-ticket |
| **Course Creator** | Content → Lead Magnet → Webinar → Course |
| **Agency** | Referrals → Proposal → Retainer |
| **SaaS** | Content → Trial → Subscription |
| **Service Provider** | Referrals → Call → Proposal → Retainer |
| **Creator** | Platform → Subscribe → Products |

---

## Need Help?

- **Questions about the skill**: Open an issue in this repo
- **General Claude questions**: [Claude Help Center](https://support.anthropic.com)
- **Draw.io questions**: [Draw.io Documentation](https://www.drawio.com/doc/)

---

## Credits

Created by [Rashid Khamis](https://rashidkhamis.com) | [The 2-Hour CLO](https://the2hourclo.com)

Built with [Claude Code](https://claude.ai/claude-code)
