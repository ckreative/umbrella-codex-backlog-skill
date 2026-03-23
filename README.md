# Codex Skills

Portable Codex skill package for operating the Umbrella engineering backlog.

This repo intentionally contains only the installable skill payload:

```text
codex-skills/
├── SKILL.md
├── agents/openai.yaml
└── references/backlog-surface.md
```

## Install

```bash
python ~/.codex/skills/.system/skill-installer/scripts/install-skill-from-github.py \
  --url https://github.com/<owner>/<repo>/tree/main/codex-skills
```

After install, restart Codex.

## What This Skill Assumes

This skill is meant to be used while working inside the Umbrella backlog project workspace, where these commands exist:

- `bash scripts/db/migrate.sh`
- `bash scripts/db/import_wave2_spec.sh`
- `bash scripts/db/test.sh`
- `bash scripts/db/psql.sh`

The skill does not bundle the Umbrella database project itself. It only bundles the Codex skill that knows how to operate that project.

