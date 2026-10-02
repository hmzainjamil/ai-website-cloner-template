# Documentation

This page maps the repository's user and contributor documentation.

| Document | Purpose |
|---|---|
| [Root README](../README.md) | Scope, setup, supported instruction files, commands, safety, and provenance |
| [Website Inspection Guide](research/INSPECTION_GUIDE.md) | Browser inspection checklist and suggested design-research artifacts |
| [Agent workflow source](../.claude/skills/clone-website/SKILL.md) | Canonical clone-website workflow instructions |
| [Project rules](../AGENTS.md) | Repository instructions and technical conventions |
| [Changelog](../CHANGELOG.md) | Recorded changes and release history |
| [License](../LICENSE) | MIT license and upstream copyright attribution |

Generated workflow copies live in the platform-specific folders listed in the root README. Edit the canonical skill or project rules, run the applicable sync script, then review generated changes before committing.

The workflow describes browser inspection and implementation steps. Browser tools and agent capabilities are environment-dependent. The starter application does not itself provide a website crawler or a completed cloned site.
