# 4 – Coding

**Question this phase answers:** *Build it.*

## Layout
```
4-Coding/
├── README.md        ← this file: app list, how to run, coding standards
├── main-app/        ← the primary application. This is what you launch.
└── <app-name>/      ← supporting apps (admin-portal, worker, api, shared…)
```

## Apps in this project
| Folder | Purpose | How to run |
|---|---|---|
| `main-app/` | Primary application | *(fill in)* |

## Rules
- All application source code lives here, and nowhere else in the repo.
- `main-app/` is always the launchable product.
- Every supporting app has its own folder and its own README.
- Code follows `3-Design/`. Change the design (or add an ADR) before diverging from it.
- Automated tests live next to the code they test.
- Reference requirement IDs (`US-03`) in commit messages.

## Gate (exit criteria)
- [ ] All MVP requirements are implemented
- [ ] Every app builds and runs locally using the instructions above
- [ ] Code is committed to version control
- [ ] Gate approved in `project-health.md`
