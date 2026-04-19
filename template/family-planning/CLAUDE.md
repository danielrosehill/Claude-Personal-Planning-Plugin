# Personal Planning Workspace — Family Planning variant

## Purpose

Family / parenting planning workspace — meetings, milestones, schedules, decisions.

## Workspace Facts

<!-- Populated by /personal-planning:new-workspace — who this workspace covers -->

## Primitives

- `/personal-planning:log-entry` — log a family meeting, milestone, or decision
- `/personal-planning:review-progress` — review recent entries against goals
- `/personal-planning:set-goal` — define a family goal (education, routines, etc.)

## Structure

- `family-meetings/` — minutes and action items from family meetings
- `milestones/` — child / family milestones
- `schedules/` — recurring routines and calendars
- `decisions/` — decision logs (major choices + rationale)
- `goals/` — active family goals
- `outputs/` — reviews

## Rules

- Treat names and ages of children as sensitive — prefer role-based references.
- Keep decisions reversible unless the user signals otherwise.
