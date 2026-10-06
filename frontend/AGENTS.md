# Frontend Dev — role rules

You build the UI from the design handoff and the OpenAPI contract. You own **G4** (integration against staging). Gate **G3** applies to your PR too.

## Inputs
- `contracts/openapi.yaml` (frozen version)
- `frontend/design/handoff.md` (tokens + Figma link from the Brand Manager)
- Your tickets in `architect/backlog.md` (role = frontend)
- Handoffs in `handoffs/`, including `staging-live-*` from backend

## Steps
1. Read contract, design handoff and tickets. Missing design or unclear behavior → question in `handoffs/`.
2. Branch `feat/<ticket-id>-name`.
3. **Generate MSW handlers from the OpenAPI file** (e.g. `msw-auto-mock` or `orval` with MSW). Never hand-write mock shapes; regenerate whenever the contract version changes.
4. Feed contract + design to your AI agent. Scaffold components, then integrate with mock data. Typed API client should be generated from the contract too.
5. Cover loading, empty, error and unauthorized states for every call. Use design tokens only.
6. Open PR with E2E tests passing on mocks.
7. Wait for the backend's `staging-live` handoff. Then switch API base URL to staging via env (mocks off) and run E2E against staging → **G4**.
8. On failure, **triage before fixing**:
   - FRONTEND_BUG → fix it.
   - BACKEND_BUG → `handoffs/_templates/integration-issue.md` to backend, with the request, response and the contract line violated.
   - CONTRACT_FLAW → `handoffs/_templates/contract-change-request.md` to the Architect.
9. AI auto-fix: max 3 attempts per failure, then escalate to the Architect with logs.

## Rules
- Never code around a backend bug in the UI. Report it.
- Never edit the contract or change a mock to disagree with it.
- No hardcoded colors, spacing or fonts; use tokens.
- MSW must not ship in the production bundle.
- Accessibility baseline: semantic HTML, labels, keyboard navigation, visible focus, contrast AA.
- Responsive behavior per design handoff; test at mobile and desktop widths.
- Client's real need may justify departing from the design or these rules: file a Deviation Report at the time.

## Definition of done
Acceptance criteria met · E2E green on mocks and on staging · all states handled · tokens only · PR template complete.
