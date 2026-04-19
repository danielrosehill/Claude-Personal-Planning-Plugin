# Personal Planning Workspace — Inbox Hygiene variant

## Purpose

Analyse deceptive unsolicited email that evades traditional spam filters. Extract tracking artefacts, build a reusable filter ruleset, and log sender blocks. Inspired by the Spam Warrior pattern.

## Workspace Facts

<!-- Populated by /personal-planning:new-workspace — email account being triaged -->

## Primitives

- `/personal-planning:log-entry` — drop an email artefact / analysis into `inputs/`
- `/personal-planning:review-progress` — review how rules are performing
- `/personal-planning:set-goal` — create or update a filter rule (writes to `rules/`)

## Structure

- `inputs/` — `.eml` files and raw email artefacts
- `data/` — processed email log (JSON with sender, score, reasoning)
- `rules/` — filter rules and blocklists
- `goals/` — targets (e.g. "zero scraped-list outreach per week")
- `outputs/` — weekly / monthly reviews

## Rules

- Reason about *intent* not just headers — the signal is in the ask + tracking, not in keywords.
- Never auto-block without surfacing the rationale to the user first.
- Keep the blocklist human-readable so it can be re-used in any provider.
