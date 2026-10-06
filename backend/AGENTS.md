# Backend Dev — role rules

You implement the API exactly as `contracts/openapi.yaml` defines it. Gates you must pass: **G3** (CI). You support **G4** by fixing backend bugs from integration.

## Inputs
- `contracts/openapi.yaml` (frozen version, see `CHANGELOG.md`)
- Your tickets in `architect/backlog.md` (role = backend)
- Handoff from Architect in `handoffs/`

## Steps
1. Read the contract and your tickets. Anything unclear → question in `handoffs/`, do not guess.
2. Branch `feat/<ticket-id>-name`.
3. Feed the contract to your AI agent. Generate models, validation and endpoints. **Read the output** — you are accountable for it.
4. Write tests:
   - Unit tests for logic (AI may draft them; you verify they test behavior, not just the implementation).
   - **Contract tests** that run against the real running API and check responses against the OpenAPI file (e.g. Schemathesis / Dredd). Required for every endpoint.
5. Handle: migrations (reversible), auth/authorization, input validation, consistent error shape from the contract, seed data for staging.
6. Open a PR early (draft is fine) using the PR template.
7. When CI is green (**G3**), CI deploys the PR branch to staging. Never deploy to staging by hand from local code.
8. Write `handoffs/staging-live-<date>.md` from the template: URL, version, seed credentials location, known gaps.
9. Respond to integration issues within the agreed time; fix, push, re-notify.

## Rules
- Do not add, rename or remove fields/endpoints/status codes. Need a change? → Contract Change Request.
- Extra behavior not in the contract (e.g. a helper endpoint) is not allowed to ship; propose it instead.
- Backward compatibility: your PR merges first, so it must work with the currently deployed frontend.
- Security baseline: no secrets in code, parameterized queries only, authz on every protected route, rate limiting on auth routes, dependency scan clean.
- Observability: structured logs, request IDs, a `/health` endpoint.
- Auto-fix by AI: max 3 attempts on one failure, then escalate.
- If real client needs make you break a rule here, do it only with a Deviation Report.

## Definition of done
Ticket acceptance criteria met · contract tests green · migrations tested up and down · `.env.example` updated · PR template complete · staging-live handoff written.
