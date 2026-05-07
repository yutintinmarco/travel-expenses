# Expenses Module UX Flow (Text Wireframe)

## A. Home / Trip Dashboard
- Header: Trip name, members, base currency.
- Primary CTA: `+ Add Expense` (sticky floating button, always visible on mobile).
- Secondary CTA: `Scan Receipt`.
- Cards:
  - Total spend
  - Per-member net (receive/pay)
  - Last 3 expenses
- Bottom nav:
  - Expenses
  - Summary
  - Activity
  - Settings

## B. Quick Add Expense
1. Open quick-add sheet.
2. Default date=today, payer=last used, currency=last used.
3. Enter amount + title.
4. Select participants (default all).
5. Save.

### Shortcuts (must be above fold)
- `Duplicate last`
- `Split equally`
- `Split custom`
- `Last payer`
- `Last currency`

## C. Scan Receipt Flow
1. Tap `Scan Receipt`.
2. Camera view + edge detection.
3. Preview capture.
4. AI extraction result sheet:
   - Merchant
   - Date
   - Amount
   - Currency
   - Suggested category
   - Confidence tag
5. User edits if needed.
6. Select payer/participants.
7. Save as expense.

## D. Expense List
- Default sort: newest first.
- Group by date sections.
- Each item shows:
  - title
  - original amount + currency
  - converted base amount
  - payer + participants count
- Swipe actions:
  - Edit
  - Delete
  - Duplicate

## E. Summary / Settlement
- Tab 1: Net by person.
- Tab 2: Suggested transfers (minimum transactions).
- Each transfer row:
  - `A pays B HKD xxx`
  - optional original-currency context.
- CTA: `Mark settled` (optional v1.1).

## F. Activity Log
- Reverse chronological feed:
  - `Marco edited Taxi amount from JPY 2000 to JPY 2200`
  - timestamp.
- Filter by member or expense.
- Restore deleted item action.

## G. Settings
- Trip base currency.
- Member management.
- Export CSV/PDF.
- Danger zone: archive trip.


## H. Hotel Split (Room/Night)
- Split mode selector:
  - Equal by participants
  - By room
  - By night
- By room flow:
  1. Add room blocks (Room A/B/...).
  2. Assign members per room.
  3. Enter subtotal per room.
  4. Choose tax/service fee allocation rule (equal or proportional).
- By night flow:
  1. Select check-in/check-out dates.
  2. Assign nights per member.
  3. Auto-calculate per-member share.
- Optional extras can be assigned to specific members only.

## I. OCR Failure Fallback
- If scan confidence is low, show fallback sheet with:
  - receipt image preview pinned top
  - amount/date/currency fields first
  - retry scan button
  - save manual entry CTA
- Target: manual correction + save within 20 seconds median.
