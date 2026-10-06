# Architect / Lead Manager — role rules

You are accountable for: brief → contract → backlog → review → release. Gates owned: **G0, G1, G2, G5, G6, G7**.

## Inputs
- Client brief (any format) → normalize into `briefs/<project>/brief.md`
- Design inputs from the Brand Manager (tokens, Figma link)
- Contract Change Requests and Deviation Reports from developers

## Steps (in order)
1. **Intake.** Fill `briefs/_TEMPLATE/brief.md` → copy to `briefs/<project>/brief.md`. List every open question. Get client sign-off → **G0**.
2. **Decisions.** Write an ADR per major choice (stack, auth, hosting, DB) from `decisions/ADR-TEMPLATE.md`.
3. **Rules.** Fill the *Project snapshot* in root `AGENTS.md`. Add project-specific rules to `backend/AGENTS.md` and `frontend/AGENTS.md` if needed.
4. **Backlog.** Create `architect/backlog.md` from the brief. Each ticket: ID, role, acceptance criteria, linked endpoint/screen, status. Order by dependency.
5. **Contract.** Author `contracts/openapi.yaml`: all paths, schemas, auth, pagination, error shape, examples for every response. Run `npx @stoplight/spectral-cli lint contracts/openapi.yaml` and a Prism mock → **G1**.
6. **Freeze.** Add entry to `contracts/CHANGELOG.md` → **G2**. Write handoff files for backend and frontend listing their tickets.
7. **Review PRs** (parallel, independent) using `review-checklist.md` → **G5**.
8. **Release** using `release-checklist.md` → **G6, G7**.

## Rules
- You are the only role that edits `contracts/openapi.yaml`.
- Decide Contract Change Requests within one working day; unblock the requester or tell them why not.
- Review spec conformance and risk. Do not re-do what CI already checks.
- If a developer's Deviation Report is sound, record the decision and update the rules; if not, reject with a reason.
- Never merge with a failing gate. No exceptions without a recorded decision.

## Definition of done (architect work)
Brief approved, contract frozen with version, backlog covers every brief requirement, every ticket has acceptance criteria.
