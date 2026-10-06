# Walkthrough: how the example brief flows through the workflow

Read `brief.md` in this folder first. This shows what the Solution Architect & Lead Manager produces from it.

## G0: brief approved
Nothing starts until open questions 1-4 are answered and the client signs off. The Architect resolves them and sets the status to `approved`.

## Backlog (made from the brief, before the contract)
| ID | Role | Title | Linked to |
|---|---|---|---|
| BE-001 | backend | Auth: register and login | R-001, `POST /auth/register`, `POST /auth/login` |
| BE-002 | backend | Available slots | R-002, `GET /slots` |
| BE-003 | backend | Create, cancel, reschedule appointment | R-002, R-003, `POST/PATCH/DELETE /appointments` |
| FE-001 | frontend | Login and register screens (FR/AR) | R-001 |
| FE-002 | frontend | Booking flow | R-002, R-003 |
| FE-003 | frontend | Receptionist calendar | R-005 |

Every requirement in the brief maps to at least one ticket. Here R-004 (email reminders) would get its own backend ticket once open question 1 is answered.

## Contract (excerpt)
```yaml
/slots:
  get:
    operationId: listSlots
    parameters:
      - {name: branchId, in: query, required: true, schema: {type: string}}
      - {name: dentistId, in: query, schema: {type: string}}
      - {name: date, in: query, required: true, schema: {type: string, format: date}}
    responses:
      "200":
        description: Available slots
        content:
          application/json:
            schema: {$ref: "#/components/schemas/SlotList"}
```

## What happens next
- Backend builds `/slots` and proves it with contract tests against this file.
- Frontend builds the booking screen against mocks generated from this same file.
- If the frontend finds that `/slots` needs a `duration` field, it files a Contract Change Request. It does not add the field itself.

The brief says what the client wants. The backlog says who builds what. The contract says exactly how the two sides talk to each other.
