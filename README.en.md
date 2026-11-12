<div align="center">

<img src="assets/logo.png" alt="Open Agent Skills — Discover • Share • Build" width="720" />

<br />
<br />

[![Claude](https://img.shields.io/badge/Claude-D97757?style=for-the-badge&logo=claude&logoColor=white)](https://claude.ai)
[![Claude Code](https://img.shields.io/badge/Claude%20Code-191919?style=for-the-badge&logo=anthropic&logoColor=white)](https://claude.com/claude-code)
[![Agent Skills](https://img.shields.io/badge/Agent%20Skills-SKILL.md-7C3AED?style=for-the-badge&logo=markdown&logoColor=white)](#-what-is-a-skill)
[![Open Source](https://img.shields.io/badge/Open%20Source-%E2%9D%A4-22D3EE?style=for-the-badge&logo=opensourceinitiative&logoColor=white)](#-how-to-contribute)

[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen?style=flat-square&logo=github)](https://github.com/hanspeterdietiker/Open-Agents-Skills/pulls)
[![Issues](https://img.shields.io/github/issues/hanspeterdietiker/Open-Agents-Skills?style=flat-square&logo=github&label=issues)](https://github.com/hanspeterdietiker/Open-Agents-Skills/issues)
[![Forks](https://img.shields.io/github/forks/hanspeterdietiker/Open-Agents-Skills?style=flat-square&logo=github)](https://github.com/hanspeterdietiker/Open-Agents-Skills/fork)
[![Stars](https://img.shields.io/github/stars/hanspeterdietiker/Open-Agents-Skills?style=flat-square&logo=github)](https://github.com/hanspeterdietiker/Open-Agents-Skills/stargazers)
[![Contributors](https://img.shields.io/github/contributors/hanspeterdietiker/Open-Agents-Skills?style=flat-square&logo=github)](https://github.com/hanspeterdietiker/Open-Agents-Skills/graphs/contributors)
[![License](https://img.shields.io/github/license/hanspeterdietiker/Open-Agents-Skills?style=flat-square)](LICENSE)
[![Made in Brazil](https://img.shields.io/badge/Made%20in-Brazil%20%F0%9F%87%A7%F0%9F%87%B7-009C3B?style=flat-square)](#)

🌐 **English** | [Português](README.md)

**An open-source, academic and collaborative community to discover, share and build _Skills_ for AI Agents — from Brazil to the world.** 🇧🇷 🌎

[About](#-about-the-project) •
[What is a Skill](#-what-is-a-skill) •
[Structure](#-repository-structure) •
[Usage](#-usage) •
[How to contribute](#-how-to-contribute) •
[Community](#-community)

</div>

---

## 📖 About the project

**Open Agent Skills** was born with a simple purpose: **to democratize knowledge about how to teach AI Agents to perform specialized tasks.**

Language models like **Claude** are extremely capable, but they become even more useful when given *packaged, reusable and versioned instructions* on **how** to carry out a specific kind of work — whether that's writing commit messages following Conventional Commits, reviewing software architecture, generating reports, running a debugging process or automating an everyday workflow. These instructions are called **Skills**.

This repository is an **open collection of Skills**, built by and for the AI community, around four pillars:

| Pillar | Description |
| --- | --- |
| 🔓 **Open-source** | All content is open, auditable and free to use, adapt and redistribute. |
| 🎓 **Academic** | We encourage well-documented Skills grounded in best practices and references, also serving as study material for students, researchers and teachers. |
| 🤝 **Interactive** | Skills evolve through issues, discussions, reviews and pull requests — every contribution is reviewed by the community. |
| 🌎 **Brazil and abroad** | A meeting point for the Brazilian AI community, open to contributions from all over the world, in **Portuguese** and **English**. |

### 🎯 Goals

- **Discover** — gather useful, tested and well-explained Skills in one place.
- **Share** — make it easy for anyone to publish and reuse Skills in their own agents.
- **Build** — serve as a lab to experiment with, compare and improve prompt engineering, *context engineering* and agent design techniques.
- **Teach** — produce high-quality learning material about AI Agents, lowering the barrier to entry for the Brazilian community and beyond.

---

## 🧠 What is a Skill?

A **Skill** is a package of instructions (and, optionally, scripts, templates and reference files) that an AI agent loads **on demand** when the task at hand matches the Skill's description.

Each Skill lives in its own folder and has a `SKILL.md` file as its entry point, made of:

1. **YAML frontmatter** — metadata with `name` and `description`. The `description` is what the agent reads to decide *when* to trigger the Skill.
2. **Markdown body** — the instructions themselves: step-by-step guidance, rules, examples and common pitfalls.

```markdown
---
name: conventional-commits
description: Use when the user asks to create a commit or write a commit message following the Conventional Commits standard.
---

# Conventional Commits

## When to use
...

## Step by step
1. Inspect the staged diff with `git diff --staged`.
2. Identify the type of change (feat, fix, docs, refactor, ...).
3. ...

## Examples
...
```

> 💡 **Tip:** a good Skill is **focused** (solves one kind of problem), **actionable** (says exactly what to do) and **verifiable** (includes criteria to tell whether the task was done well).

---

## 🗂️ Repository structure

```text
Open-Agents-Skills/
├── assets/                  # Images and visual assets for the project
├── skills/                  # All community Skills
│   └── <skill-name>/
│       ├── SKILL.md         # Entry point (required)
│       ├── references/      # Supporting documents (optional)
│       ├── scripts/         # Helper scripts (optional)
│       └── examples/        # Usage examples (optional)
├── README.md                # Portuguese version
└── README.en.md             # English version
```

**Conventions:**

- Folder names in `kebab-case` (e.g. `code-review`, `report-generator`).
- The `name` in the frontmatter must match the folder name.
- Skills may be written in Portuguese or English — when possible, include terms in both languages in the `description` to improve triggering.

---

## 🚀 Usage

### With Claude Code

1. Clone the repository:

   ```bash
   git clone https://github.com/hanspeterdietiker/Open-Agents-Skills.git
   ```

2. Copy the desired Skill folder into Claude Code's Skills directory:

   ```bash
   # Personal Skills (available in all your projects)
   cp -r Open-Agents-Skills/skills/<skill-name> ~/.claude/skills/

   # Project Skills (shared with your team via git)
   cp -r Open-Agents-Skills/skills/<skill-name> .claude/skills/
   ```

3. Done! Claude will automatically trigger the Skill whenever the task matches its description — or you can invoke it directly with `/<skill-name>`.

### With other agents

The `SKILL.md` format is simple and Markdown-based, so it can be adapted to other agents and frameworks: just include the Skill's content in the agent's context when the matching task is detected.

---

## 🤝 How to contribute

Contributions are **very welcome** — new Skills, improvements to existing ones, fixes, translations or documentation! The workflow is:

### 1. Fork the repository 🍴

Click [**Fork**](https://github.com/hanspeterdietiker/Open-Agents-Skills/fork) at the top of the page and clone your fork:

```bash
git clone https://github.com/<your-username>/Open-Agents-Skills.git
cd Open-Agents-Skills
git checkout -b feat/my-new-skill
```

### 2. Pick or open an issue 📌

- Browse the [**open issues**](https://github.com/hanspeterdietiker/Open-Agents-Skills/issues) and pick one to work on — leave a comment on the issue so others know you're on it.
- Have a new idea? [**Open an issue**](https://github.com/hanspeterdietiker/Open-Agents-Skills/issues/new) describing the proposed Skill, the problem it solves and usage examples.

### 3. Build your contribution 🛠️

- Create the `skills/<skill-name>/` folder with a `SKILL.md` file.
- Write a clear `description` stating **when** the Skill should be used.
- Test the Skill with a real agent before submitting.
- Use [Conventional Commits](https://www.conventionalcommits.org/) for commit messages (e.g. `feat(skills): add code-review skill`).

### 4. Open a Pull Request 🚀

```bash
git push origin feat/my-new-skill
```

Open a [**Pull Request**](https://github.com/hanspeterdietiker/Open-Agents-Skills/pulls) against the `main` branch and:

- ✅ Describe what the Skill does and how it was tested.
- ✅ Reference the related issue (e.g. `Closes #12`).
- ✅ **Mention a reviewer who is a project collaborator** (e.g. `@collaborator-username`) in the PR body, or request their review from the *Reviewers* panel. Check the [contributors list](https://github.com/hanspeterdietiker/Open-Agents-Skills/graphs/contributors) to find someone who can review.

> 📝 Every PR goes through community review. Be kind, constructive and open to suggestions — the goal is to learn together!

### ✔️ Good contribution checklist

- [ ] The Skill is located at `skills/<skill-name>/SKILL.md`
- [ ] The frontmatter contains `name` and `description`
- [ ] Instructions are clear, objective and include examples
- [ ] The Skill was tested with at least one agent
- [ ] The PR references an issue and mentions a reviewer

---

## 🌐 Community

This is a project **by the community, for the community**. Students, teachers, researchers, professionals and AI enthusiasts are all welcome — in Brazil and abroad.

- 💬 Questions, ideas and proposals: open an [issue](https://github.com/hanspeterdietiker/Open-Agents-Skills/issues).
- ⭐ Like the project? Leave a **star** — it helps the community grow!
- 📣 Share it with your class, your team or your study group.

### 👥 Contributors

<a href="https://github.com/hanspeterdietiker/Open-Agents-Skills/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=hanspeterdietiker/Open-Agents-Skills" alt="Contributors" />
</a>

---

<div align="center">

**Open Agent Skills** — *Discover • Share • Build*

Made with 💜 by the AI community 🇧🇷 🌎

</div>
