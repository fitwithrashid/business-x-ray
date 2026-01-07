# Business X-Ray

This repository contains the Business X-Ray skill for mapping and optimizing business operations.

## Skill Location

The main skill is at: `.claude/skills/business-x-ray/SKILL.md`

## How to Use

When user says "business x-ray", "map my business", or wants to visualize their operations:

1. Load the skill: `read .claude/skills/business-x-ray/SKILL.md`
2. Follow the workflow routing in SKILL.md
3. Generate diagrams as XML for user to paste into diagrams.net

## Diagram Output

All diagrams should be saved to the `diagrams/` folder in .drawio format.

Users can sync diagrams with GitHub via: diagrams.net → File → Save to → GitHub

## Cross-Platform Mode

This skill works in:
- **Claude Code CLI** - Generates .drawio files directly
- **Claude Web App** - Outputs XML for copy-paste to diagrams.net
