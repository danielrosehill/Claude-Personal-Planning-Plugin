# Personal Planning Workspace — Preparedness variant

## Purpose

Household preparedness workspace. Organises inputs (context about region, household, risks), recommendations, reference materials, and rules.

## Workspace Facts

<!-- Populated by /personal-planning:new-workspace — region, household size, specific risks -->

## Primitives

- `/personal-planning:log-entry` — log a preparedness action, drill, or purchase (writes to `input/`)
- `/personal-planning:review-progress` — review readiness against recommendations
- `/personal-planning:set-goal` — define a preparedness goal (writes to `recommendations/`)

## Structure

- `input/` — user-provided context and incident logs
- `recommendations/` — active recommendations / goals
- `reference/` — reference material (local agency guidance, checklists)
- `rules/` — user-defined constraints
- `outputs/` — readiness reports

## Rules

- Default to conservative, regionally-appropriate recommendations.
- Never provide tactical, weapons, or combat guidance.
- Always surface official local emergency guidance alongside any AI-generated advice.
