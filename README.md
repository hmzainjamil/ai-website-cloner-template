# AI Website Cloner Template

A reusable Next.js starter with a website reverse-engineering workflow for AI coding agents. It provides platform-specific instructions and a pre-scaffolded application; it does not include a crawler or a completed clone. The current home page explicitly marks the clone target as not yet built.

## Status

| Area | Current state |
|---|---|
| Template | Next.js App Router starter using React, TypeScript, Tailwind CSS, and shared UI components |
| Workflow | `/clone-website <url...>` instructions, with the Claude skill as the source for generated platform copies |
| Agent configuration | Checked-in command, skill, or rules files for the platforms listed below |
| Website inspection | A browser-led inspection guide; actual browser access depends on the agent environment |
| Application | Starter scaffold. Build the requested site in this repository after inspection |
| Node.js | 24 or newer |

Supported instruction/configuration files in this repository: Claude Code, Codex CLI, OpenCode, GitHub Copilot, Cursor, Windsurf, Gemini CLI, Cline, Continue, Amazon Q, Augment Code, and Aider. These files describe workflows; they do not guarantee that a given agent, browser connector, model, or parallel-agent feature is installed or available.

## Quick start

Requirements: Node.js 24 or newer and npm.

```sh
git clone https://github.com/hmzainjamil/ai-website-cloner-template.git
cd ai-website-cloner-template
npm ci
npm run dev
```

Open the local URL printed by Next.js. To use the workflow, open the project in a supported coding agent and provide the target URL to its clone-website command or skill. The workflow requires browser automation to inspect a site; availability depends on your agent setup. Review the target site's terms and rights before using its content or assets.

## What the workflow does

The source instructions in `.claude/skills/clone-website/SKILL.md` guide an agent through browser inspection, visual and interaction notes, design tokens, component specifications, implementation, and visual comparison. Platform copies are generated from that source with `node scripts/sync-skills.mjs`. Project rules are based on `AGENTS.md` and can be copied to selected agent configuration files with `bash scripts/sync-agent-rules.sh`.

Generated agent instructions may differ in format and may omit features that a platform cannot represent. Regenerate them after editing a source file, then review the generated diff before committing.

## Project map

| Path | Purpose |
|---|---|
| `src/app/` | Next.js App Router shell and current starter page |
| `src/components/ui/` | Shared UI components |
| `src/lib/utils.ts` | Shared class-name utility |
| `src/hooks/`, `src/types/` | Reserved locations for hooks and types |
| `.claude/skills/clone-website/SKILL.md` | Source workflow instructions |
| `.codex/`, `.cursor/`, `.github/skills/`, and other agent folders | Platform workflow copies and rules |
| `docs/research/INSPECTION_GUIDE.md` | Website inspection checklist and suggested research artifacts |
| `scripts/sync-skills.mjs` | Generates platform-specific clone workflow files |
| `scripts/sync-agent-rules.sh` | Generates project-rule copies from `AGENTS.md` |
| `Dockerfile`, `Dockerfile.dev`, `docker-compose.yml` | Container build and local development configuration |
| `.github/workflows/ci.yml` | CI lint, typecheck, and build checks |

## Commands

| Command | Purpose |
|---|---|
| `npm run dev` | Start the development server |
| `npm run build` | Create a production build |
| `npm start` | Serve the production build |
| `npm run lint` | Run ESLint |
| `npm run typecheck` | Check TypeScript types |
| `npm run check` | Run lint, typecheck, and build |
| `node scripts/sync-skills.mjs` | Regenerate clone-website workflow copies |
| `bash scripts/sync-agent-rules.sh` | Regenerate project rule copies |

GitHub Actions is configured to run install, lint, typecheck, and build on pushes and pull requests targeting `master`. These commands are documented from the checked-in package and workflow configuration; they were not run as part of this documentation update.

## Documentation

See [docs/README.md](docs/README.md) for the documentation map. Read the [inspection guide](docs/research/INSPECTION_GUIDE.md) before using the workflow.

## Limitations and safe use

- This repository contains agent instructions and a starter application, not a general-purpose site crawler or a guarantee of pixel-perfect results.
- Browser access, asset retrieval, agent execution, and generated output depend on tools and permissions configured in your environment.
- Inspect only sites and materials you are authorized to access. Respect site terms, copyright, privacy, and access controls. Do not collect private or credential-protected content without authorization.
- Review generated code, dependencies, downloaded assets, and external requests before deployment. Do not put API keys or session credentials in source control.
- A generated visual reproduction does not establish permission to reuse a site's branding, copy, images, or other protected material.

## Provenance and license

The repository metadata and changelog identify [JCodesMore/ai-website-cloner-template](https://github.com/JCodesMore/ai-website-cloner-template) as the upstream project. This repository retains the attribution in [LICENSE](LICENSE). See [CHANGELOG.md](CHANGELOG.md) for recorded project changes.

## Contributing

Use the source skill and project rules as the editing points. If changing generated platform instructions, run the corresponding sync script and inspect the complete diff. Use the repository's lint, typecheck, and build checks for implementation changes.

## Maintainer

[hmzainjamil](https://github.com/hmzainjamil)
