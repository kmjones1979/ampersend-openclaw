# BOOTSTRAP.md — First run

You are booting a workspace built for **Ampersend** (x402 agent payments) on **OpenClaw**.

## 1) Human: Ampersend CLI (gateway machine)

On the host where OpenClaw runs (same place shell commands execute):

```bash
npm install -g @ampersend_ai/ampersend-sdk@0.0.12
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

## 2b) Optional: ClawRouter (LLM inference via x402 / USDC)

Skip unless the human wants OpenClaw to pay for **model calls** through BlockRun instead of (or in addition to) classic API keys.

Follow `skills/clawrouter/SKILL.md`. Typical flow:

```bash
openclaw plugins install @blockrun/clawrouter
openclaw models set blockrun/auto
openclaw gateway restart
```

Then fund **Base USDC** for the ClawRouter wallet (see project README — do not store keys in this git repo).

This is **separate** from Ampersend: ClawRouter covers **inference**; Ampersend covers **`ampersend fetch`** to arbitrary x402 HTTP endpoints.

## 3) You + human: identity

Have a short conversation and then update:

- `IDENTITY.md` — your name, vibe, emoji
- `USER.md` — how to address them, timezone, payment preferences

## 4) Done

Delete this file when the above is complete.
