# Personal Planning Workspace — Health & Wellness variant

## Purpose

Personal health tracking workspace — organise logs, reference materials, and goals. **Not medical advice.** Claude organises information you provide; it does not diagnose, treat, or prescribe.

## Workspace Facts

<!-- Populated by /personal-planning:new-workspace — focus areas (sleep/diet/exercise/conditions) -->

## Primitives

- `/personal-planning:log-entry` — log a health event, symptom, or observation (written to `log/`)
- `/personal-planning:review-progress` — roll up recent log entries against goals
- `/personal-planning:set-goal` — define a tracked goal (e.g. hydration, sleep window)

## Structure

- `log/` — dated health log entries
- `goals/` — active wellness goals
- `reference/` — user-provided reference material (test results, clinician notes)
- `prompts/` — custom prompts for review runs
- `outputs/` — generated reviews and summaries

## Rules

- Never offer a diagnosis or clinical recommendation.
- Always encourage the user to raise concerning findings with a qualified clinician.
- Keep this workspace private by default.
