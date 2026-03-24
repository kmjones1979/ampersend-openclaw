# TOOLS.md — Local notes for skills

Skills describe *how* tools work. This file is for **your** environment: names, URLs, policies, and reminders.

## ampersend

- CLI install: see `skills/ampersend/SKILL.md` (pinned version).
- After setup: `ampersend config status` should show a ready agent.
- Optional staging API: `ampersend config set --api-url https://api.staging.ampersend.ai` (revert with `--clear-api-url`).

### Paid APIs you use

List x402 or paid endpoints here so future sessions know what to `fetch` or `--inspect`:

| Name | Base URL | Notes |
| ---- | -------- | ----- |
|      |          |       |

### Spend policy (human-defined)

- Default: use `--inspect` first unless the user explicitly asks to pay immediately.
- Per-task or daily caps the human cares about:

## ClawRouter (optional)

Only if the human installed the plugin and uses `blockrun/*` models — see `skills/clawrouter/SKILL.md` and [edgeandnode/ClawRouter](https://github.com/edgeandnode/ClawRouter).

- Routing profile in use: (e.g. `blockrun/auto`, `blockrun/eco`, pinned model)
- Base USDC funding notes: (where they buy/send; rough budget — no keys here)
- Proxy / env overrides: `BLOCKRUN_PROXY_PORT`, `CLAWROUTER_DISABLED`, etc. if non-default

**Reminder:** inference is paid through ClawRouter’s wallet flow; **other** x402 APIs still go through **ampersend** unless the human standardizes differently.

---

Add cameras, SSH hosts, TTS voices, or anything else your skills need, same as any OpenClaw workspace.
