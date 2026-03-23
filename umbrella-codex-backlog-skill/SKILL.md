---
name: umbrella-codex-backlog-skill
description: Use when operating the Umbrella engineering backlog for team-scale planning and execution. Covers creating epics and tickets, importing roadmap specs, tagging by platform or domain, reporting by developer or epic, and preparing product-engineering sync views.
---

# Umbrella Codex Backlog Skill

Use this skill when the team is managing shared delivery work in the Umbrella backlog system.

## Quick start

All scripts run from the repo root. Use relative paths.

Core commands:
- `bash scripts/db/migrate.sh`
- `bash scripts/db/import_wave2_spec.sh`
- `bash scripts/db/test.sh`
- `bash scripts/db/psql.sh`

Primary write functions:
- `backlog.create_epic(...)`
- `backlog.create_ticket(...)`
- `backlog.create_tag(...)`
- `backlog.add_ticket_tag(...)`
- `backlog.assign_ticket(...)`
- `backlog.transition_ticket(...)`
- `backlog.log_work(...)`

Primary reporting views:
- `backlog.current_backlog_v`
- `backlog.product_sync_v`
- `backlog.member_current_work_v`
- `backlog.member_weekly_activity_v`
- `backlog.blocked_tickets_v`
- `backlog.workload_summary_v`

Read [references/backlog-surface.md](references/backlog-surface.md) when you need the stable SQL interface, tag taxonomy, or common query patterns.

## Team workflows

### Intake roadmap work

1. Create or find the target epic.
2. Create tickets as feature-sized work items unless the source spec already defines the right granularity.
3. Prefer `ready` for implementation-ready backlog work and `intake` for loosely captured ideas.
4. Tag tickets with both platform and domain slices when possible.

### Run product and engineering sync

Start from `backlog.product_sync_v` for the overall backlog state, then use:
- `backlog.blocked_tickets_v` for risks
- `backlog.member_current_work_v` for active assignments
- `backlog.member_weekly_activity_v` for “what changed last week”

### Slice the backlog

Use tags to answer planning questions quickly:
- Platform tags: `mobile`, `desktop`, `cross-platform`, `backend`, `ai`
- Domain tags: `domain-navigation`, `domain-workspaces`, `domain-org-identity`, `domain-invites`, `domain-project-creation`, `domain-call-sheet-read`, `domain-call-sheet-create`, `domain-document-automation`, `domain-ai-requirements`, `domain-onboarding`

## Guidance

- Preserve external ticket keys when importing a structured spec if they are already meaningful.
- Prefer stable repo scripts and SQL functions over ad hoc schema edits.
- Keep the backlog easy to query: one clear epic, feature-sized tickets, explicit tags, and current status.
- When asked to share this skill, point teammates at the GitHub path containing `umbrella-codex-backlog-skill` and have them install from that path.
