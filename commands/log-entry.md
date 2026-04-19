---
description: Record a dated entry in the current personal-planning workspace. Works across all variants (diary, health, family, house-search, preparedness, therapy, personal-dev, inbox-hygiene).
---

# /personal-planning:log-entry

Append a new dated entry into the active workspace.

## Procedure

1. **Detect variant**: Read the workspace `CLAUDE.md` to determine the variant (diary / health-wellness / family-planning / house-search / preparedness / therapy-tracking / personal-dev / inbox-hygiene). Use that to pick the target folder:
   - `diary` → `entries/`
   - `health-wellness` → `log/`
   - `family-planning` → `family-meetings/` or `milestones/` (ask if ambiguous)
   - `house-search` → `viewings/` or `listings/` (ask)
   - `preparedness` → `input/`
   - `therapy-tracking` → `therapy-sessions/`
   - `personal-dev` → `progress/`
   - `inbox-hygiene` → `inputs/` (email artefacts)

2. **Collect content**: If `$ARGUMENTS` is empty, ask the user for the entry body. Otherwise treat `$ARGUMENTS` as free text.

3. **Write file**: Name it `YYMMDD-<short-slug>.md` with a short front-matter block (`date`, `variant`, optional `tags`) then the body.

4. **Log cross-reference**: If `logs/` exists, append a one-liner (date + filename + summary) to `logs/entries.md`.

5. **Report**: Print the file path and next suggested step (e.g. `/personal-planning:review-progress`).
