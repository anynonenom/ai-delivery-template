# Release Checklist (Architect) — gates G6, G7

## Before merge
- [ ] Both PRs approved (G5)
- [ ] Merge order decided: backend first, frontend second (or feature flag noted)

## Staging
- [ ] `main` deployed to staging after merges
- [ ] Smoke tests pass (auth, one critical read, one critical write per module)
- [ ] Client UAT done; sign-off recorded here: `<name, date>` — **G6**
- [ ] New client feedback added to backlog, not silently patched in

## Production
- [ ] Release tagged `vX.Y.Z`; `contracts/CHANGELOG.md` matches
- [ ] DB backup taken; migrations reviewed
- [ ] Rollback plan written: previous tag `<vX.Y.Z-1>`, steps `<fill>`
- [ ] Deploy via CI/CD
- [ ] Post-deploy smoke passes — **G7**
- [ ] If smoke fails: roll back immediately, open incident note in `handoffs/`

## Close
- [ ] Backlog statuses updated, handoff files archived
- [ ] Lessons / rule updates added to `AGENTS.md`
