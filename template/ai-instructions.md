# AI Instructions

> This project follows the **Hexaphase SDLC Framework** (by Divyek Soni).
> Any AI assistant working on this project MUST read this file first and follow it.

---

## 1. Project Overview  *(the human fills this in)*

| Field | Value |
|---|---|
| Project name | |
| One-line goal | |
| Target users | |
| Tech stack | *(decided in 2-Analysis; leave blank until then)* |
| Project Owner | |
| Repository | |

---

## 2. Hexaphase Commands

The human controls sessions with these commands (any capitalisation, with or without punctuation):

| Command | What the AI does |
|---|---|
| **`Hexaphase Session Start`** | Runs Section 3 |
| **`Hexaphase Session End`** | Runs Section 4 |

## 3. Hexaphase Session Start

Run this when the human types **`Hexaphase Session Start`**. If a session begins with any other request, run these steps silently before acting on it.

1. Read this file completely.
2. Read `project-health.md` and identify the **current phase**, the **last Session Log entry**, and any **open blockers**.
3. Read the `README.md` of the current phase folder, plus any documents in it. Read earlier phases only when needed.
4. Reply with a short summary: *current phase, what was done last, gate status, and what you propose to do next.*
5. Wait for the human to confirm before making changes.

## 4. Hexaphase Session End

Run this when the human types **`Hexaphase Session End`**. Also run it before you finish any session in which files changed, even if the human didn't ask.

1. Add a new entry at the **top** of the Session Log in `project-health.md`:
   - the date and a short session title
   - what changed (files created or modified)
   - what is next
   - open questions for the human

   If you already logged this session, update that entry instead of adding a duplicate.
2. Update "Last updated", the status and the phase gate checklist if anything moved. Never tick a gate yourself; only the human approves gates.
3. Reply with the summary and ask whether to commit the changes.

---

## 5. Where Things Belong

| Content | Location |
|---|---|
| Vision, requirements, scope, roadmap | `1-Planning/` |
| Feasibility, tech options, risks, research | `2-Analysis/` |
| Architecture, data model, API, UI, ADRs | `3-Design/` |
| **All application source code** | `4-Coding/` |
| The primary, launchable application | `4-Coding/main-app/` |
| Supporting apps (admin, worker, API, shared libs) | `4-Coding/<app-name>/`, each with its own README |
| Test plans, test cases, bug log, reports | `5-Testing/` |
| Automated test code | Next to the code it tests, inside `4-Coding/` |
| Deployment guides, environments, releases, runbooks | `6-Deployment/` |
| Project status, decisions, session history | `project-health.md` |

Never put source code outside `4-Coding/`. Never put planning or design documents inside `4-Coding/` (except app READMEs).

---

## 6. Rules for the AI

1. **Respect the phase.** Work on the current phase. If you need to change an earlier phase (for example, a requirement turns out to be wrong), say so, update that document, and log it in the Decisions Log.
2. **Don't skip gates.** Don't start coding before the Design gate is approved, unless the human explicitly says to (for example, for a prototype or spike). Log that exception.
3. **Ask, don't assume.** If a requirement is ambiguous, ask one clear question rather than guessing.
4. **Trace everything.** Reference requirement IDs (for example, `US-03`) in designs, code commits and test cases.
5. **Design first, then code.** If code must differ from `3-Design/`, update the design or add an ADR first.
6. **Small, reviewable changes.** Prefer several small changes over one huge one.
7. **No secrets.** Never write keys, passwords or tokens into any file. Use environment variables.
8. **No destructive actions without approval.** Don't delete data or files, force-push, or drop databases unless the human approves.
9. **Keep health honest.** Report problems, failing tests and risks in `project-health.md`. Don't hide them.

---

## 7. Project-Specific Rules  *(optional, the human fills this in)*

- Coding style:
- Libraries to prefer or avoid:
- Anything else the AI should always or never do:
