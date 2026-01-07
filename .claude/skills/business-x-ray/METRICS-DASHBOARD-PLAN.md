# Metrics Dashboard - Implementation Plan

**Goal:** Create a live dashboard in draw.io that AI can update weekly with real business metrics.

**Status:** PLANNING

---

## The Vision

A metrics dashboard page in the Business X-Ray .drawio file that:
1. Shows key funnel metrics (impressions, subscribers, applications, enrollments, etc.)
2. Can be **programmatically updated** by AI on a weekly basis
3. Shows **trends** (up/down arrows, % change)
4. Visually indicates **health** (green = good, yellow = warning, red = problem)

---

## Technical Challenges

### Challenge 1: Data Source
**Question:** Where do the metrics come from?

**Options:**
| Option | Pros | Cons |
|--------|------|------|
| A. Manual input | Simple, works anywhere | User has to provide data each week |
| B. Notion database | Structured, queryable | Requires Notion setup |
| C. Google Sheets | Familiar, easy API | Another tool to manage |
| D. CSV file | Simple, portable | Manual updates |
| E. API integrations | Real-time data | Complex, per-platform setup |

**Recommendation:** Start with **Option A (Manual input)** or **Option B (Notion database)**. User provides metrics weekly, AI updates the diagram.

---

### Challenge 2: Draw.io XML Modification
**Question:** How do we update specific values in the XML?

**Approach:**
1. Use **predictable IDs** for metric cells (e.g., `metric-impressions-value`, `metric-subscribers-value`)
2. Create a **Python script** that:
   - Reads the .drawio XML
   - Finds cells by ID
   - Updates the `value` attribute
   - Saves the file

**Example XML cell to update:**
```xml
<mxCell id="metric-impressions-value" value="12,450" style="..." />
```

**Script updates to:**
```xml
<mxCell id="metric-impressions-value" value="15,200 (+22%)" style="..." />
```

---

### Challenge 3: Trend Indicators
**Question:** How do we show week-over-week trends?

**Design:**
| Trend | Display | Color |
|-------|---------|-------|
| Up > 10% | ↑↑ +22% | Green (#2e7d32) |
| Up 1-10% | ↑ +5% | Light Green (#4caf50) |
| Flat ±1% | → 0% | Gray (#757575) |
| Down 1-10% | ↓ -5% | Orange (#ff9800) |
| Down > 10% | ↓↓ -22% | Red (#c62828) |

**Implementation:**
- Store previous week's value
- Calculate % change
- Update both value AND style (color)

---

### Challenge 4: Historical Data
**Question:** How do we track week-over-week changes?

**Options:**
| Option | Approach |
|--------|----------|
| A. JSON file | Store `metrics-history.json` alongside .drawio |
| B. Notion database | Store weekly snapshots in a database |
| C. Within the diagram | Add a "history" section with past 4 weeks |

**Recommendation:** **Option A (JSON file)** - Simple, portable, works offline.

```json
{
  "business_name": "Online Coaching Business",
  "metrics": {
    "impressions": {
      "current": 15200,
      "previous": 12450,
      "history": [10200, 11500, 12450, 15200]
    },
    "email_subs": {
      "current": 2340,
      "previous": 2180,
      "history": [1900, 2050, 2180, 2340]
    }
  },
  "last_updated": "2026-01-02"
}
```

---

## Proposed Architecture

```
┌─────────────────────────────────────────────────────────────────┐
│                    METRICS UPDATE WORKFLOW                       │
├─────────────────────────────────────────────────────────────────┤
│                                                                  │
│  1. User provides weekly metrics                                 │
│     └─> "This week: 15,200 impressions, 2,340 subs, 12 apps"    │
│                                                                  │
│  2. AI parses the metrics                                        │
│     └─> Extracts: impressions=15200, email_subs=2340, apps=12   │
│                                                                  │
│  3. AI reads metrics-history.json                                │
│     └─> Gets previous values and calculates trends              │
│                                                                  │
│  4. AI updates the .drawio file                                  │
│     └─> Python script modifies XML cells by ID                  │
│     └─> Updates values AND colors based on trend                │
│                                                                  │
│  5. AI updates metrics-history.json                              │
│     └─> Shifts history, adds new values                         │
│                                                                  │
│  6. User opens .drawio to see updated dashboard                  │
│                                                                  │
└─────────────────────────────────────────────────────────────────┘
```

---

## Dashboard Layout Design

```
┌──────────────────────────────────────────────────────────────────────────┐
│                     📊 BUSINESS METRICS DASHBOARD                         │
│                     Week of January 2, 2026                               │
├──────────────────────────────────────────────────────────────────────────┤
│                                                                           │
│  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐      │
│  │ IMPRESSIONS │  │ EMAIL SUBS  │  │ APPLICATIONS│  │ ENROLLMENTS │      │
│  │             │  │             │  │             │  │             │      │
│  │   15,200    │  │    2,340    │  │      12     │  │      3      │      │
│  │  ↑↑ +22%    │  │   ↑ +7%    │  │   ↓ -8%    │  │   → 0%     │      │
│  └─────────────┘  └─────────────┘  └─────────────┘  └─────────────┘      │
│                                                                           │
│  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐      │
│  │ ONBOARD %   │  │ TIME TO WIN │  │ COMPLETE %  │  │    LTV      │      │
│  │             │  │             │  │             │  │             │      │
│  │    92%      │  │   3 days    │  │    85%      │  │   $2,450    │      │
│  │   ↑ +4%     │  │  ↓↓ -25%   │  │   ↑ +10%   │  │   ↑ +8%    │      │
│  └─────────────┘  └─────────────┘  └─────────────┘  └─────────────┘      │
│                                                                           │
│  ┌───────────────────────────────────────────────────────────────────┐   │
│  │                        4-WEEK TREND                                │   │
│  │  Impressions: 10.2K → 11.5K → 12.4K → 15.2K  ████████████▓▓▓▓    │   │
│  │  Email Subs:  1.9K →  2.0K →  2.2K →  2.3K   ██████████████▓▓    │   │
│  │  Enrollments:    2 →     3 →     3 →     3   ██████████████──    │   │
│  └───────────────────────────────────────────────────────────────────┘   │
│                                                                           │
└──────────────────────────────────────────────────────────────────────────┘
```

---

## Implementation Steps

### Phase 1: Dashboard Template (Week 1)
- [ ] Create dashboard page layout in draw.io
- [ ] Define metric cell IDs (predictable naming)
- [ ] Add to Business X-Ray multi-page file
- [ ] Document XML structure for updates

### Phase 2: Update Script (Week 1-2)
- [ ] Create `update_dashboard.py` script
- [ ] Parse user-provided metrics
- [ ] Read/write .drawio XML
- [ ] Update cell values by ID
- [ ] Update colors based on trend

### Phase 3: History Tracking (Week 2)
- [ ] Create `metrics-history.json` schema
- [ ] Calculate week-over-week changes
- [ ] Store historical data
- [ ] Generate trend indicators

### Phase 4: Workflow Integration (Week 2)
- [ ] Create `workflows/update-dashboard.md`
- [ ] Define user input format
- [ ] Add to Business X-Ray skill

### Phase 5: Enhancement (Future)
- [ ] Add mini sparkline charts (if draw.io supports)
- [ ] Add Notion database integration
- [ ] Add automated data pull from APIs

---

## Files to Create

```
.claude/skills/business-x-ray/
├── workflows/
│   └── update-dashboard.md       # Workflow for weekly updates
├── scripts/
│   └── update_dashboard.py       # Python script for XML modification
└── templates/
    └── metrics-history.json      # Template for history tracking
```

---

## Questions to Resolve

1. **What metrics should we track?**
   - Funnel metrics (impressions, subs, apps, enrollments)?
   - Delivery metrics (onboarding %, completion %, LTV)?
   - Custom metrics per business?

2. **How often should updates happen?**
   - Weekly (recommended)?
   - Daily?
   - On-demand?

3. **Should we integrate with external data sources?**
   - Start simple (manual input)
   - Add integrations later (YouTube Analytics, ConvertKit, Stripe, etc.)

4. **Where does the .drawio file live?**
   - Local file only?
   - Synced to cloud (Google Drive, Dropbox)?
   - This affects how AI can access and update it

---

## Next Steps

1. **Get user feedback** on this plan
2. **Decide on MVP scope** (start with manual input, 7 core metrics)
3. **Create the dashboard template** in draw.io
4. **Write the Python update script**
5. **Test the full workflow**

---

**Note:** This is a complex feature that involves:
- Draw.io XML manipulation
- Data persistence (JSON)
- Trend calculation
- Color-coded status indicators

We should build incrementally and test each component.
