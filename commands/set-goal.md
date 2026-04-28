---
description: Create or update a goal in the current personal-planning workspace. Variant-aware target folder.
---

# /personal-planning:set-goal

Create a new goal or update an existing one.

## Procedure

1. **Detect variant** from workspace `CLAUDE.md`.

2. **Resolve goals folder**:
   - Default: `goals/`
   - `house-search`: `search-criteria/`
   - `preparedness`: `recommendations/`
   - `inbox-hygiene`: `rules/` (filter goals)

3. **Collect**: From `$ARGUMENTS` or by asking, gather:
   - Goal title (kebab-case slug)
   - Description / success criteria
   - Target date (optional)
   - Review cadence (weekly / monthly / ad-hoc)
   - Linked entries (optional)

4. **Write or update**: If a file with the slug exists, propose a diff and confirm before overwriting. Otherwise create `<goals-folder>/<slug>.md` with structured front-matter plus narrative.

5. **Cross-link**: Append a one-liner in `logs/goals.md` (create if missing).

6. **Next step**: Suggest `/personal-planning:review-progress` to see how it fits against existing goals.
