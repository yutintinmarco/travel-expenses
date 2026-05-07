# Expenses Module — Solo Plan (1-page)

## 0) Product outcome (what success means)
Build a travel expenses module that 2–5 friends are happy to use during real trips.

### Must-hit outcomes
- 20 entries in <= 5 minutes.
- OCR success (merchant/date/amount/currency) >= 85%.
- OCR failure still finishable via manual mode (>=98% completion, <=20s median correction).
- Users rate >= 8/10.

---

## 1) MVP scope (build first)
1. Fast add/edit/delete expense (mobile-first)
2. Multi-currency with **manual custom FX** per expense
3. Settlement summary (who pays whom) in base currency
4. Hotel split:
   - equal split
   - by room
   - by night
5. OCR receipt draft + fallback manual correction

---

## 2) Non-negotiable UX rules
- 3-click quick entry for common expenses
- Above-the-fold shortcuts:
  - Duplicate last
  - Split equally
  - Last payer
  - Last currency
- Amount is visually most prominent in expense row
- Primary add action always visible on mobile

---

## 3) Two-week execution
### Week 1 (Core engine)
- CRUD polish + validation
- custom FX data model + conversion
- settlement correctness
- hotel split (equal/room/night)

**Done when**
- Mixed HKD+JPY test cases stable
- No settlement math errors in test sheet

### Week 2 (OCR + usability)
- receipt scan draft
- fallback manual mode + retry scan
- shortcuts + speed polish
- pilot with 2–3 friend groups

**Done when**
- OCR targets met
- 20 entries <= 5 min achieved

---

## 4) What NOT to do now
- complicated roles/approvals
- enterprise workflows
- desktop-first redesign
- too many charts before core speed is proven

---

## 5) Weekly check-in template (5 minutes)
- What shipped this week?
- What blocked me?
- One decision needed next week?
- Keep / Cut / Add (one item each)
