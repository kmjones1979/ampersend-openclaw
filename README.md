# OpenClaw workspace: ampersend (x402 agent payments)

Pinata-style layout: repo root has **`manifest.json`** + this README; the OpenClaw home is **`workspace/`** (see [PinataCloud/agent-template](https://github.com/PinataCloud/agent-template)).

- **[ampersend](https://www.ampersend.ai/)** — `workspace/skills/ampersend/SKILL.md` (source: [ampersend.ai/SKILL.md](https://www.ampersend.ai/SKILL.md)) for **agent-governed x402 HTTP** (`ampersend fetch`) within **user-defined spend limits**.

## Layout

```
manifest.json          # Pinata Agents config (remove _docs before marketplace)
README.md
workspace/
  AGENTS.md SOUL.md USER.md IDENTITY.md TOOLS.md HEARTBEAT.md BOOTSTRAP.md
  memory/
  skills/ampersend/SKILL.md
```

## What you get

- **`manifest.json`**: `scripts.build` installs the pinned ampersend CLI; optional cron task (disabled) for `ampersend config status`.
- Workspace skill **`ampersend`** with `requires.bins: ["ampersend"]`.
- Instructions to prefer `--inspect` before spend and ampersend dashboard security rules.

## OpenClaw

Point `agents.defaults.workspace` at **`…/workspace`** (this repo’s `workspace` folder), not the repo root. See [Agent workspace](https://docs.openclaw.ai/concepts/agent-workspace).

## ampersend CLI

```bash
npm install -g @ampersend_ai/ampersend-sdk@0.0.14
ampersend --version
```

Setup (human approves in **their** browser):

```bash
ampersend setup start --name "my-openclaw-agent"
ampersend setup finish
ampersend config status
```

Details: `workspace/skills/ampersend/SKILL.md`.

## Pinata

1. Import repo in Pinata Agents; edit `manifest.json` `agent` / `template` for your listing.
2. Remove the **`_docs`** key from `manifest.json` before marketplace submit.
3. Tag releases when versions are ready.

## License

Add a `LICENSE` if you publish publicly; comply with ampersend terms for CLI/APIs.
