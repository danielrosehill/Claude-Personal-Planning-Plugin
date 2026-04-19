# Personal Planning Workspace — House Search variant

## Purpose

House / apartment search workspace. Tracks listings, viewings, comparables, mortgage options, and legal notes.

## Workspace Facts

<!-- Populated by /personal-planning:new-workspace — city/area, budget, bedrooms, hard requirements -->

## Primitives

- `/personal-planning:log-entry` — log a viewing, agent call, or listing note (resolves to `viewings/` or `listings/`)
- `/personal-planning:review-progress` — review the search funnel against criteria
- `/personal-planning:set-goal` — update search criteria (writes to `search-criteria/` — optional override)

## Structure

- `listings/` — candidate properties
- `viewings/` — viewing notes
- `comparables/` — comparable sale/rent data
- `mortgage/` — mortgage options and calculators
- `legal/` — legal checks and documents
- `areas/` — neighbourhood research
- `goals/` — search criteria
- `outputs/` — shortlist reports and weekly reviews

## Rules

- Never make an offer or legal commitment on the user's behalf.
- Preserve listing URLs and source dates — prices move.
