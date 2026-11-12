# CLAUDE.md

🌐 **English** | [Português](CLAUDE.md)

Guidelines for Claude Code when working in this repository.

## Overview

**Open Agent Skills** is an open-source, academic and collaborative collection of **Skills for AI Agents** (Claude, Claude Code, ChatGPT, Google Antigravity and others). The repository is **documentation/content only**: there is no application code, build, dependencies or test suite. The "product" is a set of Markdown `SKILL.md` files.

- Repository: `hanspeterdietiker/Open-Agents-Skills` (GitHub), main branch `main`.
- License: MIT (`LICENSE`).
- Audience: the Brazilian and international community — content in **Portuguese** and **English**.

## Structure

```text
Open-Agents-Skills/
├── assets/                  # Images (e.g. assets/logo.png)
├── skills/                  # All community Skills
│   └── <skill-name>/
│       ├── SKILL.md         # Entry point (required)
│       ├── references/      # Supporting documents (optional)
│       ├── scripts/         # Helper scripts (optional)
│       └── examples/        # Usage examples (optional)
├── README.md                # Portuguese version (main)
├── README.en.md             # English version
├── CLAUDE.md                # Claude Code guidelines (Portuguese)
├── CLAUDE.en.md             # Claude Code guidelines (English)
└── LICENSE
```

The `skills/` folder may not exist yet — create it when adding the first Skill.

## Skill conventions

Every Skill lives at `skills/<skill-name>/SKILL.md`, with YAML frontmatter + a Markdown body:

```markdown
---
name: skill-name
description: Use when ... / Use quando ... (state WHEN the Skill should be triggered)
---

# Skill Name

## When to use
## Step by step
## Examples
```

Rules:

- Folder names in `kebab-case` (e.g. `code-review`, `report-generator`).
- The frontmatter `name` must be **identical** to the folder name.
- `name` and `description` are required. The `description` is the trigger: describe *when* to use the Skill, not *what* it does in detail.
- Whenever possible, include terms in **both Portuguese and English** in the `description` to improve triggering.
- A good Skill is **focused** (one kind of problem), **actionable** (says exactly what to do) and **verifiable** (has success criteria).
- Long material goes in `references/`; keep `SKILL.md` lean.
- **Authorship and credits:** every `SKILL.md` declares `license` and `metadata` (`author`, `source`/`based-on`) in its frontmatter and ends with a `## Créditos / Credits` section. Skills copied from third parties keep the original `LICENSE` in their folder and record what was changed. Referenced sub-skills are listed with their author and where to get them. Add the Skill to the "Available skills" glossary in both READMEs, in alphabetical order (short description + a `<sub>` line with author and basis).
- **No business rules:** before adding a Skill taken from a project, remove client/company names, real issue keys, internal URLs, local paths, emails and domain-specific rules — use neutral placeholders (e.g. `PROJ-41`).

### How to test a Skill

There are no automated tests. To validate, copy the Skill into Claude Code's Skills directory and trigger it on a real task:

```bash
cp -r skills/<skill-name> ~/.claude/skills/      # personal
cp -r skills/<skill-name> .claude/skills/        # project
```

Confirm it triggers from its `description` and also via `/<skill-name>`.

## Bilingual docs

- `README.md` (PT) ↔ `README.en.md` (EN) and `CLAUDE.md` (PT) ↔ `CLAUDE.en.md` (EN) must stay **in sync**: any change to one must be mirrored in the other in the same change.
- Internal link anchors differ between languages (e.g. `#-o-que-é-uma-skill` vs `#-what-is-a-skill`) — adjust them when translating.
- Badges, logo (`assets/logo.png`, `width="420"`) and the centered layout must stay identical in both README versions.

## Git workflow: types, commits, branches and PRs

Commits, branches and Pull Requests follow **the same standard**, based on [Conventional Commits](https://www.conventionalcommits.org/). Everything is written **in English**, even when the conversation is in Portuguese.

### Allowed types (verbs)

| Type | When to use |
| --- | --- |
| `feat` | New Skill or new capability in an existing Skill |
| `fix` | Bug fix (wrong instruction, invalid frontmatter, broken link, trigger that doesn't fire) |
| `docs` | Documentation: READMEs, `CLAUDE.md`, `LICENSE`, guides |
| `refactor` | Restructuring a Skill without changing its behavior (splitting into `references/`, renaming sections) |
| `style` | Formatting only (whitespace, tables, line breaks) |
| `chore` | Maintenance: assets, configs, auxiliary files |
| `ci` | GitHub Actions workflows and automation |

Common scopes: `skills`, `readme`, `assets`, or the Skill name (e.g. `code-review`).

### Commits

```
<type>(<optional scope>): <short description>
```

- Lowercase description, imperative mood (`add`, `fix`, `update`, `remove`), no trailing period, ≤ 72 characters.
- One commit = one logical change. If more context is needed, use the commit body (blank line after the title).

```
feat(skills): add code-review skill
fix(conventional-commits): clarify scope rules in description
docs(readme): sync english readme with portuguese version
refactor(code-review): move checklist to references folder
chore(assets): compress project logo
```

Do not commit or push unless the user asks.

### Branches

```
<type>/<description-in-kebab-case>
```

- Same types as the table above; short description, in English, in `kebab-case`.
- Always branch off an up-to-date `main`. Never work directly on `main`.
- If there is an issue, its number may go at the end: `feat/code-review-skill-12`.

```
feat/code-review-skill
fix/commit-skill-frontmatter
docs/sync-readme-translations
refactor/code-review-references
chore/compress-logo
```

### Pull Requests

**Title** — same format as commits:

```
<type>(<optional scope>): <short description>
```

E.g. `feat(skills): add code-review skill`

**Steps:**

1. `git push -u origin <branch>`
2. `gh pr create --base main --title "<title>" --body-file <file>`
3. Ask the user who should review and use `--reviewer <username>` or mention them in the body — **never make up a `@username`**.

**Body** — always use this template:

```markdown
## Summary

<1–3 sentences: what this PR does and why.>

## Type of change

- [ ] feat — new skill or capability
- [ ] fix — bug fix
- [ ] docs — documentation
- [ ] refactor — restructure without behavior change
- [ ] style / chore / ci

## Changes

- <bullet list of the main changes, citing files/skills>

## How it was tested

- Agent: <Claude Code / Claude / ChatGPT / Antigravity / ...>
- Scenario: <prompt or task used to trigger the skill and the observed result>

## Related issue

Closes #<number>

## Checklist

- [ ] Skill lives at `skills/<skill-name>/SKILL.md`
- [ ] Frontmatter has `name` (matching the folder) and `description`
- [ ] Instructions are clear, actionable and include examples
- [ ] Tested with at least one agent
- [ ] PT/EN READMEs are in sync (if changed)
- [ ] Commits and branch follow Conventional Commits

## Reviewer

@<collaborator-username>
```

Remove sections that don't apply (e.g. "Related issue" when there is no issue; Skill-specific checklist items in a `docs`-only PR).

## Environment

The maintainer uses Windows (PowerShell / Git Bash). Prefer `/` paths and portable commands in documentation examples.
