# AGENTS.md — Global rules (single source of truth for all AI agents)

Read by Claude Code (via `CLAUDE.md`), Cursor (via `.cursor/rules/`), and any AGENTS.md-aware tool.
Role-specific rules live in `architect/AGENTS.md`, `backend/AGENTS.md`, `frontend/AGENTS.md`.
**Always read the role file for the folder you are working in, then `WORKFLOW.md`.**

## Project snapshot
Fill this in at intake (architect). Keep it under 15 lines.
- Project: `<name>`
- Brief: `briefs/<project>/brief.md`
- Contract: `contracts/openapi.yaml` (current version: see `contracts/CHANGELOG.md`)
- Stack backend: `<fill>` | Stack frontend: `<fill>`
- Staging URL: `<fill>` | Production URL: `<fill>`

## Non-negotiable rules
1. **The OpenAPI contract is the single source of truth.** Never change an endpoint, field, status code or error shape without an approved Contract Change Request (`handoffs/_templates/contract-change-request.md`).
2. **Never invent requirements.** If the brief or contract is silent or ambiguous, stop and raise a question in `handoffs/` — do not guess.
3. **Work only from a backlog ticket.** Every branch, commit and PR references a ticket ID (`architect/backlog.md`).
4. **Never commit to `main`.** Branch → PR → CI green → review → merge.
5. **No secrets in the repo.** Use env vars; add new ones to `.env.example`.
6. **AI-written tests do not count alone.** Backend must pass contract tests against the OpenAPI file; frontend mocks must be generated from it.
7. **Max 3 auto-fix attempts** on the same failure, then stop and escalate (see `WORKFLOW.md` §Integration).
8. **Deviations are allowed but must be reported.** Developers use judgment to meet the client's real need, but any departure from these rules, the contract, or the backlog requires a Deviation Report (`handoffs/_templates/deviation-report.md`) filed *at the time*, not afterwards.

## Definition of done (every ticket)
- Acceptance criteria in the ticket are met.
- Lint, type-check, unit tests pass. Backend: contract tests pass. Frontend: E2E for the ticket's flow passes.
- No new dependency without a one-line justification in the PR.
- PR uses `.github/pull_request_template.md` fully filled in.

## Commit & branch conventions
- Branch: `feat/<ticket-id>-short-name`, `fix/<ticket-id>-short-name`
- Commit: `<type>(<scope>): <summary> [<ticket-id>]` (types: feat, fix, test, docs, refactor, chore)

## Handoffs (how roles talk)
All cross-role communication is a file in `handoffs/` using a template from `handoffs/_templates/`. Chat messages are not a record.
