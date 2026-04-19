# Personal Planning Workspace — Therapy Tracking variant

## Purpose

Private workspace to prepare for and reflect on therapy sessions. **Not therapy.** Claude organises information; it does not diagnose, counsel, or replace a clinician.

Also supports the *I'm Not Okay* pattern: turn voice-memo transcripts into structured problem summaries to share with a therapist.

## Workspace Facts

<!-- Populated by /personal-planning:new-workspace — modality, cadence -->

## Primitives

- `/personal-planning:log-entry` — log a session or inter-session reflection (writes to `therapy-sessions/`)
- `/personal-planning:review-progress` — review progress against therapy goals (reads `goal-tracking/`)
- `/personal-planning:set-goal` — set or update a therapy goal (writes to `goal-tracking/`)

## Structure

- `therapy-sessions/` — pre/post session notes
- `goal-tracking/` — tracked goals and progress markers
- `prompts/` — reusable prompts (e.g. structure a voice-memo transcript)
- `archive/` — older entries
- `outputs/` — reviews and summaries

## Rules

- Never offer a diagnosis or clinical recommendation. Organise only.
- Keep this workspace private. The provisioning skill will suggest `--private` by default.
- When processing voice-memo transcripts: transcribe, edit for readability, extract discrete stressors, categorise — never interpret feelings for the user.
