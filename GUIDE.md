# Hexaphase Guide, v1.0

*By Divyek Soni*

This guide covers each phase in detail. Every phase folder in the template also has its own `README.md` with the same information, so the AI can read it in context.

---

## Root Files

### `ai-instructions.md`
The contract between the project and any AI. It covers:
- a project overview (name, goal, users, tech stack)
- the commands `Hexaphase Session Start` and `Hexaphase Session End`, and what the AI does for each
- where things belong (docs vs. code, main app vs. supporting apps)
- rules for asking questions, making changes, and respecting phase gates

### `project-health.md`
The single source of truth for status:
- current phase and overall status (🟢 / 🟡 / 🔴)
- a phase gate checklist
- open risks and blockers
- the Decisions Log
- the Session Log (latest entry first)

---

## Phase 1: Planning
**Question answered:** *What are we building, for whom, and why?*

| Deliverable | Purpose |
|---|---|
| `vision.md` | Problem, target users, the outcome we want |
| `requirements.md` | Features as user stories with acceptance criteria |
| `scope.md` | In scope / out of scope / future ideas |
| `roadmap.md` | Milestones, or MVP → v1 → v2 |

**Gate:** The vision is clear, an MVP scope is agreed, and requirements have acceptance criteria.

**Example prompt:** *"Interview me one question at a time until you can write vision.md and requirements.md for this project."*

---

## Phase 2: Analysis
**Question answered:** *Can we build it, and what's the smartest way?*

| Deliverable | Purpose |
|---|---|
| `feasibility.md` | Technical, cost and time feasibility |
| `tech-options.md` | Compared options for stack, hosting and libraries, with a recommendation |
| `risks.md` | Risks, likelihood, impact, mitigation |
| `research-notes.md` | Competitors, existing systems, constraints, APIs |

**Gate:** The tech stack is chosen, top risks have mitigations, and no unknown blocks design.

**Example prompt:** *"Compare three tech stacks for requirements.md. Recommend one, with trade-offs, in tech-options.md."*

---

## Phase 3: Design
**Question answered:** *How exactly will it be built?*

| Deliverable | Purpose |
|---|---|
| `architecture.md` | Components, how they talk, diagram (Mermaid recommended) |
| `data-model.md` | Entities, fields, relationships |
| `api-design.md` | Endpoints / interfaces and contracts |
| `ui-design.md` | Screens, flows, wireframes or links |
| `decisions/` | Architecture Decision Records (`ADR-001-*.md`) |

**Gate:** Every MVP requirement maps to a design element, and the folder layout under `4-Coding/` is defined.

**Example prompt:** *"Using requirements.md and tech-options.md, write architecture.md with a Mermaid diagram, and list which apps go in 4-Coding/."*

---

## Phase 4: Coding
**Question answered:** *Build it.*

```
4-Coding/
├── README.md            ← How to run each app; coding standards
├── main-app/            ← The primary application. Launch this.
├── admin-portal/        ← (example) supporting app
├── background-worker/   ← (example) supporting app
└── shared/              ← (example) code shared by several apps
```

Rules:
- **All source code lives in `4-Coding/`.** No other folder in the repo contains application code.
- **`main-app/` is always the thing you launch** to run the product.
- **Each supporting app gets its own subfolder** with its own README explaining what it does and how to run it.
- **Code follows `3-Design/`.** If the code needs to differ from the design, update the design (or add an ADR) first.

**Gate:** All MVP requirements are implemented, the app builds and runs locally, and the code is committed.

**Example prompt:** *"Implement user story US-03 from requirements.md in main-app, following architecture.md. Then update project-health.md."*

---

## Phase 5: Testing
**Question answered:** *Does it actually work?*

| Deliverable | Purpose |
|---|---|
| `test-plan.md` | What is tested, how, and by whom (AI, human, automated) |
| `test-cases.md` | Cases mapped to requirement IDs |
| `bug-log.md` | Bugs found, severity, status |
| `test-report.md` | Results summary per release |

Automated test *code* lives next to the app it tests in `4-Coding/`, because that's where test runners expect it. `5-Testing/` holds the plans, evidence and results.

**Gate:** Every acceptance criterion has a passing test, and no critical or high bugs are open.

**Example prompt:** *"Generate test-cases.md covering every acceptance criterion in requirements.md, then write automated tests for them in main-app."*

---

## Phase 6: Deployment
**Question answered:** *How does it ship, run and recover?*

| Deliverable | Purpose |
|---|---|
| `deployment-guide.md` | Step-by-step deployment |
| `environments.md` | Dev / staging / prod: URLs and config (never secrets) |
| `release-notes.md` | What changed in each version |
| `runbook.md` | Monitoring, common failures, rollback |

**Gate:** Deployed to the target environment, a smoke test passes, and rollback is documented.

**Example prompt:** *"Write deployment-guide.md and a CI pipeline to deploy main-app to &lt;platform&gt;. Include rollback steps."*

---

## Scaling Hexaphase

| Project size | How to apply |
|---|---|
| **Weekend / solo vibe project** | Keep each phase to one short file. Gates take minutes. |
| **Startup / small team** | Full template. Run the phases once per release. |
| **Large / multi-team** | One Hexaphase structure per product or service. Run the phases per feature inside Scrum sprints. ADRs become mandatory. |

---

## Adopting Hexaphase

### Hexaphase Lite (solo / weekend projects)
Keep all six folders, but use a single `notes.md` in each phase folder instead of the full set of deliverables. Gates are a quick self-check. You keep the habit and the structure, without the paperwork.

### Existing projects
You don't need a big-bang migration.
1. Add `ai-instructions.md`, `project-health.md` and the six folders at the root.
2. Move the existing code into `4-Coding/main-app/` in **one dedicated commit** (`git mv`, so history is preserved), and fix build paths in that same commit.
3. Ask the AI to *reverse-engineer* `3-Design/architecture.md` and `1-Planning/requirements.md` from the code, and review them.
4. Set `project-health.md` to the phase you are really in (usually 4 or 5), and continue from there.

### Tooling notes for `4-Coding/main-app/`
Because the app is not at the repo root, set the app's root directory once in your tooling:
- **Hosting** (Vercel, Netlify, Render, Railway…): set "Root Directory" to `4-Coding/main-app`.
- **CI** (GitHub Actions etc.): use `working-directory: 4-Coding/main-app`.
- **Docker**: use `4-Coding/main-app` as the build context, or a Dockerfile inside it.
- **Monorepo tools** (npm/pnpm workspaces, Nx, Turborepo): list `4-Coding/*` as the workspace packages.

### Keep the AI's context small
Hexaphase docs grow over time. The `Hexaphase Session Start` command tells the AI to read only the two root files plus the **current** phase folder. Earlier phases are read on demand. Keep `project-health.md` short: archive Session Log entries older than about 20 into `project-health-archive.md`.

---

## Security Rules (all phases)
- Never commit secrets, keys or passwords. Reference them in `environments.md` by name only.
- The AI must not run destructive commands (deleting data, force-pushing, dropping databases) without explicit human approval.
- Review AI-suggested dependencies before adding them.
