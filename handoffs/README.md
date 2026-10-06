# Handoffs

Every cross-role message is a file here, copied from `_templates/` and named `<type>-<NNN>-<short-name>.md`.

| Type | Template | From → To | When |
|---|---|---|---|
| Specs handoff | `specs-handoff.md` | Architect → BE/FE | At contract freeze (G2) |
| Staging live | `staging-live.md` | Backend → Frontend | After CI deploys staging |
| Integration issue | `integration-issue.md` | Frontend → Backend | E2E failure classified BACKEND_BUG |
| Contract change request | `contract-change-request.md` | Anyone → Architect | Contract is wrong/incomplete |
| Deviation report | `deviation-report.md` | Anyone → Architect | Any departure from rules/contract/backlog |
| Question | `question.md` | Anyone → Architect | Brief/contract unclear |

Keep open items at the top of your file's `Status:` line: `open | answered | closed`.
