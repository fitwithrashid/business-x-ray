# Progressive Interview Workflow

**Extract business information through inference-first questioning, building visual artifacts incrementally.**

---

## Execution Instructions

**Follow these steps exactly. Do NOT skip steps or combine questions.**

### Step 1: Opening
Say this EXACTLY:
> "Let's map your business! I'll make some educated guesses based on what you tell me - just confirm or correct as we go.
>
> **What type of business do you run?**"

STOP. Wait for response.

### Step 2: Identify Business Type
From their response, identify which archetype they match:
- Coach / Consultant
- Course Creator
- Agency
- SaaS
- Service Provider
- Creator / Influencer

### Step 3: Present Pre-Filled Business Map Guess
Based on archetype, present YOUR GUESS of their business:
> "Based on what you've told me, here's my initial map:
>
> **Business Type:** [Your guess]
> **Likely Traffic Sources:** [Your guess based on type]
> **Typical Funnel:** [Your guess based on type]
> **Team Structure:** [Your guess]
>
> How close am I? What should I adjust?"

STOP. Wait for response.

### Step 4: Extract 7 Columns (ONE AT A TIME)
Go through each column. Ask ONE question, wait for response, then next:

1. **TRAFFIC** → "For a [type], I'm guessing your main traffic is [guess]. That right?"
2. **CONVERTERS** → "So from [platform], people land on... do you have a lead magnet?"
3. **PRODUCTS** → "What's your main product right now and its price?"
4. **FUNNELS** → "Once someone downloads [lead magnet], what happens next?"
5. **MATH** → "At $X with roughly Y sales/month, that's about $Z. Monthly expenses roughly?"
6. **TEAM** → "Sounds like you're solo - is that right?"
7. **GOALS** → "To keep your funnel running, your key actions are: [guess]. That right?"

**CRITICAL:** After EACH question, STOP and wait for their response before asking the next.

### Step 5: Checkpoint - Business Map Complete
> "Here's your Business Map:
>
> [Show summary of all 7 columns]
>
> Does this capture your business accurately? Any adjustments?"

STOP. Wait for confirmation.

**After confirmation:** SPAWN A SUB-AGENT to generate the diagram:
```
Use the Task tool with subagent_type="general-purpose" and model="opus":
"Generate Business Map .drawio. Data: [paste 7 columns].
Read references/drawio-standards.md for XML patterns.
Save to: diagrams/[business-name]-x-ray.drawio"
```

### Step 6: Infer Bow-Tie Funnel
From Business Map data, present the 7-stage customer journey:
> "Based on your Business Map, here's your customer journey:
>
> **ACQUISITION:** [Awareness] → [Nurturing] → [Consideration]
> **COMMIT:** [Conversion moment]
> **DELIVERY:** [Onboarding] → [Launch] → [Results]
>
> How does this look? What's missing?"

STOP. Wait for response.

### Step 7: Checkpoint - Business Overview Complete
> "Great! Your Business Overview is complete.
>
> Now let's map out how things actually work. Which area should we dive into first?
>
> A) Lead Generation - How you attract and capture leads
> B) Sales - How you convert leads to customers
> C) Fulfillment - How you deliver and get results"

STOP. Wait for choice.

**After Bow-Tie confirmation (before asking about areas):** SPAWN A SUB-AGENT to add Bow-Tie to diagram:
```
Use the Task tool with subagent_type="general-purpose" and model="opus":
"Add Bow-Tie Funnel to existing .drawio file.

CRITICAL: Generate a 7-COLUMN GRID, NOT a flowchart.
- Row 1: Title
- Row 2: 3 phase banners (ACQUISITION | COMMIT | DELIVERY)
- Row 3: 7 column headers (AWARENESS | NURTURING | etc.)
- Row 4: 3-4 SEPARATE RECTANGLES stacked vertically in EACH column
- Each activity = its own box (e.g., 'YouTube', 'Substack', 'X/Threads' = 3 separate boxes)

Data per column:
- Awareness: [list]
- Nurturing: [list]
- Consideration: [list]
- Conversion: [list + PURCHASE box]
- Onboarding: [list]
- Launch: [list]
- Results: [list]

Read references/bowtie-funnel.md for exact XML patterns.
File: diagrams/[business-name]-x-ray.drawio"
```

### Step 8: Map Selected Process (Level 1)
Based on their choice, map the process with actor lanes (Owner | AI | Team | Output).

Present your inference:
> "Based on what you told me, here's your [Process] flow:
>
> **PHASE 1:** [Activity] → Owner
> **PHASE 2:** [Activity] → AI/System
> **PHASE 3:** [Activity] → Owner
> **PHASE 4:** [Activity] → Output
>
> Who owns each step? What's missing?"

STOP. Wait for response. Iterate until confirmed.

**After process flow is confirmed:** SPAWN A SUB-AGENT to add Process Swimlane:
```
Use the Task tool with subagent_type="general-purpose" and model="opus":
"Add [Process Name] swimlane page to .drawio file.
Lanes: Owner | AI | Team | Output
Phases: [list phases with actor assignments]
Read references/drawio-standards.md for XML patterns.
File: diagrams/[business-name]-x-ray.drawio"
```

### Step 9: Probe for Gaps
If any phase seems incomplete, probe:
> "You mentioned [X]. But what happens after - [specific gap question]?"

Use the gap detection tables below to know what to probe for.

### Step 10: Pain Discovery (Observe, Don't Ask)
As you map, listen for pain signals:
- "I do all of that myself" → Bottleneck
- "That takes forever" → Time sink
- "I should do that but don't" → Missing step
- "I don't have that" → Digital asset needed

After mapping, OBSERVE:
> "I noticed a few things while we mapped:
> - [X] and [Y] are all you - those seem like time sinks
> - [Z] could probably be automated
>
> Want to annotate these on the diagram?"

### Step 11: Decision Point
> "Your [Process] page is done. What's next?
>
> A) Map another area - Sales or Fulfillment
> B) Generate roadmap - Prioritized action plan
> C) Stop here - Take what we have and start fixing"

STOP. Wait for choice. Loop back to Step 8 if they choose A.

### Step 12: Output Diagram + Resume Block
Generate the .drawio file (or XML for web users) and provide the resume YAML block.

**Final diagram output:** SPAWN A SUB-AGENT to finalize and verify diagram:
```
Use the Task tool with subagent_type="general-purpose" and model="opus":
"Finalize Business X-Ray .drawio file.
Verify all pages are present:
- Page 1: Business Overview (Bow-Tie + Business Map)
- Page 2+: Process swimlanes with annotations
Apply opportunity annotations (bottleneck=red, automate=orange, high-value=green, digital-asset=purple).
Read references/drawio-standards.md for color codes.
File: diagrams/[business-name]-x-ray.drawio"
```

---

## Purpose

This workflow guides the progressive extraction of business information, producing:
1. **Business Map** (7 columns) - Complete business snapshot
2. **Bow-Tie Funnel** - Customer journey visualization
3. **Lead Generation Swimlane** - First process mapped with pain discovered through mapping

Each phase ends with a **checkpoint** where user confirms before proceeding.

**Key insight:** Pain points are discovered through the process of mapping, not declared by the user upfront. As we walk through each step together, bottlenecks and opportunities surface naturally.

---

## Core Principles (Apply Throughout)

1. **Inference-first** - Claude guesses more, user confirms more (less typing for user)
2. **ONE question at a time** - NEVER stack multiple questions in one message
3. **Map first, annotate after** - Get structure right, then flag issues
4. **Fix before moving on** - Actionable output at each checkpoint
5. **Goals emerge, not asked** - Listen for goals in pain points, don't ask directly
6. **Think like a consultant** - Know what's SUPPOSED to be there, probe for gaps

---

## Business Consultant Thinking

**You are a business consultant, not a form-filler.** Don't just accept what the user says - probe for the complete picture.

### Mental Model: How Businesses Actually Work

Every business has these connected systems. If one is missing, the others break:

```
LEAD GENERATION (Acquisition)
├── Traffic Generation → How strangers discover you
│   └── Content Creation is ONE METHOD of generating traffic
├── Lead Capture → How viewers become contacts (email, booking, etc.)
├── Lead Nurture → How contacts become warm leads
└── Qualification → How warm leads become sales-ready

SALES (Conversion)
├── Discovery → Understanding prospect needs
├── Presentation → Showing solution
├── Proposal → Making the offer
└── Close → Getting commitment

FULFILLMENT (Delivery)
├── Onboarding → Setting up for success
├── Delivery → Providing the value
├── Support → Handling issues
└── Results → Capturing outcomes + referrals
```

### Completeness Checks (Always Probe)

**When user says "I create content":**
- ✅ GOOD: "Where does that content live? YouTube? Newsletter?"
- ✅ PROBE: "When someone watches your video, what's the next step for them? How do they become a lead?"
- ❌ BAD: Just accepting "I create content" and moving on

**When user describes Lead Gen but misses Lead Capture:**
- ✅ PROBE: "So you have YouTube and Instagram. When someone watches, how do you capture them as a lead? Lead magnet? Email signup? Direct booking?"
- ❌ BAD: Assuming they have it figured out

**When user describes process but misses handoffs:**
- ✅ PROBE: "OK so content goes out on YouTube. What happens next? How does someone go from viewer to subscriber to lead to client?"
- ❌ BAD: Mapping isolated activities without connections

### The Funnel Logic Test

After gathering info, mentally check: **Does this funnel make sense?**

| If They Have | But Missing | Ask About |
|--------------|-------------|-----------|
| Traffic (YouTube, content) | Lead Capture | "How do viewers become contacts? CTA? Lead magnet?" |
| Lead Capture (email signup) | Nurture Sequence | "What happens after someone joins your list?" |
| Nurture (emails) | Qualification | "How do you know when someone's ready to buy?" |
| Qualified Leads | Sales Process | "What's the actual sales conversation look like?" |
| Sales Calls | Follow-up | "What happens if they don't buy on the call?" |
| Clients | Onboarding | "How do new clients get started with you?" |
| Delivery | Results Capture | "How do you capture testimonials and referrals?" |

### Probing Questions by Gap Type

**Traffic exists but no Capture:**
> "You mentioned YouTube videos. Where do you send viewers? Is there a call-to-action to capture them as leads?"

**Capture exists but no Nurture:**
> "So people download your lead magnet. Then what? Do they hear from you again, or is it one-and-done?"

**Nurture exists but no Qualification:**
> "Your email sequence is running. How do you know when someone's actually interested vs. just on the list?"

**Activities described without outcomes:**
> "Walk me through what happens when someone sees your content for the first time all the way to becoming a client. What's the journey?"

### Common Gaps to Surface

**By Business Type:**

| Business Type | Lead Gen Gaps | Sales Gaps | Fulfillment Gaps |
|---------------|---------------|------------|------------------|
| **Coach** | Nurture between lead magnet and call | Follow-up after no-show/no-close | Results tracking, testimonial system |
| **Course Creator** | Webinar → checkout connection | Objection handling, cart abandonment | Post-purchase onboarding, completion tracking |
| **Agency** | Case study → discovery call path | Proposal follow-up system | Client offboarding, referral ask |
| **Creator** | Monetization path from audience | No formal sales process at all | Community management, engagement tracking |
| **Service Provider** | Lead capture from referrals | Written proposals, pricing structure | Results documentation, renewal system |

**By Funnel Phase:**

| Phase | Common Gaps |
|-------|-------------|
| **Traffic → Capture** | No clear CTA, no lead magnet, content doesn't point anywhere |
| **Capture → Nurture** | One-and-done welcome email, no sequence |
| **Nurture → Qualify** | No trigger to identify ready buyers, passive list |
| **Discovery → Presentation** | Jumps straight to pricing, no value demonstration |
| **Proposal → Close** | No follow-up sequence, ghosted prospects |
| **Close → Onboarding** | Gap between payment and first contact |
| **Delivery → Results** | No milestone tracking, no success metrics |
| **Results → Referral** | No systematic ask, relies on organic mentions |

### Don't Accept Surface-Level Answers

**LEAD GEN surface answers:**

**"I create content and post it"** → Probe:
- "What type of content? Where does it go?"
- "What's the CTA? How do they become a lead?"
- "How does someone go from content → contact → client?"

**"I have a lead magnet"** → Probe:
- "What happens after they download it?"
- "Is there a nurture sequence? How many emails?"
- "How do you know when someone's ready to buy?"

**SALES surface answers:**

**"I do sales calls"** → Probe:
- "How do calls get booked? What's the trigger?"
- "What prep happens before? How long is the call?"
- "What's your close rate? Where do you lose people?"
- "What happens after if they don't buy?"

**"People just buy from my website"** → Probe:
- "Is there a checkout page? Payment processor?"
- "Any objection handling or FAQ?"
- "What about cart abandonment? Follow-up?"
- "How do you know what made them buy?"

**"I send proposals"** → Probe:
- "What triggers a proposal? Discovery call?"
- "How do you present pricing? Options or single offer?"
- "What's your follow-up sequence if they don't respond?"
- "What's your proposal-to-close rate?"

**FULFILLMENT surface answers:**

**"I deliver coaching sessions"** → Probe:
- "What happens between payment and first session?"
- "Is there an intake form? Kickoff call?"
- "How do you track their progress?"
- "What happens when they finish?"

**"I have a course"** → Probe:
- "What's the onboarding experience?"
- "How do students get help if stuck?"
- "How do you know if they're completing it?"
- "How do you get testimonials?"

**"I send deliverables"** → Probe:
- "What's the kickoff process? Asset collection?"
- "How do clients give feedback? Revisions?"
- "What happens at project end? Handoff?"
- "How do you capture results and referrals?"

### CRITICAL: Question Flow

**WRONG (bundled questions):**
> "What are your products? And how much do you charge? And what are your expenses?"

**RIGHT (one focused question):**
> "What's your main product right now and its price?"
> *[wait for response]*
> "Got it. Any other products or offers?"
> *[wait for response]*
> "What are your rough monthly expenses - software, team, etc.?"

**WRONG (asking for goals directly):**
> "What are your top 3 goals?"

**RIGHT (inferring goals from pain):**
> "I noticed you mentioned content creation takes a lot of time. Is getting a system for that a priority?"

---

## Phase 1: Business Map (7 Columns)

### Opening

Say this to begin:

> "Let's map your business! I'll make some educated guesses based on what you tell me - just confirm or correct as we go.
>
> **What type of business do you run?**"

### Inference Pattern

After user describes their business:

1. **Identify archetype** from references/business-archetypes.md
2. **Present pre-filled guess:**

> "Based on what you've told me, here's my initial map:
>
> **Business Type:** [Coach/Course Creator/Agency/SaaS]
> **Likely Traffic Sources:** [YouTube, Instagram, LinkedIn]
> **Typical Funnel:** [Content → Lead Magnet → Email → Call → High-ticket]
> **Team Structure:** [Solo with 1 VA]
>
> How close am I? What should I adjust?"

3. **Iterate until confirmed** - adjust each element based on feedback

### The 7 Columns to Extract

| Column | What to Extract | Inference Approach |
|--------|-----------------|-------------------|
| **TRAFFIC** | All traffic sources | Infer from business type, confirm active vs planned |
| **CONVERTERS** | Landing pages, lead magnets | Infer from traffic, confirm what exists |
| **PRODUCTS** | All offers with pricing | Ask directly, calculate capacity |
| **FUNNELS** | Email sequences, sales flows | Infer from products, confirm mechanisms |
| **MATH** | Income + Expenses | Calculate from products/capacity, expenses optional |
| **TEAM** | Roles and capacity | Infer from operations described |
| **GOALS** | Performance Goals (actions that drive funnel) | INFER from traffic/products - what you DO to generate revenue |

### Column-by-Column Flow (ONE at a time)

**TRAFFIC** (infer, then confirm):
> "For a [business type], I'm guessing your main traffic is [YouTube/LinkedIn]. That right?"
> *[wait for yes/adjustment]*

**CONVERTERS** (infer from traffic):
> "So from [platform], people probably land on [your website/a lead magnet page]. Do you have a lead magnet?"
> *[wait for response]*

**PRODUCTS** (ask, but focused):
> "What's your main product right now?"
> *[wait]*
> "And the price?"
> *[wait]*
> "Any other products or is that the focus?"
> *[wait]*

**FUNNELS** (infer from converters):
> "Once someone downloads [lead magnet], I'm guessing they get a welcome email. Do you have any automated follow-up after that?"
> *[wait for response - if no, note as gap, move on]*

**MATH** (calculate, optional ask):
> "At $X with roughly Y sales/month, that's about $Z. Monthly expenses roughly?"
> *[wait - if user doesn't know, say "No worries, we can skip that"]*

**TEAM** (infer from everything):
> "Sounds like you're solo - is that right?"
> *[wait for confirmation]*

**GOALS** (INFER as Performance Goals - actions that drive the funnel):
> "To keep your funnel running, sounds like your key actions are: publish newsletter, post on YouTube, run discovery calls. That right?"
> *[wait - let user confirm or adjust]*

**Performance Goals = Actions that drive the funnel to generate revenue**

Examples by funnel stage:
- **Traffic:** "Post 2 YouTube videos/week", "Daily Substack newsletter"
- **Conversion:** "Run 4 discovery calls/week", "Send 2 proposals/week"
- **Delivery:** "Onboard 2 new clients/week", "Complete 4 coaching sessions/week"

**NOT Performance Goals (these are outcomes, not actions):**
- "Make $50K/month" - result of actions
- "Get 10 new clients" - depends on conversion
- "Grow to 10K subscribers" - outcome of content

### Pain Signal Detection

While gathering Business Map data, listen for these signals:

| Signal | What They Say | Flag For |
|--------|---------------|----------|
| Time complaints | "takes forever", "I spend hours on" | Bottleneck |
| Frustration | "so frustrating", "I hate doing" | Bottleneck |
| Inconsistency | "sometimes I forget", "it's random" | Needs System |
| Manual work | "I do it all myself", "no automation" | AI Opportunity |
| Missing pieces | "I don't have", "we really need" | Digital Asset Gap |

Note these for Phase 3.

### CHECKPOINT: Business Map

After all 7 columns extracted:

> "Here's your Business Map:
>
> [Generate ASCII preview or describe structure]
>
> Does this capture your business accurately? Any adjustments?"

**If Claude Code:** Generate .drawio file with Business Map page

**If Web/ChatGPT:** Output XML for copy-paste:
> "Copy this XML and paste it at app.diagrams.net:"

---

## Phase 2: Bow-Tie Funnel

### Inference from Business Map

Use Business Map data to infer the 7-stage funnel:

| Stage | Infer From | Example |
|-------|------------|---------|
| **Awareness** | TRAFFIC column | YouTube, Instagram, LinkedIn |
| **Nurturing** | CONVERTERS + FUNNELS | Lead magnet, email list |
| **Consideration** | FUNNELS | Application, webinar, DMs |
| **Commit** | PRODUCTS | Call → Payment |
| **Onboarding** | Fulfillment description | Intake form, kickoff |
| **Launch** | First delivery | First session, module access |
| **Results** | Ongoing + retention | Outcomes, testimonials, upsells |

### Present Inferred Funnel

> "Based on your Business Map, here's your customer journey:
>
> **ACQUISITION (narrowing)**
> - Awareness: [YouTube, Instagram]
> - Nurturing: [Free guide, Email list]
> - Consideration: [Application form, Discovery call]
>
> **COMMIT (the knot)**
> - Conversion: [Enrollment call → Payment]
>
> **DELIVERY (expanding)**
> - Onboarding: [Intake, Goals call]
> - Launch: [First session]
> - Results: [Transformation, Testimonial, Referral]
>
> How does this look? What's missing or wrong?"

### CHECKPOINT: Business Overview Complete

After user confirms Bow-Tie:

> "Great! Your Business Overview is complete - Bow-Tie Funnel + Business Map on one page.
>
> [Generate visual or output XML - both sections on Page 1]
>
> Now let's map out how things actually work..."

---

## Phase 3: Map Lead Generation Process (Level 1 - High-Level)

**Key principle:** Don't ask user to identify pain. Map the process together and pain surfaces naturally.

### What Lead Generation Actually IS

**Lead Generation is NOT just "content creation" or "distribution".**

Lead Generation is the complete system that turns strangers into qualified leads:

```
LEAD GENERATION FLOW (Level 1)
┌─────────────┬─────────────┬─────────────┬─────────────┐
│   TRAFFIC   │   CAPTURE   │   NURTURE   │  QUALIFY    │
│ Generation  │             │             │             │
├─────────────┼─────────────┼─────────────┼─────────────┤
│ How do      │ How do      │ How do      │ How do you  │
│ strangers   │ viewers     │ contacts    │ know when   │
│ find you?   │ become      │ become warm │ someone is  │
│             │ contacts?   │ leads?      │ ready to    │
│             │             │             │ buy?        │
├─────────────┼─────────────┼─────────────┼─────────────┤
│ YouTube     │ Lead magnet │ Email       │ Application │
│ Podcast     │ Newsletter  │ sequence    │ Call booked │
│ Social      │ Free trial  │ Content     │ Replied to  │
│ Referrals   │ Webinar     │ binging     │ sales email │
│ Ads         │ Booking     │ DM convos   │             │
└─────────────┴─────────────┴─────────────┴─────────────┘
                                                ↓
                                         To SALES Process
```

**Content Creation is a SUB-PROCESS within Traffic Generation** - it's how you CREATE content, not how the full lead gen system works.

When mapping Lead Gen, ensure ALL FOUR phases are represented:
1. **Traffic** - How do strangers discover you?
2. **Capture** - How do viewers become contacts?
3. **Nurture** - How do contacts become warm leads?
4. **Qualify** - How do you know when someone's ready?

**If any phase is missing, PROBE for it:**
> "You mentioned creating YouTube videos. That's traffic. But what happens when someone watches? How do they become a lead you can contact?"

---

### What Sales Actually IS

**Sales is NOT just "discovery calls".**

Sales is the complete system that turns qualified leads into paying customers:

```
SALES FLOW (Level 1)
┌─────────────┬─────────────┬─────────────┬─────────────┐
│  DISCOVERY  │ PRESENTATION│  PROPOSAL   │   CLOSE     │
├─────────────┼─────────────┼─────────────┼─────────────┤
│ Understand  │ Show the    │ Make the    │ Get         │
│ their needs │ solution    │ offer       │ commitment  │
├─────────────┼─────────────┼─────────────┼─────────────┤
│ Questions   │ Demo        │ Pricing     │ Contract    │
│ Pain points │ Case studies│ Options     │ Payment     │
│ Goals       │ Social proof│ Terms       │ Onboarding  │
│ Objections  │ Positioning │ Deadline    │ trigger     │
└─────────────┴─────────────┴─────────────┴─────────────┘
                                                ↓
                                         To FULFILLMENT
```

When mapping Sales, ensure ALL FOUR phases are represented:
1. **Discovery** - How do you understand their needs?
2. **Presentation** - How do you show them the solution?
3. **Proposal** - How do you make the offer?
4. **Close** - How do you get commitment?

---

### What Fulfillment Actually IS

**Fulfillment is NOT just "delivering the service".**

Fulfillment is the complete system that turns customers into successful outcomes and referrals:

```
FULFILLMENT FLOW (Level 1)
┌─────────────┬─────────────┬─────────────┬─────────────┐
│ ONBOARDING  │  DELIVERY   │   SUPPORT   │   RESULTS   │
├─────────────┼─────────────┼─────────────┼─────────────┤
│ Set up for  │ Provide the │ Handle      │ Capture     │
│ success     │ value       │ issues      │ outcomes    │
├─────────────┼─────────────┼─────────────┼─────────────┤
│ Welcome     │ Sessions    │ Check-ins   │ Testimonial │
│ Intake      │ Content     │ Q&A         │ Case study  │
│ Kickoff     │ Deliverables│ Troubleshoot│ Referral    │
│ Access      │ Milestones  │ Feedback    │ Renewal     │
└─────────────┴─────────────┴─────────────┴─────────────┘
                                                ↓
                                         Back to LEAD GEN (referrals)
```

When mapping Fulfillment, ensure ALL FOUR phases are represented:
1. **Onboarding** - How do new clients get started?
2. **Delivery** - How do you provide the value?
3. **Support** - How do you handle issues?
4. **Results** - How do you capture outcomes and referrals?

---

### 3-Level Progressive Drill-Down

| Level | Lanes | Shows | Tool Names? |
|-------|-------|-------|-------------|
| **Level 1: Process Flow** | Actor types (Owner \| AI \| Team \| Output) | WHAT phases happen, WHO owns each | No |
| **Level 2: System Detail** | Sub-systems or parallel workflows | WHICH systems handle each phase | No |
| **Level 3: Execution Detail** | Steps within each system | HOW each system works internally | Yes |

**Key differences:**
- **Level 1** = Actor swimlane (who does the work)
- **Level 2** = System/parallel swimlane (which systems handle it)
- **Level 3** = Execution swimlane (how each system works internally, with tools)

**Start at Level 1, drill into phases where pain surfaces.**

---

### Level 1: Process Flow Swimlane

**Lanes:** `Owner` | `AI` | `Team` | `Output`

Based on Business Map data, infer the COMPLETE process flow with actor lanes:

> "Based on what you told me, here's your Lead Generation flow - from stranger to qualified lead:
>
> **TRAFFIC → CAPTURE → NURTURE → QUALIFY**
>
> **LANES:**
> - Owner: Create Content → Review Applications
> - AI/System: Distribute → Capture (email signup) → Nurture Sequence → Qualify (engagement scoring)
> - Output: Qualified Lead → Ready for Sales Call
>
> Does this match your process? What's missing?"

**For diagram generation:** Use swimlane XML patterns from `references/drawio-standards.md`

**IMPORTANT:** Level 1 must show the COMPLETE journey, not just one activity:

| Phase | What to Map | Common Question |
|-------|-------------|-----------------|
| **Traffic** | How strangers discover you | "Where does your content go?" |
| **Capture** | How viewers become contacts | "What's the CTA? How do they join your list?" |
| **Nurture** | How contacts become warm | "What happens after they sign up?" |
| **Qualify** | How you know they're ready | "How do you know when to reach out?" |

**Common Level 1 Lead Gen patterns by business:**

| Business Type | Traffic | Capture | Nurture | Qualify |
|---------------|---------|---------|---------|---------|
| **Coach** | YouTube, LinkedIn | Free guide, Webinar | Email sequence | Application/Call booked |
| **Course Creator** | YouTube, Podcast | Free mini-course | Email + content binge | Webinar attended |
| **Agency** | Referrals, Case studies | Free audit offer | Case study sequence | Discovery call booked |
| **Creator** | Social, Newsletter | Email signup | Regular content | Engaged subscriber |

**What to ask at Level 1:**
- "Who owns each of these steps - you, a system, or someone else?"
- "Which step feels like it takes the most time or causes delays?"
- **"Is anything missing here? How does someone actually go from seeing your content to becoming a lead you can contact?"**

*Listen for signals to know where to drill down*

---

### Level 1 Sales Process Mapping

When mapping the Sales Process, ensure ALL FOUR phases are represented:

**Common Level 1 Sales patterns by business:**

| Business Type | Discovery | Presentation | Proposal | Close |
|---------------|-----------|--------------|----------|-------|
| **Coach** | Triage call, application review | Strategy session, case studies | Package options, investment | Verbal yes → payment link |
| **Course Creator** | Webinar Q&A, DM convos | Webinar content, success stories | Checkout page, bonus stack | Scarcity/urgency → buy now |
| **Agency** | Discovery call, audit | Proposal presentation, portfolio | Custom quote, scope doc | Contract → deposit |
| **Service Provider** | Consultation, needs assessment | Service overview, testimonials | Quote, package options | Agreement → invoice |

**Phase-by-phase mapping questions for Sales:**

| Phase | What to Map | Questions to Ask |
|-------|-------------|------------------|
| **Discovery** | How you understand their needs | "What happens on a sales call? What questions do you ask? How long?" |
| **Presentation** | How you show the solution | "Do you do a demo? Share case studies? Walk through a proposal deck?" |
| **Proposal** | How you make the offer | "When do you present pricing? Options or single offer? Written proposal?" |
| **Close** | How you get commitment | "What's the actual conversion moment? Payment link? Contract?" |

**Probing for Sales gaps:**
- "What happens if they don't buy on the call?"
- "Do you have a follow-up sequence?"
- "How do you handle objections?"
- "What's your close rate? Where do you lose people?"

**If any phase is missing, PROBE for it:**
> "You mentioned doing discovery calls. But what happens after - do you present a formal proposal or is pricing discussed on the same call?"

---

### Level 1 Fulfillment/Delivery Mapping

When mapping Fulfillment, ensure ALL FOUR phases are represented:

**Common Level 1 Fulfillment patterns by business:**

| Business Type | Onboarding | Delivery | Support | Results |
|---------------|------------|----------|---------|---------|
| **Coach** | Welcome email, intake form, kickoff call | Weekly sessions, Voxer access | Check-ins, SOS calls | Progress tracking, testimonial request |
| **Course Creator** | Welcome sequence, platform access, orientation | Module releases, live calls, community | Q&A, office hours, troubleshooting | Completion certificate, case study interview |
| **Agency** | Kickoff call, asset collection, project plan | Deliverables, revisions, progress updates | Slack channel, weekly syncs | Final handoff, results report, referral ask |
| **Service Provider** | Agreement, access setup, expectations call | Monthly deliverables, reports | Email support, issue resolution | Review, renewal discussion, testimonial |

**Phase-by-phase mapping questions for Fulfillment:**

| Phase | What to Map | Questions to Ask |
|-------|-------------|------------------|
| **Onboarding** | How clients get started | "What happens right after someone pays? First 48 hours? First week?" |
| **Delivery** | How you provide the value | "What's the actual experience? Sessions? Content? Deliverables? Timeline?" |
| **Support** | How you handle issues | "How do clients reach you with questions? Response time? Emergency access?" |
| **Results** | How you capture outcomes | "How do you know when they've succeeded? Testimonial process? Referral ask?" |

**Probing for Fulfillment gaps:**
- "What's the experience like between when they pay and their first session?"
- "How do you handle a client who's struggling or not engaging?"
- "What happens when someone finishes - is there a graduation/exit process?"
- "How do you systematically capture testimonials and referrals?"

**If any phase is missing, PROBE for it:**
> "You mentioned coaching sessions every week. But what about onboarding - what happens between payment and that first session? Is there an intake form? Kickoff call?"

---

### Level 1 Client Onboarding Mapping (Sub-section of Fulfillment)

Sometimes users want to drill specifically into Onboarding. Expand to show:

**Common Onboarding sub-phases:**

| Sub-Phase | Purpose | Examples |
|-----------|---------|----------|
| **Welcome** | Confirm purchase, set expectations | Welcome email, celebration message, what's next |
| **Intake** | Gather info needed to serve them | Intake form, questionnaire, asset collection |
| **Setup** | Get them access and oriented | Portal access, community invite, tool setup |
| **Kickoff** | Align on goals and start work | Kickoff call, goal setting, first milestone |

**Onboarding questions:**
- "Walk me through the first 48 hours after someone pays"
- "What information do you need from them before you can start?"
- "How do you set expectations about what's coming?"
- "When is the first 'real' interaction after purchase?"

---

### CHECKPOINT: Level 1 Complete

> "Here's your process flow. I noticed [Nurture Sequence] is all automated but [Discovery Call] prep is all you - want to drill into that and see the systems involved?"

**After confirmation:** If user wants to drill down → proceed to Level 2 for that step

---

### Level 2: System Detail Swimlane

**Lanes:** The sub-systems or parallel workflows that execute the phase (lanes change based on what you're drilling into)

Drill into ONE phase to show the systems that handle it:

> "Let's break down [Discovery Call Prep] to see the systems involved:
>
> **LANES (sub-systems):**
> - Calendar System
> - CRM System
> - Prep Workflow
>
> These should run before each call. Which one causes delays or gets skipped?"

**For diagram generation:** Use swimlane XML patterns from `references/drawio-standards.md`

**What to ask at Level 2:**
- "What systems handle this phase?"
- "Do these run in parallel or sequence?"
- "Which system causes the most delays?"
- "What are the inputs and outputs?"

**Level 2 does NOT include tool names** - that's Level 3.

### CHECKPOINT: Level 2 Complete

> "Now I can see the systems involved in [Discovery Call Prep]. The Prep Workflow seems to be where things get stuck.
>
> Want to drill into that system to see the actual steps and tools?"

**After confirmation:** If complex system → proceed to Level 3. Otherwise → annotation pass.

---

### Level 3: Execution Detail Swimlane (Case-by-Case)

**When to use:** Only when a specific system in Level 2 is complex enough to warrant detailed step breakdown. Not every system needs Level 3.

**Lanes:** Steps within the system (sequential or parallel execution)

Drill into ONE system to show execution steps with tool names:

> "Let's see exactly how [Prep Workflow] works:
>
> **STEPS:**
> - Pull Lead Info (HubSpot) → Generate Questions (Claude) → Review Notes (Notion) → Ready for Call
>
> This takes about 15 minutes. Which step is the bottleneck?"

**For diagram generation:** Use swimlane XML patterns from `references/drawio-standards.md`

**Level 3 includes:**
- Specific tool names (Claude, Notion, Zapier, ConvertKit, etc.)
- Step-by-step execution order
- Time estimates per step
- Inputs/outputs for each step
- Bottleneck annotations

### CHECKPOINT: Level 3 Complete

> "Now I can see exactly how [Prep Workflow] executes. [Generate Questions] is manual and takes 10 minutes - that's the bottleneck.
>
> Ready to annotate and look at options?"

**After confirmation:** Proceed to annotation pass (→ `expand-process.md`)

---

## Pain Discovery (Not Pain Declaration)

**WRONG approach:**
> "What's your biggest bottleneck?"
> "Where do you struggle most?"

**RIGHT approach:** Pain surfaces naturally during mapping:

| What They Say During Mapping | What It Reveals |
|------------------------------|-----------------|
| "I do all of that myself" | 🔴 Bottleneck - no delegation |
| "That takes forever" | 🔴 Bottleneck - time sink |
| "I should do that but don't" | 🟠 Gap - missing step |
| "We use [tool] for that" | 🟢 Already optimized |
| "My VA handles that" | 🟢 Already delegated |
| "I don't have that" | 🟣 Digital asset needed |

**After mapping, Claude observes:**
> "I noticed a few things while we mapped this out:
> - You're doing [X] and [Y] yourself - those seem like time sinks
> - [Z] could probably be automated
> - You mentioned not having [Asset] - that might help
>
> Want to annotate these on the diagram and look at options?"

---

## Decision Point

After Lead Generation swimlane is complete and annotated:

> "Your Lead Generation page is done. You have:
> - The process mapped out
> - [X] bottlenecks flagged
> - [Y] automation opportunities identified
>
> **What's next?**
>
> A) **Map another area** - Sales Process or Fulfillment
> B) **Generate roadmap** - Prioritized action plan from what we found
> C) **Stop here** - Take what we have and start fixing"

**Based on choice:**
- **Map another:** Loop back to Phase 3 for next area
- **Roadmap:** → `generate-roadmap.md`
- **Stop:** Output current .drawio + resume block

---

## Cross-Platform Mode

### Claude Code (File Access)

- Generate .drawio files directly
- Save progress state to file
- Show file path to user

### Claude Web / ChatGPT (No File Access)

- Output XML in code blocks
- Instruct user to copy → paste at app.diagrams.net
- Output Resume Block for session continuity

---

## Resume Format

At end of session, output this block:

```yaml
# Business X-Ray Progress - Copy this to resume later
stage: [current_stage]
business_type: [type]
business_map_complete: [true/false]
bowtie_complete: [true/false]
pain_points: [list]
selected_process: [process or null]
expanded_processes: []
pending: [list]
opportunities_flagged: 0
last_updated: [date]
```

### Resume Instructions

> "To continue this session later:
> 1. Copy the progress block above
> 2. Start a new session and paste it
> 3. Also upload your .drawio file if you have one
> 4. Say 'continue my Business X-Ray'
>
> I'll pick up exactly where we left off."

---

## Drill-Down Questions

When user mentions vague activities, always drill:

### "I create content"
- "What type of content specifically?"
- "What tools do you use?"
- "How long does each piece take?"
- "Who else is involved?"

### "I do sales calls"
- "How do people book?"
- "What prep do you do?"
- "What happens after?"
- "Who handles follow-ups?"

### "I deliver the service"
- "Walk me through the customer experience"
- "What's manual vs automated?"
- "How do you handle communication?"

### "I do admin stuff"
- "What specific tasks?"
- "How often?"
- "What tools?"
- "Could any be automated?"

---

## Data Output Format

After interview, structure data for diagram generation:

### Business Map Data

```markdown
## TRAFFIC
| Source | Status | Notes |
|--------|--------|-------|
| [Source] | Active/Planned | [details] |

## CONVERTERS
| Converter | Type | Status |
|-----------|------|--------|
| [Name] | Landing/Lead Magnet | Active/Missing |

## PRODUCTS
| Product | Price | Capacity | $/Month |
|---------|-------|----------|---------|
| [Name] | $X | X | $X |

## FUNNELS
| Funnel | Type | Status |
|--------|------|--------|
| [Name] | Nurture/Sales | Active/Missing |

## MATH
### Income: $X/month
### Expenses: $X/month
### Net Profit: $X/month

## TEAM
| Role | Who |
|------|-----|
| Owner | [Name] |
| VA | [Name/None] |

## GOALS (Performance Goals - inputs within control)
1. [Action-based goal - e.g., "Publish daily newsletter"]
2. [Action-based goal - e.g., "Post 2 YouTube videos/week"]
3. [Action-based goal - e.g., "Run 4 discovery calls/week"]
```

### Pain Points Summary

```markdown
## Bottlenecks Detected
- [Process]: [Signal heard]

## AI Opportunities
- [Process]: [Why automatable]

## Digital Asset Gaps
- [Asset needed]: [Purpose]
```

---

## Next Workflow

After Phase 3 (Lead Generation mapped):
- **If mapping another area:** Loop back to Phase 3 pattern for Sales or Fulfillment
- **If ready for roadmap:** → `generate-roadmap.md`
- **If stopping:** Output current .drawio + resume block

**For deeper sub-process expansion** (e.g., drilling into Content Creation within Lead Generation):
→ `expand-process.md` handles adding sub-process swimlanes below the main process on the same page
