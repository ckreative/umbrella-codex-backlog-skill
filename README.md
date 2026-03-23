# Umbrella Codex Backlog Skill

Portable Codex skill package for operating the Umbrella engineering backlog.

If you are sending this repo to a teammate, send them this install command:

```bash
python ~/.codex/skills/.system/skill-installer/scripts/install-skill-from-github.py \
  --url https://github.com/ckreative/umbrella-codex-backlog-skill/tree/main/umbrella-codex-backlog-skill
```

After install, restart Codex.

## What It Does

Gives Codex full knowledge of the Umbrella backlog system:

- Write operations — create epics, tickets, tags; assign work; transition status; log work
- Read operations — query the backlog, sync views, blocked tickets, workload summaries
- Tag taxonomy — platform tags (`mobile`, `desktop`, `cross-platform`, `backend`, `ai`) and domain tags (`domain-navigation`, `domain-workspaces`, `domain-org-identity`, `domain-invites`, `domain-project-creation`, `domain-call-sheet-read`, `domain-call-sheet-create`, `domain-document-automation`, `domain-ai-requirements`, `domain-onboarding`)
- Team workflows — intake roadmap work, run product-engineering sync, slice by tags

## What You Can Ask

- "Show me the current backlog"
- "List tickets in epic W2-E10"
- "What's blocked?"
- "Show mobile platform work"
- "Create a ticket for..."
- "Assign ticket CS-01 to alex"
- "What did alex work on last week?"

This repo intentionally contains only the installable skill payload:

```text
umbrella-codex-backlog-skill/
├── SKILL.md
├── agents/openai.yaml
└── references/backlog-surface.md
```

## Install

Use this exact command:

```bash
python ~/.codex/skills/.system/skill-installer/scripts/install-skill-from-github.py \
  --url https://github.com/ckreative/umbrella-codex-backlog-skill/tree/main/umbrella-codex-backlog-skill
```

Why the folder URL instead of just the repo URL?

Because the installer needs the path to the actual skill folder. In this repo, the installable skill lives in:

`umbrella-codex-backlog-skill/`

After install, restart Codex.

## What This Skill Assumes

This skill is meant to be used while working inside the Umbrella backlog project workspace, where these commands exist:

- `bash scripts/db/migrate.sh`
- `bash scripts/db/import_wave2_spec.sh`
- `bash scripts/db/test.sh`
- `bash scripts/db/psql.sh`

The skill does not bundle the Umbrella database project itself. It only bundles the Codex skill that knows how to operate that project.
