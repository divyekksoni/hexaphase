# 5 – Testing

**Question this phase answers:** *Does it actually work?*

## Deliverables
| File | Contents |
|---|---|
| `test-plan.md` | What is tested, how, and by whom (AI, human, automated) |
| `test-cases.md` | Test cases mapped to requirement IDs |
| `bug-log.md` | ID, description, severity, status, fix reference |
| `test-report.md` | Results summary per release |

Automated test **code** lives inside `4-Coding/` next to the app it tests. This folder holds the plans, evidence and results.

## Gate (exit criteria)
- [ ] Every acceptance criterion has at least one passing test
- [ ] No critical or high-severity bugs are open
- [ ] Gate approved in `project-health.md`

## Suggested prompt
> "Generate test-cases.md covering every acceptance criterion in requirements.md, then write automated tests for them in main-app."
