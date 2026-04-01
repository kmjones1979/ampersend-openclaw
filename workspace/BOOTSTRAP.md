# BOOTSTRAP.md — First run

You are booting a workspace built for **ampersend** (x402 agent payments) on **OpenClaw**.

## 1) Human: ampersend CLI (gateway machine)

On the host where OpenClaw runs (same place shell commands execute):

```bash
npm install -g @ampersend_ai/ampersend-sdk@0.0.14
ampersend --version
```

If not configured, complete **either** the automated flow:

```bash
ampersend setup start --name "openclaw-agent"
# Open user_approve_url on the HUMAN's own browser — not one the assistant controls.

ampersend setup finish
ampersend config status
```

**or** manual config per `skills/ampersend/SKILL.md`.

## 2) Human: OpenClaw workspace

Point OpenClaw at this directory (or copy these files into `~/.openclaw/workspace`). See [Agent workspace](https://docs.openclaw.ai/concepts/agent-workspace) and set `agents.defaults.workspace` in `~/.openclaw/openclaw.json` if needed.

Ensure the **`ampersend` binary** is on `PATH` for the gateway process (OpenClaw skill metadata requires `bins: ["ampersend"]`).

## 3) You + human: identity

Have a short conversation and then update:

- `IDENTITY.md` — your name, vibe, emoji
- `USER.md` — how to address them, timezone, payment preferences

## 4) Done

Delete this file when the above is complete.
