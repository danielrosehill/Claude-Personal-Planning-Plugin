---
name: new-workspace
description: Provision a new personal-planning workspace on disk. Use when the user wants to start a new personal-planning workspace — diary, health tracking, family planning, house search, preparedness, personal-dev, or inbox hygiene. Accepts a workspace name and variant. Scaffolds the workspace, personalises CLAUDE.md from the user's global memory, and (by default) creates a GitHub repo. (For therapy tracking, use the dedicated `therapy-tracking` plugin.)
disable-model-invocation: true
allowed-tools: Bash(mkdir *), Bash(cp *), Bash(cat *), Bash(git init *), Bash(git add *), Bash(git commit *), Bash(gh repo create *), Bash(gh auth status), Bash(git push *), Read
---

# Provision Personal-Planning Workspace

Creates a new workspace for a personal-planning use case. This plugin's commands (`/personal-planning:log-entry`, `/personal-planning:review-progress`, `/personal-planning:set-goal`) are globally available once installed — this skill only provisions the **data scaffold** (CLAUDE.md, entries/, goals/, logs/, etc.) those commands read from and write to.

## Arguments

`$ARGUMENTS` is parsed as:

- **First positional**: workspace name (kebab-case, used as directory and GitHub repo name). Required.
- **Second positional** (optional): target parent path. Defaults to `~/repos/github/my-repos`.
- **`--variant=<diary|health-wellness|family-planning|house-search|preparedness|personal-dev|inbox-hygiene>`** (optional): which scaffold to copy. Default: `diary`. (For `therapy-tracking`, use the dedicated `therapy-tracking` plugin instead.)
- **`--local-only`** (optional): skip GitHub repo creation and push. Default: create a public GitHub repo and push.
- **`--private`** (optional): create the GitHub repo as private. Default: public.

### Examples

```
/personal-planning:new-workspace my-diary
/personal-planning:new-workspace health-log --variant=health-wellness --private
/personal-planning:new-workspace flat-search --variant=house-search
/personal-planning:new-workspace go-bag --variant=preparedness
/personal-planning:new-workspace inbox-rules --variant=inbox-hygiene
```

## Procedure

### 1. Parse arguments

Extract workspace name, target parent path, variant, and flags from `$ARGUMENTS`. If workspace name is missing, ask the user for it before proceeding.

### 2. Resolve the scaffold path

The bundled scaffold lives at `${CLAUDE_SKILL_DIR}/../../template/<variant>/`. Confirm it exists. If the variant isn't one of the listed options, tell the user which variants are available.

### 3. Read ambient facts

Read `~/.claude/CLAUDE.md` if it exists. Extract OS, locale, timezone, and user identity facts. These will personalise the workspace's CLAUDE.md at step 6.

### 4. Create the workspace directory

```bash
mkdir -p <target-parent>/<workspace-name>
cp -r ${CLAUDE_SKILL_DIR}/../../template/<variant>/. <target-parent>/<workspace-name>/
```

Do **not** copy any `.claude/` tree. The plugin's primitives are global.

### 5. Personalise CLAUDE.md

Open the new workspace's `CLAUDE.md` and:

- Replace any placeholder identity with the facts from step 3.
- Add a short header noting the workspace name and variant.
- If ambient facts include OS/locale/timezone, embed them so downstream commands can skip re-asking.

### 6. Prompt for workspace-specific facts

Ask the user only for facts this plugin can't infer — variant-dependent:

- **diary**: preferred cadence (daily / weekly).
- **health-wellness**: broad focus areas (sleep, diet, exercise, conditions).
- **family-planning**: who this covers (self, partner, children count).
- **house-search**: target city/area and budget range.
- **preparedness**: region and household size.
- **personal-dev**: top-level goals or skill areas.
- **inbox-hygiene**: email account being triaged.

Write facts into `CLAUDE.md` under a `Workspace Facts` section.

### 7. Initialise git and (optionally) publish

```bash
cd <target-parent>/<workspace-name>
git init
git add .
git commit -m "Initial workspace from personal-planning plugin"
```

Unless `--local-only` is set:

```bash
gh repo create <workspace-name> --<public|private> --source=. --push
```

Use `--public` by default, `--private` if flag was passed. For health-wellness and inbox-hygiene variants, remind the user that private is usually more appropriate if they chose public.

### 8. Print next steps

Tell the user:

- Workspace path.
- Variant chosen.
- Which plugin commands apply (`/personal-planning:log-entry`, `/personal-planning:review-progress`, `/personal-planning:set-goal`).
- Reminder that the workspace is **data** — they can delete/move it freely without losing the plugin's commands.

## Notes

- Resolve the scaffold path via `${CLAUDE_SKILL_DIR}/../../template/<variant>` (not `${CLAUDE_PLUGIN_ROOT}` — not exported in skill bash injection).
- Never copy `.claude/commands/`, `.claude/agents/`, or `.claude/skills/` into the new workspace.
- Do not hard-code any personal paths or identifiers — everything comes from user memory or prompts.
