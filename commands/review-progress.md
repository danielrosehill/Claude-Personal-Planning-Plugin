---
description: Summarise recent entries and progress toward goals in the current personal-planning workspace. Variant-aware.
---

# /personal-planning:review-progress

Produce a concise progress review across recent entries, goals, and logs.

## Procedure

1. **Detect variant** from `CLAUDE.md` in the workspace.

2. **Gather inputs**:
   - Read the most recent 10 entries from the variant's entry folder.
   - Read all files in `goals/` (or `search-criteria/` for house-search, `recommendations/` for preparedness).
   - Read the last few `logs/` entries if present.

3. **Analyse**:
   - For each active goal, classify status: on-track / slipping / stalled / achieved.
   - Identify recurring themes in recent entries.
   - Flag anything the user mentioned twice but never acted on.

4. **Write review**: Save to `outputs/review-YYMMDD.md` with sections:
   - Goals snapshot (table)
   - Themes from recent entries
   - Suggested next actions
   - Open questions for the user

5. **Present**: Show the review inline and ask if the user wants to update any goals (`/personal-planning:set-goal`).
