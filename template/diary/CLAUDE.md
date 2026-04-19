# Personal Planning Workspace — Diary variant

## Purpose

Structured diary / journaling workspace. Entries live in `entries/`, goals in `goals/`, cross-reference logs in `logs/`, reviews in `outputs/`.

## Workspace Facts

<!-- Populated by /personal-planning:new-workspace -->

## Primitives (provided by the personal-planning plugin)

- `/personal-planning:log-entry` — append a dated entry
- `/personal-planning:review-progress` — summarise recent entries + goals
- `/personal-planning:set-goal` — create/update goals

## Conventions

- Entry filenames: `YYMMDD-<slug>.md` with front-matter (`date`, `tags`).
- Dates: DD/MM/YY in prose; YYMMDD in filenames.
- Keep entries raw and honest — summarisation happens in `outputs/`.

## What NOT to do

- Do not publish or share entries without the user's explicit request.
- Do not auto-edit past entries; append corrections as new entries.
