# Project Brief: Atlas Clinic Booking

> **Example only.** Fictional client, filled in so you can see what a good brief looks like. Copy `briefs/_TEMPLATE/brief.md` for real projects. Walkthrough: `walkthrough.md`.

- Client: Atlas Dental Clinic (3 branches, Agadir)
- Date received: 2026-10-06
- Status: clarifying
- Client sign-off: pending

## 1. Goal
Patients book, reschedule and cancel appointments online, so the reception team spends less time on phone calls. Target: 60% of bookings online within 3 months.

## 2. Users & roles
| Role | What they need to do |
|---|---|
| Patient | Browse dentists and slots, book, reschedule, cancel, get SMS or email confirmation |
| Receptionist | See the day's calendar per branch, add walk-ins, block slots |
| Admin (clinic owner) | Manage dentists, branches and working hours; see monthly stats |

## 3. Requirements
| ID | Requirement | Priority (must/should/could) |
|---|---|---|
| R-001 | Patient registers and logs in (email and password) | must |
| R-002 | Patient picks branch, dentist and an available slot | must |
| R-003 | Patient cancels or reschedules up to 24h before the appointment | must |
| R-004 | Email confirmation and a reminder 24h before | must |
| R-005 | Receptionist calendar view per branch and day | must |
| R-006 | Admin manages dentists, branches and working hours | should |
| R-007 | Monthly stats dashboard | could |
| R-008 | SMS reminders | could |

## 4. Non-functional
- French and Arabic (RTL), mobile-first
- Patient data is personal health information: Moroccan data-protection rules apply. Encrypt it and log access.
- Pages load in under 3s on 4G. Target 99.5% uptime.
- Last 2 versions of Chrome, Safari and Edge.

## 5. Integrations & data
- Email via the client's existing provider (to confirm)
- Import of about 2,000 existing patients from an Excel file

## 6. Design inputs
Brand guide and Figma link from the Brand Manager go in `frontend/design/handoff.md`. Not received yet.

## 7. Out of scope
Online payment, medical records, a mobile app, patient-to-dentist chat.

## 8. Open questions
| # | Question | Owner | Answer | Resolved |
|---|---|---|---|---|
| 1 | Which email provider, and who owns the account? | Client | | no |
| 2 | Do patients need ID or insurance details at registration? | Client | | no |
| 3 | Are SMS reminders in the first release? | Client | | no |
| 4 | How long is data retained? | Client legal | | no |

## 9. Deadlines & budget
Launch on 2026-12-15, in time for the pilot at one branch. Budget: fixed, amount to confirm.
