# Guide for agents working on this repo

This file is for AI agents (and people) editing the **AI Content Guidelines** repo itself. To *use* the guidelines on a website project, install the skill as described in `README.md`.

## What this repo is

A Markdown-only agent skill with no build step. `SKILL.md` is the source of truth. Every other file packages it for a particular tool.

## Files

| File | Purpose |
|---|---|
| `SKILL.md` | The skill: frontmatter (name, description, license, version) and all the rules |
| `README.md` | What the skill covers, installation for each tool, usage, sources, disclaimer |
| `CHANGELOG.md` | Release notes, newest first |
| `LICENSE` | MIT |
| `.claude-plugin/plugin.json` | Claude Code plugin manifest |
| `.claude-plugin/marketplace.json` | Lets Claude Code add this repo as a plugin marketplace |
| `.cursor-plugin/plugin.json` | Cursor plugin manifest |
| `agents/openai.yaml` | Display name and default prompt for Codex |
| `package.json` | pi package manifest |
| `scripts/validate-package.py` | Checks frontmatter, JSON, version sync and word count |
| `.github/workflows/validate.yml` | Runs the validator on every push and pull request |

## Rules for changes

- Keep `SKILL.md` and `README.md` in sync. If you add, remove or rename a section in `SKILL.md`, update "What it covers" in the README.
- Keep the version identical in `SKILL.md` (`metadata.version`), `package.json`, both `.claude-plugin` files and `.cursor-plugin/plugin.json`. Use semantic versioning: patch for wording fixes, minor for new rules, major for changes that alter existing behaviour.
- Add a `CHANGELOG.md` entry for every change in behaviour.
- Keep `SKILL.md` under 5,000 words so it loads cheaply into an agent's context.
- Keep the `name` in `SKILL.md` as `ai-content-guidelines` (lowercase, hyphens), matching the plugin manifests.
- Every rule taken from Google's documentation must stay accurate to the current source. When Google updates a page, update the rule, update "Last checked" in the README, and note it in the changelog.
- Label conventions as conventions (for example title and meta description lengths). Don't present them as Google requirements.
- Don't copy text from sources. Paraphrase and link.
- Keep install instructions neutral across agents.

## Before publishing

```bash
python3 scripts/validate-package.py
```

If the tools are installed, also run:

```bash
claude plugin validate .
npx skills add . --list
```

## Writing style

Plain language, short sentences and active voice. Use one term per concept. Use "never" and "must" for hard rules, and "should" for recommendations.
