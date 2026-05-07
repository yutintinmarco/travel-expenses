# Expenses Module Delivery Milestones (Weekly, Reviewable)

## Week 1 — Foundation + UX polish
### Deliverables
- Stable CRUD (create/edit/delete) with validation.
- Fast quick-add interactions.
- Improved list readability and mobile spacing.
- Trip/member dynamic config (remove hardcoded trip/members).

### Review checklist
- Add/edit/delete works across 2 test devices.
- No data loss during refresh.
- New user can add first entry in <= 3 minutes.

## Week 2 — Multi-currency engine (manual custom FX)
### Deliverables
- Base currency per trip.
- Expense stores original + converted amount + user-defined custom fx rate.
- Per-expense override of trip default custom rate.
- Summary/settlement computed from base amounts.
- UI shows original and converted values.

### Review checklist
- HKD + JPY mixed entries produce stable settlement.
- Re-opening app does not change historical converted amounts.

## Week 3 — OCR receipt input + fallback speed
### Deliverables
- Receipt photo upload/capture flow.
- AI extraction draft form with confidence badges.
- User confirmation before save.
- Failure fallback path with retry + manual correction mode.

### Review checklist
- 30-receipt test set achieves >=85% accuracy for date/amount/currency.
- Failed extraction fallback completion >=98%.
- Manual correction median time <=20 seconds.

## Week 4 — Trust features + hotel split + pilot readiness
### Deliverables
- Activity log for all edits/deletes.
- Restore deleted records.
- Hotel split rules (room/night/equal) production-ready.
- Filters + export (CSV at minimum).
- Pilot instrumentation (basic usage metrics).

### Review checklist
- All edits traceable by member and time.
- Pilot groups can finish full trip bookkeeping without blockers.

## Merge Gate (to main travel webapp)
Ship merge only if all conditions pass:
1. No critical bugs (data corruption, wrong settlement).
2. KPI targets met:
   - 20 entries <= 5 min
   - OCR >=85%
   - Satisfaction >=8/10
3. UX sign-off from pilot users.
