# personal-planning-plugin

Claude Code plugin for personal life planning — ships `log-entry`, `review-progress`, and `set-goal` primitives plus a provisioning skill that scaffolds a workspace for any of seven variants.

> **Note:** Therapy tracking has been broken out into its own dedicated plugin: [Therapy-Tracking-Plugin](https://github.com/danielrosehill/Therapy-Tracking-Plugin).

Part of the [danielrosehill Claude Code marketplace](https://github.com/danielrosehill/Claude-Code-Plugins).

## What you get

### Primitives (always available once the plugin is installed)

- `/personal-planning:log-entry` — append a dated entry to the current workspace (variant-aware target folder)
- `/personal-planning:review-progress` — summarise recent entries and progress against goals
- `/personal-planning:set-goal` — create or update a goal

### Agent

- `personal-planner` — autonomous planner for multi-step workspace work

### Provisioning skill

- `/personal-planning:new-workspace <name> [--variant=<variant>] [--local-only] [--private]`

Scaffolds a new workspace (CLAUDE.md + variant-appropriate folder tree), personalises it from `~/.claude/CLAUDE.md`, and (by default) creates a public GitHub repo for it.

## Variants

| Variant | Use case |
|---|---|
| `diary` (default) | Personal journaling |
| `health-wellness` | Non-clinical health tracking |
| `family-planning` | Parenting, family meetings, milestones |
| `house-search` | House / apartment search funnel |
| `preparedness` | Household preparedness |
| `personal-dev` | Skills, habits, learning goals |
| `inbox-hygiene` | Deceptive-email analysis + filter building |

## Pattern

Primitives live in the plugin → globally available from any cwd.
Workspace scaffolds are provisioned as **data** → no `.claude/` tree inside provisioned workspaces.
Plugin updates never touch your workspace data.

See [PLAN.md in Claude-Workspace-Reshaping-190426](https://github.com/danielrosehill/Claude-Workspace-Reshaping-190426) for the full pattern spec.

## Install

Via the danielrosehill marketplace:

```
/plugin marketplace add danielrosehill/Claude-Code-Plugins
/plugin install personal-planning
```

## License

MIT.
