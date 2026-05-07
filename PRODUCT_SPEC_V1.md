# Expenses Module Product Spec v1 (Non-Technical)

## 1) Product Goal
Build a travel expenses module for small friend groups (2–5 people) that is faster and more enjoyable than existing split-bill apps.

### Success Definition
- People are willing to use it during a real trip.
- Input is fast, summary is trusted, and UI feels premium.

## 2) Target Users
- Primary: friend groups of 2–5 travelers.
- Use cases: meals, transport, hotel, shopping, tickets.
- Editing model: all members can edit all records.

## 3) Core Principles
1. **Fast entry first** (minimal taps).
2. **Always clear settlement** (no mental math).
3. **Full traceability** (edit history & restore).
4. **Mobile-first, beautiful UI**.

## 4) Scope (v1)
### In scope
- Create/edit/delete expense.
- Fields: date, title, amount, currency, payer, participants, category, note.
- Live sync across members.
- Net balance + suggested settlement.
- Multi-currency support (HKD + local currencies) using stored FX snapshot per entry.
- Receipt photo upload + AI extraction (merchant/date/amount/currency/category suggestion).
- Filters: by member, date range, category, currency.
- Activity log for edits.
- Undo delete / restore latest version.

### Out of scope (v1)
- Corporate approval flows.
- Complex role hierarchy.
- Desktop-first optimization.

## 5) UX Requirements
- First entry in under 3 minutes for a new user.
- Add a normal expense in <= 3 taps after opening quick-add.
- One-tap duplicate previous expense.
- Settlement screen must show:
  - who should pay whom,
  - amount in base currency,
  - original currency reference when applicable.

## 6) Multi-Currency Rules
- Trip has a base currency (default HKD).
- Each expense stores:
  - original amount + original currency,
  - fx rate snapshot at entry time,
  - converted base amount.
- Settlement calculation uses converted base amounts only.
- UI displays both original and converted values.

## 7) Permissions
- Any member can edit/delete any expense.
- Every update writes activity log entry:
  - actor, timestamp, before/after summary.
- Deleted items can be restored from history.

## 8) OCR / AI Receipt Entry
### v1 behavior
- User takes or uploads receipt photo.
- System extracts: merchant, date, total amount, currency.
- User confirms editable draft before save.
- Confidence indicator shown for uncertain fields.

### Acceptance target
- Merchant/date/amount extraction accuracy >= 85% on test set.

## 9) Metrics (KPI)
1. 20 expenses entered in <= 5 minutes (group test).
2. OCR auto-fill success >= 85% for key fields.
3. Settlement dispute rate = 0 in pilot groups.
4. User satisfaction >= 8/10.
5. Day-2 return rate >= 70% during active trip.

## 10) Release Plan
- **Pilot:** 2–3 friend groups, real trip usage.
- **Pilot duration:** 1–2 weeks.
- **Merge gate:** all KPI pass + no critical defects.
