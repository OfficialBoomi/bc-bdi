# bc-bdi

Agent notes for developing this plugin. The product context, credential contract, and terminology the agent needs at work time live in `skills/boomi-bdi/SKILL.md` — load it before modifying the skill.

## Layout

- `skills/boomi-bdi/` — the shipped skill: `SKILL.md` plus `scripts/` (bash CLI tools over the BDI REST API).
- `.claude-plugin/plugin.json` — plugin manifest.

## Conventions

- Scripts are bash-only with no third-party dependencies; every script supports `--help`.