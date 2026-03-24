# OpenClaw workspace: ampersend (x402 agent payments)

Template workspace for [OpenClaw](https://docs.openclaw.ai/concepts/agent-workspace) with:

- **[ampersend](https://www.ampersend.ai/)** — `skills/ampersend/SKILL.md` (source: [ampersend.ai/SKILL.md](https://www.ampersend.ai/SKILL.md)) for **agent-governed x402 HTTP** (`ampersend fetch`) within **user-defined spend limits**.

## What you get

- OpenClaw bootstrap files: `AGENTS.md`, `SOUL.md`, `USER.md`, `IDENTITY.md`, `TOOLS.md`, `HEARTBEAT.md`, `BOOTSTRAP.md`, `memory/`
- Workspace skill **`ampersend`** with OpenClaw metadata `requires.bins: ["ampersend"]`
- Agent instructions wired to prefer `--inspect` before spend and to follow ampersend’s security rules (no dashboard login on assistant-controlled browsers)

## Prerequisites

1. **OpenClaw** installed and a gateway running where you want this workspace.
2. **Node/npm** on that same host to install the ampersend CLI globally.
3. An **ampersend** account / approval flow completed by the **human** (the agent must not drive dashboard login in a browser it controls).

## Install this workspace

1. Clone this repository (or copy the files) to the machine that runs the OpenClaw gateway.
2. Point OpenClaw at this folder as the agent workspace, e.g. set `agents.defaults.workspace` in `~/.openclaw/openclaw.json` to this path. See [Agent workspace](https://docs.openclaw.ai/concepts/agent-workspace).
3. Run `openclaw setup` (or your usual flow) if you need missing files seeded; this repo already includes the standard set.

## Install ampersend CLI (pinned)

```bash
npm install -g @ampersend_ai/ampersend-sdk@0.0.12
ampersend --version
```

## Configure ampersend (human-in-the-loop)

Follow `skills/ampersend/SKILL.md`. Short version:

```bash
ampersend setup start --name "my-openclaw-agent"
# Human opens user_approve_url in THEIR browser.

ampersend setup finish
ampersend config status
```

Optional limits (example: 1 USDC/day in atomic units):

```bash
ampersend setup start --name "my-openclaw-agent" --daily-limit "1000000" --auto-topup
```

## Day-to-day usage

- **Probe price/requirements:** `ampersend fetch --inspect <url>`
- **Paid request:** `ampersend fetch <url>` (and POST variants per the skill)
- **Config:** `ampersend config status` and `ampersend config set ...` as documented in the skill

All CLI output is JSON; check `"ok": true` before treating a run as success.

## Customization for real use cases

Pinata’s template guidance: ship a **use case**, not only a skill.

1. Add rows to the “Paid APIs” table in `TOOLS.md` (real x402 endpoints your agent will call).
2. Extend `AGENTS.md` with your workflow (e.g. “every morning, `--inspect` then fetch …”).
3. Add cron/heartbeat tasks in OpenClaw if you need schedules; keep `HEARTBEAT.md` small.

## Pinata / partner checklist

1. Remove secrets, tokens, and personal data from all files and from chat logs before publishing.
2. Tag a **GitHub release** when a version is ready.
3. Notify Pinata with the repo URL and release tag.

## License

Add a `LICENSE` file for your org before public release if needed. Skill text is descriptive documentation; comply with ampersend’s terms when using their CLI and APIs.
