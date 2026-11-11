# Hexaphase

**Hexaphase™ is a folder-first Software Development Life Cycle (SDLC) framework for building software with AI.**

*Hexa* (six) + *phase*: six phases, two files, any AI tool.

Created by **Divyek Soni** · Version 1.0 · 2026

[![Built with Hexaphase](https://img.shields.io/badge/built%20with-Hexaphase-6f42c1)](https://github.com/divyekksoni/hexaphase) [![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.24029073.svg)](https://doi.org/10.5281/zenodo.24029073)

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

Pick your path:

- **New to coding?** (you build with AI but don't write code yourself) → [Step-by-step guide](#if-youre-new-to-coding)
- **Developer?** → [Developer setup](#if-youre-a-developer)

Want to see it in action? Follow [SpendCLI](https://github.com/divyekksoni/hexaphase-sample-spendcli), an example project being built with Hexaphase in public.

### Supported AI tools

Hexaphase works through an AI coding tool that can read and write files in your project folder. Two are tested:

| Tool | Cost | Auto-loaded file | Status |
|---|---|---|---|
| **Claude Code** | Paid Claude plan (Pro or above) or an Anthropic API account | `CLAUDE.md` | ✅ Tested |
| **Gemini CLI** | Free with a personal Google account (daily limits apply) | `GEMINI.md` | ✅ Tested. Tip: if responses are slow, start it with `gemini -m gemini-3-flash-preview` (or switch with `/model`). |

The template includes both auto-loaded files. Each one simply tells the AI to read `ai-instructions.md` first. Other tools (Cursor, Copilot, Codex, ChatGPT…) aren't officially tested yet; see [GUIDE.md](GUIDE.md#other-ai-tools-untested) to try them.

---

### If you're new to coding

You don't need to know how to program. You'll describe what you want, the AI will plan and build it with you, and Hexaphase keeps everything organized so the AI remembers where you left off. Plan about 20 minutes for the first setup.

#### Step 1: Install an AI coding tool (one time)

Install **one** of these by following its official page:

- **Claude Code**: [claude.com/product/claude-code](https://claude.com/product/claude-code)
- **Gemini CLI**: [github.com/google-gemini/gemini-cli](https://github.com/google-gemini/gemini-cli) (needs [Node.js](https://nodejs.org) installed first; pick the "LTS" version)

Both run in a **terminal**: a window where you type commands instead of clicking. Step 3 shows how to open one. The first time you start the tool, it will ask you to sign in with your Claude or Google account.

#### Step 2: Create your project folder

1. On this page, click the green **Code** button, then **Download ZIP**.
2. Unzip the downloaded file and open the `hexaphase-main` folder inside it.
3. Copy the **`template`** folder and paste it wherever you keep your projects (for example, `Documents`).
4. Rename the pasted folder to your project's name, for example `my-recipe-app`.

Open it to check. You should see `ai-instructions.md`, `project-health.md`, `CLAUDE.md`, `GEMINI.md` and six folders numbered `1-Planning` to `6-Deployment`. That's your project. You can delete the rest of the download.

#### Step 3: Open your project in the AI tool

Open a terminal **inside your project folder**:

- **Windows:** open the folder in File Explorer, click the address bar at the top, type `powershell`, and press Enter.
- **Mac:** open the **Terminal** app, type `cd ` (with a space after it), drag your project folder into the Terminal window, and press Enter.

Then type `claude` (for Claude Code) or `gemini` (for Gemini CLI) and press Enter. If it asks whether you trust the files in this folder, say yes.

#### Step 4: Start your first session

Copy this message, replace the part in angle brackets with your idea, and send it:

```
Hexaphase Session Start.
This is a brand-new project and I'm not a developer, so please explain things in plain language.
My idea: <describe your app in 2-3 sentences: what it does and who it's for>.
Keep it light: use one notes.md file in each phase folder (Hexaphase Lite).
First, help me fill in the Project Overview in ai-instructions.md by asking me questions one at a time. Then guide me through Phase 1 (Planning).
```

#### Step 5: Build it, one phase at a time

The AI walks you through six phases in order: **Planning → Analysis → Design → Coding → Testing → Deployment.** For each one:

1. The AI asks you questions and drafts the documents (and, from Phase 4, the code).
2. **You read what it wrote.** You're the decision-maker: ask for changes until it matches what you want.
3. When the phase is complete, the AI asks you to approve its **gate**. Reply: *"I've reviewed Phase 1 and I approve Gate 1. Please record it in project-health.md."* Then it moves on.

Answering the AI's questions and approving gates is your job. Writing everything else is the AI's job.

#### Step 6: End every session, then pick up later

- When you're done for the day, type **`Hexaphase Session End`**. The AI writes down what changed and what's next in `project-health.md`.
- If it asks whether to **commit**, say yes. A commit is a save point you can return to if something breaks. (The first time, it may offer to set up *git*, the tool that stores save points. Say yes to that too.)
- Next time, open the terminal in the same folder (Step 3) and type **`Hexaphase Session Start`**. The AI reads its notes and tells you exactly where you left off.

#### Useful phrases

| You want to… | Type |
|---|---|
| See where the project stands | `Where are we? Summarize project-health.md for me.` |
| Change your mind about something | `I want to change <X>. Update the earlier phase and log the decision.` |
| Understand something | `Explain that in simple terms.` |
| Try the app | `How do I run the app on my computer? Give me step-by-step instructions.` |

**Safety:** never paste passwords, API keys or bank details into the chat or into project files. If the AI needs a key, ask it how to store it safely.

---

### If you're a developer

#### 1. Scaffold the project

**New project** (pulls only the `template/` folder, without the framework docs):

```bash
npx degit divyekksoni/hexaphase/template my-app
cd my-app
git init && git add . && git commit -m "Scaffold with Hexaphase"
```

No Node? Run `git clone --depth 1 https://github.com/divyekksoni/hexaphase.git` and copy the contents of `hexaphase/template/` into your project. (The GitHub **Use this template** button copies the whole framework repo, docs included, so it's not the best way to start an app.)

**Existing project:** copy the template's two root files and six folders into your repo root. If you already have a `CLAUDE.md` or `GEMINI.md`, append the template's one-line pointer instead of overwriting yours. Then follow the [migration steps](GUIDE.md#existing-projects): move code into `4-Coding/main-app/` in one `git mv` commit, have the AI reverse-engineer requirements and architecture, and set `project-health.md` to the phase you're really in.

#### 2. What's in the template

| Path | Purpose | Who edits it |
|---|---|---|
| `ai-instructions.md` | The rulebook: session commands, where files belong, rules for the AI | You: §1 Project Overview and §7 Project-Specific Rules. The rest is the framework. |
| `project-health.md` | Phase gates, risks, Decisions Log, Session Log | The AI updates it every session; only you approve gates |
| `CLAUDE.md`, `GEMINI.md` | One-line pointers auto-loaded by each tool | Delete the one you don't use |
| `1-Planning/` … `6-Deployment/` | One folder per phase, each with a README explaining what goes in it | The AI drafts, you review |
| `4-Coding/main-app/` | The primary, launchable app. Supporting apps go in `4-Coding/<app-name>/` | |

#### 3. Configure

- Fill in **§1 Project Overview** in `ai-instructions.md`. Leave *Tech stack* blank; it's decided in Phase 2.
- Optionally add coding style, preferred libraries and other house rules in **§7**.
- Choose a mode and say so in §7 or in your first session: **Standard** (the full deliverables per phase in [GUIDE.md](GUIDE.md)) or **Lite** (one `notes.md` per phase, for solo or weekend builds).

#### 4. The session loop

```text
$ claude                      # or: gemini
> Hexaphase Session Start     # AI reads ai-instructions.md → project-health.md → current phase folder,
                              # replies with phase, last session, gate status and a proposed next step,
                              # then waits for your go-ahead
> ...work...
> Hexaphase Session End       # AI adds a Session Log entry, updates status, asks whether to commit
```

If you skip the commands, the AI still runs Session Start silently before your first request, and Session End automatically when files changed.

#### 5. Gates and conventions

- **Gates:** when a phase meets its exit criteria (listed per phase in [GUIDE.md](GUIDE.md)), review the deliverables and mark the gate ✅ in `project-health.md` with your name and the date, or tell the AI you approve and it will record it. The AI never approves a gate itself, and it won't write code before Gate 3 (Design) unless you explicitly allow a spike, which it logs.
- **Traceability:** requirements get IDs (`US-03`) that are referenced in designs, commit messages and test cases.
- **Layout:** all source code goes in `4-Coding/`, with automated tests next to the code they test. Point hosting, CI and Docker at `4-Coding/main-app` ([tooling notes](GUIDE.md#tooling-notes-for-4-codingmain-app)).
- **Going back:** change an earlier phase's docs and log it in the Decisions Log. That's expected, not a failure.
- **Context size:** Session Start reads only the root files and the current phase. Archive Session Log entries older than about 20 into `project-health-archive.md`.

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

## 🧪 Join the Early-Adopter Study

Use Hexaphase on a real project for 4 weeks (starting Nov 23, 2026) and share honest feedback through a short survey and an optional 20-minute interview. Your feedback shapes v1.1 and a research paper (anonymised).

👉 **[Sign up here](https://forms.gle/gQLAMtDLiK3H16xe9)**

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

> Hexaphase SDLC Framework by Divyek Soni, https://github.com/divyekksoni/hexaphase, DOI: [10.5281/zenodo.24029073](https://doi.org/10.5281/zenodo.24029073)

See [LICENSE.md](LICENSE.md) and [NOTICE](NOTICE) for the terms.
