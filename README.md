# Hexaphase

**Hexaphase™ is a folder-first Software Development Life Cycle (SDLC) framework for building software with AI.**

*Hexa* (six) + *phase*: six phases, two files, any AI tool.

Created by **Divyek Soni** · Version 1.0 · 2026

[![Built with Hexaphase](https://img.shields.io/badge/built%20with-Hexaphase-6f42c1)](https://github.com/divyekksoni/hexaphase)

---

## Why Hexaphase?

Everyone uses AI for software differently. One person pastes code into a chat window, another lets an agent rewrite the whole repo, and a third keeps prompts in their head. The result is often the same: code with no plan, no design, no tests, and an AI that forgets everything between sessions.

Scrum gave teams a shared way to *organize work*. **Hexaphase gives humans and AI a shared way to organize a project.**

It is intentionally simple:

- **Two files at the root** tell any AI how to behave and where the project stands.
- **Six numbered folders** walk every project through the classic SDLC: Planning → Analysis → Design → Coding → Testing → Deployment.
- **Code lives in one place** (`4-Coding/`), with the main app separated from supporting apps.

It's plain Markdown and folders, so it works with any technology and any project size. **Tested with Claude Code and Gemini CLI**; other AI tools are coming.

---

## The Structure

```
your-project/
├── ai-instructions.md      ← The rulebook every AI reads first
├── project-health.md       ← Live status: phase, progress, risks, decisions, session log
│
├── 1-Planning/             ← What are we building and why?
├── 2-Analysis/             ← Is it feasible? What are the options and risks?
├── 3-Design/               ← How will it be built?
├── 4-Coding/               ← The code itself
│   ├── main-app/           ← The primary application (the thing you launch)
│   └── <supporting-app>/   ← Optional: admin panel, worker, API, shared library…
├── 5-Testing/              ← Does it work? Test plans, cases, bug log
└── 6-Deployment/           ← How does it ship and run? Guides, releases, runbooks
```

The numbers matter. They show the natural order of work, and they keep the folders sorted the same way in every file explorer, IDE and AI context window.

---

## The Six Principles

1. **Structure before prompts.** A well-organized repo beats a clever prompt.
2. **The repo is the memory.** AI forgets between sessions; files don't. Every decision, plan and status lives in a file.
3. **One phase at a time, with gates.** Each phase has exit criteria. Going back is allowed; skipping silently is not.
4. **Humans decide, AI drafts.** AI proposes plans, designs, code and tests. A human approves each phase gate.
5. **Health is always visible.** Anyone (human or AI) can open `project-health.md` and know exactly where things stand.
6. **Tool-agnostic by design.** No vendor lock-in. Markdown and folders work everywhere.

---

## The Rituals

Scrum has ceremonies. Hexaphase has three lightweight rituals:

| Ritual | When | What happens |
|---|---|---|
| **Hexaphase Session Start** | Every time an AI session begins (the human types the command; the AI also does it automatically) | The AI reads `ai-instructions.md`, then `project-health.md`, then the current phase folder, and confirms the current phase and next task before writing anything. |
| **Hexaphase Session End** | Every time an AI session ends (typed, or automatically when files changed) | The AI adds an entry to the Session Log in `project-health.md`: what changed, what's next, and any open questions. |
| **Phase Gate** | When a phase's exit criteria are met | The human reviews the phase deliverables, ticks the gate in `project-health.md`, and the project moves to the next phase. |

## The Roles

| Role | Responsibility |
|---|---|
| **Project Owner (human)** | Sets goals, answers questions, approves phase gates, owns final decisions. |
| **AI Assistant(s)** | Drafts documents, designs, code and tests; follows `ai-instructions.md`; keeps `project-health.md` current. |
| **Reviewer (optional human)** | Reviews code, designs or releases on larger teams. |

---

## Quick Start

1. Copy the [`template/`](template/) folder into a new project (or the root of an existing one).
2. Fill in the **Project Overview** section at the top of `ai-instructions.md`.
3. Open the project in a supported AI tool. The template includes the file each tool loads automatically, which points the AI to `ai-instructions.md`:

   | Tool | Auto-loaded file | Status |
   |---|---|---|
   | **Claude Code** | `CLAUDE.md` | ✅ Tested |
   | **Gemini CLI** | `GEMINI.md` | ✅ Tested. Tip: if responses are slow, start with `gemini -m gemini-3-flash-preview` (or switch with `/model`). |

   Other tools (Cursor, Copilot, Codex, ChatGPT…) aren't officially tested yet. See [GUIDE.md](GUIDE.md#other-ai-tools-untested) to try them.
4. Start every session by typing **`Hexaphase Session Start`** and end it with **`Hexaphase Session End`**.

Adding Hexaphase to an **existing project**, or want a **lighter version** for a weekend build? See [GUIDE.md](GUIDE.md#adopting-hexaphase).

---

## Going Back Is Normal

Hexaphase is not waterfall. Requirements change, tests reveal design flaws, deployments uncover bugs. When that happens:

- Go back to the earlier phase folder and update its documents.
- Record the change in the **Decisions Log** in `project-health.md`.
- Keep moving forward.

For larger projects you can run Hexaphase **per feature or per release**: plan, analyze, design, code, test and deploy one slice at a time, which works well alongside Scrum sprints.

---

## Full Guide

See [GUIDE.md](GUIDE.md) for each phase in detail: purpose, deliverables, gate criteria, and example prompts.

---

## Built with Hexaphase?

Add the badge to your project's README and help others discover the framework:

```markdown
[![Built with Hexaphase](https://img.shields.io/badge/built%20with-Hexaphase-6f42c1)](https://github.com/divyekksoni/hexaphase)
```

---

## Contributing

Hexaphase is maintained by its author, much as the Scrum Guide is maintained by its creators. Ideas, case studies and translations are welcome. See [CONTRIBUTING.md](CONTRIBUTING.md).

---

## Attribution

Hexaphase was created by **Divyek Soni**. When you write about, teach, adapt or build on this framework, please credit:

> Hexaphase SDLC Framework by Divyek Soni, https://github.com/divyekksoni/hexaphase

See [LICENSE.md](LICENSE.md) and [NOTICE](NOTICE) for the terms.
