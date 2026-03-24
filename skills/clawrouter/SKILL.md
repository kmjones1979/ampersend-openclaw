---
name: clawrouter
description: Smart LLM router — routes OpenClaw model requests and pays for inference via x402 (USDC). Optional; install when the human wants BlockRun-powered routing instead of traditional API keys.
homepage: https://github.com/edgeandnode/ClawRouter
metadata: { "openclaw": { "emoji": "🦀", "requires": { "config": ["models.providers.blockrun"] } } }
---

# ClawRouter (optional)

[ClawRouter](https://github.com/edgeandnode/ClawRouter) is the agent-native LLM router for OpenClaw: local routing across many models with **per-request x402 / USDC** payment (non-custodial wallet flow described in the project README). Upstream also publishes under [BlockRunAI/ClawRouter](https://github.com/BlockRunAI/ClawRouter).

This workspace also includes **ampersend** (`skills/ampersend/SKILL.md`). Those concerns split naturally:

| Piece | What it pays for |
| ----- | ---------------- |
| **ClawRouter** (plugin) | **OpenClaw LLM inference** routed through BlockRun / `blockrun/*` models |
| **ampersend** (`ampersend fetch`) | **Arbitrary HTTP** x402 endpoints (APIs, tools) under agent spend limits |

The human may enable **one, both, or neither**. Do not assume ClawRouter is installed unless `models.providers.blockrun` is configured or the user says they use BlockRun routing.

## Install

```bash
openclaw plugins install @blockrun/clawrouter
```

Alternative installer from the project docs (then restart gateway):

```bash
curl -fsSL https://blockrun.ai/ClawRouter-update | bash
openclaw gateway restart
```

## Setup

```bash
# Smart routing (auto-picks a capable cheap model per request)
openclaw models set blockrun/auto

# Or pin a specific model
openclaw models set openai/gpt-4o
```

Chat shortcuts (when supported): `/model auto`, `/model eco`, `/model premium`, `/wallet`, `/stats` — see the [ClawRouter README](https://github.com/edgeandnode/ClawRouter).

## Funding inference

Per ClawRouter documentation: fund the **Base** USDC balance for the wallet the plugin uses (often auto-generated under `~/.openclaw/blockrun/`). This is **separate** from ampersend agent keys; the human funds each path they enable.

## How routing works (summary)

ClawRouter classifies requests into tiers (simple / medium / complex / reasoning) and picks a cost-effective model. See the repo for the full model table and pricing.

## Troubleshooting

```bash
npx @blockrun/clawrouter doctor
```

## Example output

```
[ClawRouter] google/gemini-2.5-flash (SIMPLE, rules, confidence=0.92)
             Cost: $0.0025 | Baseline: $0.308 | Saved: 99.2%
```
