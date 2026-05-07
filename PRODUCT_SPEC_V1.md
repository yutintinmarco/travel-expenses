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
- Multi-currency support (HKD + local currencies) using **manual custom exchange rates** captured per entry.
- Receipt photo upload + AI extraction (merchant/date/amount/currency/category suggestion) with fallback and manual correction path.
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

## 5A) "Good UI" Definition
- **3-click entry rule**: returning users can save a common expense within 3 interactions from quick-add.
- **Common shortcuts** must be visible above fold:
  - Duplicate last expense
  - Split equally
  - Last payer
  - Last currency
- **Visual clarity rules**:
  - primary action always sticky/visible,
  - amount is highest visual priority in list rows,
  - settlement card appears before long history list on mobile.
- **Delight baseline**:
  - animation response < 200ms for primary interactions,
  - no blocking spinner for normal add/edit flows.

## 6) Multi-Currency Rules
- Trip has a base currency (default HKD).
- Each expense stores:
  - original amount + original currency,
  - fx rate snapshot at entry time,
  - converted base amount.
- Settlement calculation uses converted base amounts only.
- UI displays both original and converted values.


## 6A) Hotel Room Split Rules (Detailed)
- Expense type `Hotel` supports 3 split modes:
  1. **Equal by participants**: total / selected participants.
  2. **By room**: each room has assigned members and room subtotal.
  3. **By night**: each member pays proportional nights stayed.
- Service fee/taxes can be:
  - distributed equally, or
  - distributed by room subtotal ratio.
- Optional extras (mini-bar, breakfast, late check-out) can be tagged to specific members only.
- Settlement engine merges hotel split result with other expenses into final base-currency net balances.

## 6B) Manual FX Rules (Custom Exchange Rate)
- Trip owner sets a default reference rate table per currency pair (e.g., JPY->HKD).
- Each expense stores:
  - original amount/currency,
  - **custom rate value entered or confirmed by user**,
  - converted base amount.
- User can choose rate source at entry:
  - `Use trip default rate`, or
  - `Override with custom rate for this expense`.
- Historical records remain immutable: changing trip default rate does not alter existing converted amounts.

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

### OCR failure fallback
- If OCR confidence is low or parsing fails:
  1. Show `Could not read clearly` notice.
  2. Pre-fill only safe fields (if any).
  3. Open manual entry mode with image pinned on top for quick reference.
  4. Offer one-tap `Retry Scan`.

### Manual correction speed target
- From failed OCR to successful save should be <= 20 seconds median in usability tests.
- Keyboard focus defaults to amount field in manual mode.
- Frequently corrected fields (amount/date/currency) appear first.

### Acceptance target
- Merchant/date/amount extraction accuracy >= 85% on test set.
- Fallback completion success rate >= 98% (user can always finish entry).

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
