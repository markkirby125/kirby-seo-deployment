# Programmatic SEO Deployment & Network Isolation (Kirby SEO Deployment)

[![Kirby Skills Collection](https://img.shields.io/badge/Kirby_Skills-Collection-blue?style=flat-square&logo=github)](https://github.com/markkirby125/kirby-skills-collection)

You are trying to scale your search footprint by publishing a large volume of programmatic SEO content. For a long time, the standard playbook was to buy an expired domain, fire up a bulk AI content generator, and publish thousands of pages on day one to brute-force your way into the index.

**However, Google's "Scaled Content Abuse" and "Site Reputation Abuse" spam updates have weaponized deployment velocity against you.** Google now actively monitors publishing spikes, network footprints, and domain history mismatches.

If you deploy scale content without rigorous staging, velocity gating, and footprint isolation, your entire domain will trigger algorithmic suppression or a manual de-indexing penalty overnight.

**The Solution:** The `kirby-seo-deployment` skill dictates the exact mechanical rules for safe AI content deployment. From the MVP AI Content Testing Protocol (David Quaid) to IP isolation and publishing velocity caps, this skill forces your AI agent to deploy programmatic content defensively, evading spam classifiers.

## 🪄 The Magic Prompt

Copy and paste this directly to your AI (Cursor, Windsurf, Claude Code, Antigravity):

```markdown
@agent Please install the kirby-seo-deployment skill into this workspace.
1. Read the `SKILL.md` file and `references/` directory from this repository: https://github.com/markkirby125/kirby-seo-deployment
2. Identify the correct rules system for our current environment (e.g., `.cursor/rules/` for Cursor, `.windsurfrules` for Windsurf, `.clinerules` for Cline, or `~/.agents/skills/` for Antigravity).
3. Save the contents appropriately. If our environment supports multi-file dispatcher skills, clone the directory structure exactly.
4. Confirm when the installation is complete.
```

## Manual Installation

- **Cursor**: Save `SKILL.md` to `.cursor/rules/kirby-seo-deployment.mdc` and copy `references/`
- **Windsurf**: Save `SKILL.md` to `.windsurfrules` and copy `references/`
- **Antigravity**: Clone this repository directly into `~/.agents/skills/kirby-seo-deployment`

## Tech Stack

- **Format**: Markdown / YAML
- **Compatibility**: Antigravity, Claude Code, Cursor, Windsurf, Cline
