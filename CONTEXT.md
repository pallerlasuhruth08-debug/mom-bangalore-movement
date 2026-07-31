# CONTEXT — MOM Bangalore data work, 31 July 2026

Working record of the session that produced the dashboard, the pincode seed and the captain seed. Written so someone picking this up cold — or a future assistant session — can resume without re-deriving anything.

---

## 1. What was asked, and what actually happened

The ask started as *"dashboard of MOM app users by pincode and centre, including active users, the data is in Ishangam."*

It went through three corrections, all of which matter more than the dashboard:

| # | What was believed | What is true |
|---|---|---|
| 1 | Ishangam has no Miracle of Mind data (based on the Santosha Software Guide, which documents none) | **Wrong.** Model `miracle.of.mind` exists with 2,392,695 records. Suhruth was right, twice. |
| 2 | `ip_pincode` gives pincode-level segmentation | **Wrong.** It is IP geolocation to a city centroid. All 81,465 Bengaluru records carrying it share one value, 562114. Nationally the top values are 110001 / 400017 / 411001 — GPO centroids. |
| 3 | Therefore pincode segmentation is impossible | **Also wrong.** Real pincodes come from `contact_id_fkey` → `res.partner.zip`. 76,002 matched records, 71,750 resolving to a Bangalore pincode. |

**The one thing that remains true:** there is no activity data anywhere in Ishangam. No sessions, no minutes, no last-active. "Active app users" is still unanswerable and still requires MOM core.

---

## 2. How to query the data again

Ishangam Odoo, `https://ishangam.isha.in`, model **`miracle.of.mind`**, menu_id 139, action 2169. JSON-RPC via `/web/dataset/call_kw` — same recipe as `ka-centers-dashboard/OPERATION-PLAYBOOK.md` §2.

```js
const call=(m,me,a,k)=>fetch('/web/dataset/call_kw',{method:'POST',
  headers:{'Content-Type':'application/json'},
  body:JSON.stringify({jsonrpc:'2.0',method:'call',
    params:{model:m,method:me,args:a,kwargs:k||{}}})}).then(r=>r.json());
```

### Gotchas, all hit and solved

- **`center_id` is computed, not stored** — `read_group` rejects it. Group on **`record_center`** (char, stored).
- **`res.partner.read()` on large id lists throws `AccessError`.** Use `search_read` with `[['id','in',chunk]]` instead — it silently drops the ~2% withheld by record rules rather than failing. Chunk at 2,500.
- **`zip` can be the literal string `"NULL"`.** Validate with `/^\d{6}$/`.
- **The browser JS bridge loses `window` state between executions** and truncates returned output at roughly 2–3 KB. Page ~10,000 records per call and return compact fixed-order arrays, not objects with string keys.
- Returning long colon-delimited strings gets blocked as cookie-like data. Return JSON.

### Fields worth knowing

`record_center` · `is_meditator` · `record_phone` · `first_login_ts` (registration, not activity) · `opt_in` · `dnd` · `total_referred` · `was_referred` · `referred_by` · `contact_id_fkey` → res.partner · `mom_sso_id` · `match_type` (N = no match, H/L/C = match confidence).

`active` is Odoo's archive flag — all 2,392,695 records are `true`. It does **not** mean app-active. Do not use it.

Related models: `mom.referral.summary` (11,578 rows, daily referral counts by centre/region) and `mom.date.region.referral.summary`.

---

## 3. The numbers

All queried 31 Jul 2026. Bengaluru = `ip_city = 'Bengaluru'` (note: `'Bangalore'` returns zero).

| Metric | Value | Note |
|---|---|---|
| MOM users, Bengaluru | **293,569** | the plan's "300–350K" holds, at the low end |
| Not flagged as Isha meditators | **262,778 (89.5%)** | the strongest number in the argument |
| Phone number on record | 170,776 (58%) | the contactable base |
| On DND | 417 (0.1%) | outreach is not the constraint; reach is |
| Mapped to a centre | 126,737 (43%) | |
| Signed up in 2026 | 26,859 | 3,827 in July alone |
| Active meditators (Ishangam baseline) | 34,206 | 14 Bangalore centres, snapshot 10 Jul 2026 |
| Referred ≥1 person | 3,516 | |
| Referred ≥3 — pin-charge shortlist | **1,088** | |

### The volunteer arithmetic

- Centres at the historical 3–8% conversion: **1,026–2,736**. Reaching 10,000 from centres alone needs 29% of every active meditator in the city.
- App base @3% of all 293,569: **8,807**. Plan closes.
- App base @3% of the *contactable* 170,776: **5,123**.
- **Realistic ceiling without in-app notification: 2,736 + 5,123 = 7,859.** Short of 10,000.
- Therefore **in-app access by 1 Nov is the critical path**, not a dependency on it.

### Pincode tiers

20 pincodes carry half the target, 48 carry 80%, 87 carry the remaining fifth.

| Tier | Pincodes | Volunteer target |
|---|---|---|
| 1 | 20 | 4,304 |
| 2 | 28 | 2,684 |
| 3 | 87 | 1,818 |
| Event capture (non-pincode) | — | 1,194 |
| **Total** | **135** | **10,000** |

The 1,194 residual independently matches the 1,200 the grassroots plan had already assigned to consecration / IE closings / walk-ins. Two methods agreeing is the first external check the target has had.

**Method for the estimate:** each pincode's share of the 71,750-record matched sample, applied to the 293,569 city base. Reliable *shape*, unreliable *magnitude* — it assumes matched users (people Isha already holds a contact record for) live where unmatched ones do.

---

## 4. Data-quality artefacts — exclude these

- **`Karnataka – Others`**: 146,906 records, more than every named Bangalore centre combined. Roughly half the Karnataka base is unassigned to any centre.
- **Budigere Cross / pincode 562114 (Hoskote)**: 17,610 users, 100% first-logged-in during 2026, 8,320 since May, against only 170 meditators. At pincode level, 7,073 matched users against 117 active meditators — a ratio 30× the city norm. A bulk load or single campaign, not organic growth. Excluded from every ranking and allocation. **Verify before letting it back in.**
- Smaller artefacts of the same kind are almost certainly present and were not large enough to detect.

---

## 5. Decisions taken during the session

| Decision | Rationale |
|---|---|
| Lead with *app users per active meditator*, not total users | Totals restate an assumption already in the plan; the ratio shows where the centre system cannot reach, which is the actual argument for organising by pincode |
| Cut the captain structure from 100 to ~63 | 20 pincodes carry half the target; a flat grid spends identical effort on a pincode worth 12 and one worth 369 |
| Source pin-charges from existing referrers rather than recruiting them | 1,088 people already do this unprompted; every Tier 1 pincode has ≥5 |
| **No personal data in any deliverable** | The dashboard, CSV and repo hold counts only. Names and phone numbers stay inside Ishangam — pull the call list there with `total_referred >= 3` |
| Keep both mobilisation plans, separate | User's call. `mom-volunteer-mobilisation-plan.md` (team construct, from the 31 Jul morning call) is the plan of record; `mom-bangalore-mobilisation-plan.md` is the conservative data-driven counterpart |
| Signup target 16,700, not 14,000 | 14,000 at 40% attrition yields 8,400, not 10,000 — see below |

---

## 6. Open items

1. **The 14,000 signup figure is arithmetically wrong.** 40% attrition on 14,000 gives 8,400 active. To hold 10,000 you need 16,700. The plan is under-recruiting by ~2,700 and the error is baked into every downstream tier target. Fix or restate the attrition assumption.
2. **Centre count: plan says 18, Ishangam lists 15, only 14 carry MOM records.** Kanakapura Road returns zero under that name. Reconcile before quoting a centre count publicly.
3. **The 3% response rate is unvalidated.** Carried from the grassroots plan; nothing in Ishangam confirms it. Test on Tier 1 in August, decide by 15 September.
4. **Usage data still outstanding from MOM core** — sessions, minutes, last-active, and a true pincode. See `mom-app-data-request.md`. Without it the tiering ranks *registration* density, not *engagement* density, and those may be different maps.
5. **In-app access by 1 Nov** — escalate in the first week of August, not October.

---

## 7. Files

| File | What it is |
|---|---|
| `mom-bangalore-dashboard.html` | Five-tab dashboard, self-contained, data embedded. The argument · mobilisation plan · pincode seed · captain seed (with CSV download) · data & limits |
| `mom-bangalore-captain-seed.csv` | 135-row roster, sorted by tier then target. `pin_charge_name` / `pin_charge_phone` / `status` deliberately blank — that is the Phase 1 work |
| `mom-bangalore-pincode-seed.md` | Method behind the pincode layer, tier table, Tier 1 list |
| `mom-bangalore-mobilisation-plan.md` | Data-driven plan (conservative, one-sit model) |
| `mom-volunteer-mobilisation-plan.md` | **Plan of record** — team construct from the 31 Jul morning call |
| `mom-app-data-request.md` | The ask to MOM core, narrowed to usage + true pincode |
| `mom-bangalore-grassroots-plan.md`, `mom-bangalore-phase-plan.md`, `mom-bangalore-meeting-2026-07-30.md`, `mom-captain-incentives.md` | Pre-existing planning documents |

**Most time-critical item across all of them:** the consecration harvest. ~2,000 volunteers arrive on e-passes in early August. Capture intent at the event, before 17 Aug, without waiting for the note to Sadhguru to be approved. A clipboard and a QR code are sufficient.
