# PR Review Checklist (Architect) — gate G5

Automated checks (lint, types, tests, security scan) are already enforced by CI. Review the things CI cannot judge.

## Every PR

- [ ] PR references a backlog ticket; acceptance criteria are met
- [ ] CI is green (G3); no skipped or deleted tests
- [ ] No contract deviation (paths, fields, status codes, error shape unchanged)
- [ ] Any Deviation Report attached is justified; decision recorded
- [ ] No unexplained new dependency; no secrets; `.env.example` updated
- [ ] AI-generated code reviewed for: hardcoded values, dead code, invented behavior not in brief

## Backend PR

- [ ] Contract tests cover every endpoint touched
- [ ] Auth/authorization enforced as specified; input validated
- [ ] Migrations are reversible and tested
- [ ] Backward compatible with the currently deployed frontend (merge order!)

## Frontend PR

- [ ] Uses design tokens; matches design handoff
- [ ] Handles loading, empty, error states for every API call
- [ ] No leftover MSW in production bundle; API base URL via env
- [ ] Accessibility basics: labels, focus, contrast, keyboard

## Decision

Approve / Request changes (list items, address to the owning role only).
