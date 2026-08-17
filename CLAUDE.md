# bc-bdi

Agent notes for developing this plugin. The product context, credential contract, and terminology the agent needs at work time live in `skills/boomi-bdi/SKILL.md` — load it before modifying the skill.

## Layout

- `skills/boomi-bdi/` — the shipped skill: `SKILL.md` plus `scripts/` (bash CLI tools over the BDI REST API).
- `.claude-plugin/plugin.json` — plugin manifest.

## Conventions

- Scripts are bash-only with no third-party dependencies; every script supports `--help`.
- API calls go through the `bdi_api` helper in `skills/boomi-bdi/scripts/bdi-common.sh`. It feeds auth to curl on stdin (`-K -`) to keep the token out of process arguments, so stdin is reserved — never `@-`, `-T -`, or piping into the wrapper. Inline `-d` and `--data-binary @file` are both fine.
- Presigned URLs are credentials: the signature is in the query string, so they go via the curl config rather than argv — see `fetch_presigned` in `bdi-logicode.sh`.