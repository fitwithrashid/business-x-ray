# Business X-Ray Workshop

**Duration:** 90 minutes
**Format:** Live walkthrough + hands-on mapping

---

## Pre-Workshop Checklist (For You)

- [ ] Test the full flow on a fresh GitHub account
- [ ] Have backup instructions ready if Codespaces is slow
- [ ] Prepare a sample business to demo (your own or fictional)
- [ ] Have diagrams.net open in a tab for showing final output

---

## Workshop Flow

### Part 1: Setup (15 minutes)

**Goal:** Everyone has Claude Code running in Codespaces

#### Step 1: GitHub Account (2 min)
- Go to [github.com/signup](https://github.com/signup)
- Create free account (or sign in if they have one)

#### Step 2: Fork the Repo (2 min)
- Share your repo link: `github.com/the2hourclo/business-x-ray`
- Click **"Fork"** button (top right)
- Click **"Create fork"**
- They now have their own copy

#### Step 3: Open Codespaces (3 min)
- On THEIR fork, click green **"Code"** button
- Select **"Codespaces"** tab
- Click **"Create codespace on master"**
- Wait for it to load (~1 minute)

#### Step 4: Install Claude Code Extension (3 min)
- Click **Extensions** icon (left sidebar)
- Search **"Claude Code"**
- Click **Install**
- Click **"Sign in"** and connect Claude account

#### Step 5: Verify It Works (5 min)
- In Claude Code chat, type: `Let's do a business x-ray`
- Claude should respond with the first question
- **Troubleshooting:** If skill not found, they may need to reload the window

---

### Part 2: Live Demo (20 minutes)

**Goal:** Show the complete flow so they know what to expect

You run through the X-Ray on YOUR business (or a sample):

1. **Business Map extraction** (5 min)
   - Show inference-first approach ("You're a coach, so I'm guessing...")
   - Point out the 7 columns
   - Show the generated diagram

2. **Bow-Tie Funnel** (5 min)
   - Walk through customer journey stages
   - Show how activities stack in columns
   - Preview the visual output

3. **Process drill-down** (5 min)
   - Pick one process to expand
   - Show swimlane with actor lanes
   - Point out annotations (bottleneck, automate, etc.)

4. **Saving to diagrams.net** (5 min)
   - Open [diagrams.net](https://app.diagrams.net)
   - File → Open from → GitHub
   - Show the diagram renders correctly

---

### Part 3: Hands-On Mapping (45 minutes)

**Goal:** Everyone maps their own business

#### Structure:
- They work at their own pace
- You walk around / monitor chat for questions
- Checkpoint at 20 min mark: "Who has their Business Map done?"

#### Common Questions:

**"Claude stopped responding"**
- Check if they hit a token limit
- Have them start a new chat and say "Continue my business x-ray"

**"The diagram looks wrong"**
- This is iterative - they can say "Fix the layout" or "Regenerate"
- Remind them: the map is a living document

**"I don't know my conversion rates"**
- That's fine - leave blank or estimate
- The goal is structure, not perfection

**"How do I save my progress?"**
- Claude provides a YAML block they can copy
- Paste it in a new chat to resume

---

### Part 4: Wrap-Up (10 minutes)

#### Show: How to Get Updates
1. Go to their fork on GitHub
2. Click **"Sync fork"** → **"Update branch"**
3. Next Codespaces session will have latest version

#### Reassure: Your Diagrams Are Safe
- Their `diagrams/[business-name]-x-ray.drawio` files are THEIRS
- Sync Fork only updates skill files, not their unique diagrams
- **Pro tip:** Name diagrams `[your-business-name]-x-ray.drawio` to avoid any chance of collision

#### Next Steps:
- Continue mapping on their own
- Drill down into problem processes
- Join the community (if you have one)

---

## Troubleshooting Guide

| Problem | Solution |
|---------|----------|
| Codespace won't load | Wait 2 min, refresh. If still stuck, try "Stop codespace" and restart |
| Claude Code not finding skill | Reload window (Ctrl+Shift+P → "Reload Window") |
| Diagram XML looks like gibberish | Copy the XML, paste into diagrams.net → Arrange → Insert → Advanced → XML |
| Hit Claude token limit | Start new chat, paste YAML progress block, say "Continue" |
| Fork sync shows conflicts | They edited a skill file - discard their changes or resolve manually |

---

## Post-Workshop

Send follow-up with:
- [ ] Link to their fork (remind them it's at `github.com/THEIR-USERNAME/business-x-ray`)
- [ ] Quick reference for Sync Fork updates
- [ ] Link to diagrams.net for editing
- [ ] Your contact for questions

---

## Workshop Customization

### For Shorter Sessions (60 min)
- Skip Part 2 (Live Demo) - go straight to hands-on
- Have them map ONLY the Business Map + Bow-Tie
- Save process drill-down for homework

### For Longer Sessions (2+ hours)
- Add: Everyone drills down one process
- Add: Group share - 2-3 people show their maps
- Add: Roadmap generation for identified bottlenecks

### For Virtual Workshops
- Use Zoom breakout rooms for small group help
- Have a shared doc for common questions
- Record your demo for async reference

---

*Workshop template for Business X-Ray skill*
*Last updated: 2025-01-07*
