# OpenClaw Engineering Solver Workspace

This package is a workspace-first starter for OpenClaw.

It is designed to match the official workspace and skills model:
- bootstrap files such as `AGENTS.md`, `SOUL.md`, `TOOLS.md`, `USER.md`, `IDENTITY.md`, `HEARTBEAT.md`, and `BOOTSTRAP.md` live in the workspace,
- workspace skills live under `<workspace>/skills`,
- each skill is a directory with a `SKILL.md` containing YAML frontmatter and Markdown instructions.

## Suggested install
1. Choose a workspace location, commonly `~/.openclaw/workspace`.
2. Copy this package into that workspace, or into a dedicated workspace root.
3. If you manage bootstrap files yourself, enable `agents.defaults.skipBootstrap` in your OpenClaw config so onboarding does not overwrite them.
4. Start a new problem by copying `problems/_template` to a new problem id.

## What is included
- workspace bootstrap files
- six skills
- a reusable problem template

## What is intentionally not included
- a full `openclaw.json`

OpenClaw configuration evolves, so this package stays on the safe side: it gives you a conforming workspace layout and skills pack without hardcoding unverified runtime config keys.
