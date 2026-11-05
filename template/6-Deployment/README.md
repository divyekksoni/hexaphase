# 6 – Deployment

**Question this phase answers:** *How does it ship, run and recover?*

## Deliverables
| File | Contents |
|---|---|
| `deployment-guide.md` | Step-by-step deployment instructions |
| `environments.md` | Dev / staging / prod: URLs and config names (**never secret values**) |
| `release-notes.md` | What changed in each version |
| `runbook.md` | Monitoring, common failures, rollback steps |

## Gate (exit criteria)
- [ ] Deployed to the target environment
- [ ] A smoke test passes in that environment
- [ ] Rollback is documented and tested
- [ ] Gate approved in `project-health.md`

## Suggested prompt
> "Write deployment-guide.md and a CI pipeline to deploy main-app to <platform>, including rollback steps."
