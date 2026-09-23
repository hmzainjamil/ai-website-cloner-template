# ai-website-cloner-template

> **Clone any website, your way** - Universal AI agent template (works in Claude Code, Cursor, Aider, Continue, Cline, Codex, Amazon Q, Augment) that clones any public website into editable HTML/Tailwind in minutes.

<p align="center"><a href="https://github.com/hmzainjamil/ai-website-cloner-template">Repository</a> · <a href="https://github.com/hmzainjamil/ai-website-cloner-template/commits/main">Commits</a> · <a href="https://github.com/hmzainjamil/ai-website-cloner-template/issues">Issues</a></p>
<p align="center"><img alt="Documentation" src="https://img.shields.io/badge/documentation-deep%20editorial-lightgrey"> <img alt="Lifecycle" src="https://img.shields.io/badge/lifecycle-active-success"></p>

<!-- HMZ DEEP README v1 -->

## At a glance

| Field | Current state |
|---|---|
| Repository | ai-website-cloner-template |
| Visibility | Public |
| Lifecycle | Active |
| Evidence basis | Current repository documentation and source-visible material |

## Why this exists

**Clone any website, your way** - Universal AI agent template (works in Claude Code, Cursor, Aider, Continue, Cline, Codex, Amazon Q, Augment) that clones any public website into editable HTML/Tailwind in minutes.

The README documents the cloning workflow while separating source inspection, generated implementation, and the behavior of the resulting site.

## CONCEPTS

| Concept | Location | Description |
|---|---|---|
| **Claude skill** | `.claude/skills/clone-website/SKILL.md` | Claude Code clone-website skill - [Source](https://github.com/hmzainjamil/ai-website-cloner-template/blob/main/.claude/skills/clone-website/SKILL.md) |
| **Cursor command** | `.cursor/commands/clone-website.md` | Cursor sibling command - [Source](https://github.com/hmzainjamil/ai-website-cloner-template/blob/main/.cursor/commands/clone-website.md) |
| **Aider config** | `.aider.conf.yml` | Aider runtime config - [Source](https://github.com/hmzainjamil/ai-website-cloner-template/blob/main/.aider.conf.yml) |
| **Codex skill** | `.codex/skills/clone-website/SKILL.md` | OpenAI Codex skill mirror - [Source](https://github.com/hmzainjamil/ai-website-cloner-template/blob/main/.codex/skills/clone-website/SKILL.md) |
| **Amazon Q agent** | `.amazonq/cli-agents/clone-website.json` | Amazon Q CLI agent definition - [Source](https://github.com/hmzainjamil/ai-website-cloner-template/blob/main/.amazonq/cli-agents/clone-website.json) |
| **Augment command** | `.augment/commands/clone-website.md` | Augment command sibling - [Source](https://github.com/hmzainjamil/ai-website-cloner-template/blob/main/.augment/commands/clone-website.md) |
| **Continue command** | `.continue/commands/clone-website.md` | Continue command sibling - [Source](https://github.com/hmzainjamil/ai-website-cloner-template/blob/main/.continue/commands/clone-website.md) |
| **Cline rules** | `.clinerules` | Cline rules file - [Source](https://github.com/hmzainjamil/ai-website-cloner-template/blob/main/.clinerules) |
| **Amazon Q project rules** | `.amazonq/rules/project.md` | Amazon Q project rules - [Source](https://github.com/hmzainjamil/ai-website-cloner-template/blob/main/.amazonq/rules/project.md) |
| **Continue rules** | `.continue/rules/project.md` | Continue project rules - [Source](https://github.com/hmzainjamil/ai-website-cloner-template/blob/main/.continue/rules/project.md) |

## HOW IT WORKS

```
+---------------------------------------------------------+
|                       INPUT                             |
|   Claude Code . Cursor . Aider . Continue . Cline . |
+--------------------------+------------------------------+
                           v
+---------------------------------------------------------+
|                  ORIENT / PARSE                         |
|   - Validate inputs                                     |
|   - Load skill / agent / tool definitions               |
|   - Resolve config + secrets from .env                  |
+--------------------------+------------------------------+
                           v
+---------------------------------------------------------+
|                  PLAN (Claude Sonnet)                   |
|   - Decompose goal into ordered subtasks                |
|   - Pick model per task (Sonnet / Haiku / Tier-0)       |
+--------------------------+------------------------------+
                           v
+---------------------------------------------------------+
|                  EXECUTE (parallel)                     |
|   - Spawn sub-agents / call tools                       |
|   - Stream tokens, persist artifacts                    |
+--------------------------+------------------------------+
                           v
+---------------------------------------------------------+
|                  VERIFY                                 |
|   - Lint / typecheck / visual diff / QA agent           |
|   - On failure -> re-prompt with error context          |
+--------------------------+------------------------------+
                           v
+---------------------------------------------------------+
|                  SHIP                                   |
|   - Write to disk . commit . PR . upload                |
+---------------------------------------------------------+
```

## Install

```bash
git clone https://github.com/hmzainjamil/ai-website-cloner-template.git
cd ai-website-cloner-template

# Per-repo install (try in order):
bash install.sh 2>/dev/null || \
npm install 2>/dev/null || \
bun install 2>/dev/null || \
pip install -r requirements.txt 2>/dev/null || true
```

Environment:

```bash
cp .env.example .env  # if present
# fill ANTHROPIC_API_KEY at minimum
```

## Usage

```bash
# Claude Code skill packs:
/skill-name "your goal"

# CLI / scripts:
python scripts/<script>.py --input ./input --output ./output

# TypeScript projects:
bun run dev    # or npm run dev
```

### Configuration knobs

| Key | Default | Description |
|---|---|---|
| `ANTHROPIC_API_KEY` | - (required) | Claude API key |
| `MODEL` | `claude-sonnet-4-7` | Default LLM |
| `MODEL_FALLBACK` | `claude-haiku-4` | Cheaper fallback |
| `MAX_TOKENS` | `8192` | Per-call ceiling |
| `TEMPERATURE` | `0.2` | Determinism dial |
| `LOG_LEVEL` | `info` | debug / info / warn / error |
| `OUT_DIR` | `./out` | Where artifacts land |
| `CACHE_DIR` | `.cache` | Prompt cache root |
| `PARALLELISM` | `4` | Sub-agent concurrency |
| `RETRY_MAX` | `3` | Per-call retry budget |
| `TIMEOUT_S` | `120` | Per-call timeout |
| `DRY_RUN` | `false` | Plan-only, no side effects |

### Case 3 - DTC brand, ad creative testing

- Before: $2K/month UGC creator retainer, 4 ads/month.
- After: 30+ ad variants/week via Arcads + Claude, A/B-tested.
- Result: 3x creative velocity, 41% lower CAC after 6 weeks.

## Security

- Never commit API keys. `.env` is in `.gitignore` by default.
- Use [git-secret](https://git-secret.io/) or 1Password CLI for team secret sharing.
- Review the QA / safety layer for any tool that writes to disk or runs shells (see `mac_safety.py` style guards).
- Vulnerability reports: open a private GitHub Security Advisory.

## Limitations

- A generated clone is not automatically equivalent to its source site.
- External websites change independently of this repository.
- Legal and licensing constraints apply to copied content and assets.

## Related

- [Claude Code](https://docs.claude.com/en/docs/claude-code) - official docs
- [Anthropic Console](https://console.anthropic.com) - API keys + billing
- [Crawlee](https://crawlee.dev) - web scraping framework
- [hmz-claude-code-best-practice](https://github.com/hmzainjamil/hmz-claude-code-best-practice) - sister repo

## Maintainer

[hmzainjamil](https://github.com/hmzainjamil)