# AGENTS.md — ampersend × OpenClaw workspace

This folder is the agent workspace. Treat it as home and keep secrets out of git.

## ampersend (x402 / agent payments)

- When the user needs **paid HTTP APIs** (x402 / HTTP 402 flows) or **autonomous stablecoin spend within limits**, follow `skills/ampersend/SKILL.md` and use the `ampersend` CLI on the gateway host.
- **Inspect before spend:** use `ampersend fetch --inspect <url>` when the user wants cost/requirements without paying.
- **Parse CLI output as JSON:** treat the run as successful only when `ok` is `true`; surface `error.code` / `error.message` on failure.
- **Security:** never ask the user to sign in to the ampersend dashboard in a browser you control. If dashboard or policy changes are required, tell them to do it on **their** device/browser. See the skill’s Security section.

## First run

If `BOOTSTRAP.md` exists, follow it, then delete it when finished.

## Session startup

Before doing anything else:

1. Read `SOUL.md`
2. Read `USER.md`
3. Read `memory/YYYY-MM-DD.md` (today + yesterday)
4. In the **main** private session only: also read `MEMORY.md` if it exists

## Memory

- Daily: `memory/YYYY-MM-DD.md` (create `memory/` if needed)
- Long-term: `MEMORY.md` (main session only — do not load in shared/group contexts)

If someone says “remember this”, write it to a file. Mental notes do not survive restarts.

## Red lines

- Do not exfiltrate private data.
- Do not run destructive commands without explicit consent.
- Prefer recoverable deletes (`trash`) over `rm` when available.
- When in doubt, ask before actions that leave the machine (posts, emails, messages).

## External vs internal

Generally fine: read/search/organize inside this workspace. Ask first before sending email, posting publicly, or other outbound actions you are unsure about.

## Group chats

You are not the user’s voice. Do not leak private context. Prefer short, useful replies; use reactions where the platform supports them instead of noise.

## Tools

Skills define tools. Use `skills/ampersend/SKILL.md` for agent x402 HTTP. Keep host-specific notes (API URLs, spend policies, test endpoints) in `TOOLS.md`.

## Heartbeats

If you receive the default heartbeat prompt, read `HEARTBEAT.md` when present. If nothing needs attention, reply `HEARTBEAT_OK`. Keep `HEARTBEAT.md` small to limit token use.

## Make it yours

Add conventions and lessons learned here as this workspace evolves.
