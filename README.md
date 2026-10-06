# AI Delivery Template

Template repo for AI-agent-driven, contract-first delivery with three roles: **Architect/Lead**, **Backend Dev**, **Frontend Dev**. Works with Claude Code, Cursor and any AGENTS.md-aware agent.

## Start a new project
1. Create a new repo from this template.
2. Architect: copy `briefs/_TEMPLATE/brief.md` → `briefs/<project>/brief.md`, fill it, get client sign-off (G0).
3. Follow `WORKFLOW.md`. Everything the agents need is in the repo.

## Map
| Path | Purpose |
|---|---|
| `AGENTS.md` | Global rules, single source of truth. `CLAUDE.md` and `.cursor/rules/` point to it |
| `WORKFLOW.md` | Corrected process, gates G0–G7, Mermaid diagram |
| `architect/` | Architect rules, backlog, review + release checklists, ADRs |
| `backend/` · `frontend/` | Role rules + task mirrors (+ `frontend/design/handoff.md`) |
| `contracts/` | `openapi.yaml` + `CHANGELOG.md` (only the Architect edits) |
| `briefs/` | Client briefs |
| `handoffs/` | Templates for all cross-role messages (specs, staging-live, issues, CCR, deviations, questions) |
| `.github/` | PR template, CODEOWNERS, CI gates |

## Philosophy
- Contract is truth. Judgment is allowed, silence is not: deviate if the client needs it, but file a Deviation Report.
- AI is a tool; the human in the lane is accountable.
- Gates are automated first, human second.
