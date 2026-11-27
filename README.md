# AI Content Guidelines

**Version 1.0.0** · Released 27 November 2026 · Last checked against Google Search Central documentation: 27 November 2026

A skill for AI coding and writing agents (Claude, Claude Code, Codex, Gemini / Antigravity, Cursor, Copilot, Windsurf and others). It covers what the agent should keep in mind when it builds a website or writes content for one, so the result is helpful to people, stays within Google's spam policies and is ready for AI search.

---

## What it covers

- **People-first content.** No invented facts, testimonials, reviews, authors or credentials. Visible `[TODO]` placeholders when real information is missing. Human review before publishing.
- **Google spam policies.** Scaled content abuse, doorway pages, cloaking, hidden text, keyword stuffing, link spam, thin affiliation, site reputation abuse and more, each with the legitimate alternative.
- **E-E-A-T and YMYL.** Real authorship, AI-use disclosure, and extra care for health, money, legal and safety topics.
- **Technical SEO.** Server-side rendering, canonicals, indexing controls, robots.txt, sitemaps, metadata, hreflang and Core Web Vitals.
- **Structured data.** JSON-LD only for visible content, never fabricated, always validated.
- **Site architecture.** Clear intent per page, no cannibalization, no orphan pages, no thin location or service pages.
- **GEO (AI search readiness).** Treating search and training crawlers as separate decisions, content that can be extracted without JavaScript, entity signals, and optional extras like `llms.txt`.
- **Agent rules.** Check impact before changing anything SEO-critical, use 301 redirect maps when URLs change, and don't let staging `noindex` reach production.
- **Pre-deployment checklist** and a **final SEO report** the agent gives the user at the end of every website task.

The full guidelines are in [`SKILL.md`](SKILL.md).

---

## Installation

### Claude Code (plugin)

```text
/plugin marketplace add sanjivthakur165/ai-content-guidelines
/plugin install ai-content-guidelines@ai-content-guidelines
```

This needs a recent version of Claude Code. If the plugin commands aren't available, use the skills CLI below.

### Claude Code, Codex and other agents (skills CLI)

```bash
# Claude Code
npx skills add sanjivthakur165/ai-content-guidelines --global --agent claude-code

# Codex
npx skills add sanjivthakur165/ai-content-guidelines --global --agent codex

# Every supported agent (Gemini CLI, GitHub Copilot, Cursor, Windsurf and others)
npx skills add sanjivthakur165/ai-content-guidelines --global --agent '*'
```

Leave out `--global` to install for the current project only.

### Claude.ai and Claude Desktop

1. On this repo's page, click **Code → Download ZIP**, or download `ai-content-guidelines-v1.0.0.zip` from the Releases page.
2. Upload the ZIP as a skill in Claude's settings.
3. Claude loads the skill automatically when a task involves building or writing a website.

### pi

```bash
pi install git:github.com/sanjivthakur165/ai-content-guidelines
```

Add `-l` to install for the current project only. Run `pi update --extensions` to get new versions.

### Any other agent (manual)

Copy `SKILL.md` into the agent's skills folder. If the agent doesn't support skills, paste the contents into its rules or instructions file:

| Tool | File |
|---|---|
| Gemini CLI / Antigravity | `GEMINI.md` or the workspace rules |
| Cursor | `.cursor/rules/ai-content-guidelines.mdc` |
| GitHub Copilot | `.github/copilot-instructions.md` |
| Windsurf | `.windsurfrules` |
| Codex and other `AGENTS.md`-aware tools | `AGENTS.md` in your project |

---

## How to use it

Ask your agent to build or edit a site as usual. With the skill loaded, the agent should:

1. Write people-first content and mark anything it can't verify with `[TODO]`.
2. Avoid spam-policy patterns and explain the risk if you ask for one.
3. Run the pre-deployment checklist before calling the task done.
4. End with an SEO report covering what passed, what failed, what needs human fact-checking, and what you need to decide.

You can also call it directly:

- Claude: *"Use the AI content guidelines skill to audit this page."*
- Codex: *"Use $ai-content-guidelines while you build this site."*

---

## Repository layout

| File | Purpose |
|---|---|
| `SKILL.md` | The skill itself and the source of truth |
| `README.md` | This file |
| `CHANGELOG.md` | Release notes |
| `LICENSE` | MIT license |
| `AGENTS.md` | Rules for agents and people who edit this repo |
| `.claude-plugin/` | Claude Code plugin and marketplace manifests |
| `.cursor-plugin/` | Cursor plugin manifest |
| `agents/openai.yaml` | Codex display name and default prompt |
| `package.json` | pi package manifest |
| `scripts/validate-package.py` | Checks frontmatter, JSON and version sync |
| `.github/workflows/validate.yml` | Runs the validator on every push and pull request |

---

## Sources

The guidelines are based on these sources. Credit goes to their authors.

**Google Search Central**
- [Using generative AI content](https://developers.google.com/search/docs/fundamentals/using-gen-ai-content/)
- [Spam policies for Google web search](https://developers.google.com/search/docs/essentials/spam-policies)
- [Creating helpful, reliable, people-first content](https://developers.google.com/search/docs/fundamentals/creating-helpful-content)
- [What web creators should know about the March 2024 core update and new spam policies](https://developers.google.com/search/blog/2024/03/core-update-spam-policies)

Google Search Central documentation is published by Google, and this repo summarizes and paraphrases it. Except where Google notes otherwise, Google's developer documentation content is licensed under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).

**Open-source SEO / GEO audit tools**
- [searchsolved/search-audit-kit](https://github.com/searchsolved/search-audit-kit): checklists built from Google's documentation
- [MelnixDev/seo-crawl-audit](https://github.com/MelnixDev/seo-crawl-audit): crawl and regression checks
- [alexsilver8/open-seo](https://github.com/alexsilver8/open-seo): on-page, performance, security and AI-search checks
- [zeebees/seo-geo-audit](https://github.com/zeebees/seo-geo-audit): hostname, rendering, AI crawler and cloaking checks
- [indexcraft/ai-seo-audit-agent](https://github.com/indexcraft/ai-seo-audit-agent): technical, content and GEO scoring

No code from these repositories is included. They were used as references for which checks to include.

The repository layout follows the multi-agent packaging approach of [blader/humanizer](https://github.com/blader/humanizer).

---

## Disclaimer

These are independent guidelines based on Google's public documentation and common SEO practice. They are **not** official Google rules, and Google is not affiliated with or endorsing this project. Following them does not guarantee rankings, indexing or citations in AI search.

Some figures in the skill are widely used conventions, not Google requirements. These include title length (about 50–60 characters) and meta description length (about 120–160 characters). Google's policies and AI search behaviour change over time, so check the dates above and the linked sources for the latest guidance.

AI-generated content still needs review by a person before publishing. Always fact-check, especially for health, finance, legal and safety topics.

---

## Contributing

Issues and pull requests are welcome, especially when Google updates its documentation. Read [`AGENTS.md`](AGENTS.md) first, and run `python3 scripts/validate-package.py` before you open a pull request.

See [`CHANGELOG.md`](CHANGELOG.md) for version history.

---

## License

Released under the [MIT License](LICENSE).
