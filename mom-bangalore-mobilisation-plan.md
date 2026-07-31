# Bangalore volunteer mobilisation plan

**10,000 active volunteers by 1 December 2026** · Prepared 31 July 2026 · 18 weeks to go
**Owner:** Suhruth & Santosh (volunteer movement vertical) · **Data:** Ishangam `miracle.of.mind`, queried 31 Jul 2026

> **Relationship to `mom-volunteer-mobilisation-plan.md`.** That document is the plan of record from the 31 July morning call: captains build persistent *teams*, potential meditators count, schools scale to 300–500, and the December minutes arithmetic is correspondingly larger. **This document is the data-driven counterpart**, built from Ishangam records. It models a volunteer as one person hosting one seven-minute sit, which is the *conservative* case. Where the two disagree, the team construct is newer and should win — but the pincode tiers, the pin-charge candidate lists and the risks below apply to both, because they come from the data rather than the construct.

---

## 1. What a volunteer is

**One person who hosts one seven-minute sit for ten people.** About an hour of total commitment, no leave applied for, no training weekend.

This definition is the plan. On the Yoga-Veera definition of a volunteer, 10,000 in eighteen weeks is fantasy. On this one it is roughly 3% of the Bangalore Miracle of Mind base, which is a number the city has plausibly hit before. Every figure below depends on holding this line — the moment "volunteer" quietly reverts to meaning someone who gives weekends, the plan fails silently and nobody notices until November.

---

## 2. Where the 10,000 come from

| Pool | Active volunteers | Basis |
|---|---|---|
| Tier 1 pincodes (20) | 4,304 | 3% of estimated MOM base |
| Tier 2 pincodes (28) | 2,684 | 3% of estimated MOM base |
| Tier 3 pincodes (87) | 1,818 | 3% of estimated MOM base |
| Consecration harvest, IE closings, walk-ins | 1,194 | event capture, not pincode-driven |
| **Total** | **10,000** | |

The first three lines come from the pincode seed and sum to 8,806. The residual, 1,194, lands almost exactly on the 1,200 the grassroots plan already assigned to event capture — the two methods agree, which is the first independent check this target has had.

### The arithmetic error to fix first

The existing plan says: assume 40% attrition, therefore sign up ~14,000. **Those two numbers do not go together.** 14,000 at 40% attrition yields 8,400 active, not 10,000. To hold 10,000 on 1 December at 40% attrition you must sign up **16,700**.

The plan is currently under-recruiting by roughly 2,700 people, and the error compounds every week it goes unfixed because it is baked into every downstream tier target. Either raise the signup target to 16,700 or state explicitly that attrition is assumed at 28.6%, which is a much more optimistic claim than anyone in the room has defended.

**This plan uses 16,700.**

| Pool | Active target | Signups needed @40% attrition |
|---|---|---|
| Tier 1 | 4,304 | 7,173 |
| Tier 2 | 2,684 | 4,473 |
| Tier 3 | 1,818 | 3,030 |
| Event capture | 1,194 | 1,990 |
| **Total** | **10,000** | **16,700** |

---

## 2b. The pin-charge layer already exists — call it, don't build it

The plan of record asks for ~135 pin-charges and identifies the right way to find them: people who have *already, unprompted, with no campaign and no incentive, got others onto the app*. That list is now extracted.

| Signal | Count |
|---|---|
| Bangalore MOM users who have referred **≥1** person | 3,516 |
| Who have referred **≥3** — the pin-charge shortlist | **1,088** |
| Pincodes with **≥3** candidates | 87 of 135 |
| Pincodes with **zero** candidates | 26 |
| **Tier 1 pincodes with fewer than 5 candidates** | **none** |

Every one of the twenty Tier 1 pincodes has at least five people who have already demonstrated exactly the behaviour the campaign is trying to manufacture. The top of the list runs 46 candidates in 560100 Electronic City, 43 in 560078 JP Nagar, 38 in 560064 Yelahanka, 36 each in 560037 Marathahalli and 560043 Kalyan Nagar.

This compresses Stage 1 from a six-week search into a weekend of phone calls. The 26 pincodes with no candidates are flagged in the seed CSV and must be sourced from the nearest centre instead.

**Pulling the actual call list:** filter `miracle.of.mind` in Ishangam on `record_center` = the centre and `total_referred >= 3`, sorted descending. Names and numbers stay inside Ishangam — no personal data is held in the dashboard, the CSV, or the repository, deliberately.

---

## 3. The structure

**63 captains, not 100.** Twenty pincodes carry half the target; 87 carry a fifth between them. A flat grid spends identical effort on a pincode worth 12 volunteers and one worth 369.

```
        63 captains          →   ~950 cell leaders   →   16,700 signed hosts   →   10,000 active
   20 Tier 1  (15 leaders ea)      300
   28 Tier 2  (12 leaders ea)      336                    ~18 hosts per cell leader
   15 Tier 3  (20 leaders ea)      300      clusters of ~6 pincodes each
```

Tier 1 captains are full-time equivalents with a cell-leader layer beneath them. Tier 2 is one captain per pincode. Tier 3 is clustered — one captain covering roughly six low-density pincodes — because the alternative is 87 people each recruiting twenty volunteers, which is 87 relationships to manage for a fifth of the target.

**Cell types, in yield order:** apartment/RWA → workplace → campus → street → school-parent → affinity groups. Every Tier 1 pincode is an apartment-dense corridor, which is why RWA-first is the default opening move and not a preference.

---

## 4. The eighteen weeks

### Phase 0 — Harvest and spine · 1–17 August

The consecration brings roughly 2,000 volunteers to Bangalore on e-passes. **Capture their intent at the event, before they disperse.** This is the single most time-critical item in the whole plan and it does not depend on the note to Sadhguru being approved, the cause name being locked, or the platform existing. A clipboard and a QR code are sufficient.

- Capture 700 signed intents from the consecration cohort
- Name all 20 Tier 1 captains from the seed roster — the `centre` column tells you which coordinator to ask
- Cause name locked by 10 Aug *(dependency: cause & communication track)*

**Gate:** 20 Tier 1 captains named by 17 Aug. If fewer than 15, the timeline slips and you need to know in August.

### Phase 1 — Tier 1 build · 18 August – 15 September

Centre briefings begin in the second half of August — the Rally for Rivers precedent is three to four months of lead time, and December is four months out. Later than this and the centre layer never engages.

- 20 Tier 1 captains briefed and active
- 300 Tier 1 cell leaders recruited
- **First real sits happen in this phase.** Not a pilot, not a rehearsal — actual seven-minute sits with actual strangers, so the model is proven before it is scaled
- Cumulative signups: **2,500**

**Gate — 15 September:** measure the actual response rate on Tier 1 outreach. The whole plan rests on 3%, which is an assumption nobody has tested. If the real number is 1.5%, every target above halves and the structure needs re-cutting while there is still time.

### Phase 2 — Tier 2 and platform · 16 September – 15 October

- Platform live 30 Sep *(dependency: product/campaign platform track)*
- 28 Tier 2 captains named and briefed; 336 cell leaders
- World Mental Health Day, 10 Oct — first public seeding moment
- Cumulative signups: **6,500**

### Phase 3 — Tier 3 and the app push · 16 October – 15 November

- 15 Tier 3 cluster captains; 300 cell leaders
- **In-app notification access by 1 Nov** *(dependency — see risk 1; this is the volume lever)*
- The bulk of recruitment lands here. Roughly 6,500 signups in four weeks
- Cumulative signups: **13,000**

### Phase 4 — Activation and drill · 16–30 November

- Remaining 3,700 signups
- **Every host completes one practice sit before 1 December.** This is the anti-attrition mechanism, not a nice-to-have
- Public announcement, late November
- **16,700 signed → 10,000 active on 1 Dec**

### Phase 5 — Run · 1–31 December

---

## 5. The death zone, and the three things that fix it

Yoga Veera went 1,000 signed → 350 trained → **60 who actually did it**. The loss is not at signup and not at training. It is between being trained and doing it once.

Three mechanisms, all cheap, all non-negotiable:

1. **First sit within 7 days of signup, with the cell leader physically present.** The gap between joining and doing is where people leave. Close it to a week and most of the attrition never happens.
2. **A human call within 48 hours of signup.** Not a WhatsApp broadcast. A person.
3. **Visible attribution from day one.** Every host sees their own minutes counted, from their first sit — not a city total they cannot locate themselves in.

**The metric that matters weekly is not signups. It is the share of new hosts who complete a first sit within seven days.** If that number is below 50%, recruiting faster makes the problem worse, not better — you are filling a bucket with a hole in it.

---

## 6. Four risks that can kill this

**1 · In-app access slips past 1 November.** Only 170,776 of 293,569 Bengaluru MOM users have a phone number on record. Reaching the other ~123,000 requires in-app notification. Without it the realistic ceiling is 7,859 — centres at 2,736 plus 3% of the contactable base at 5,123 — and 10,000 is unreachable by any amount of effort on the ground. *This is not a dependency on the critical path; it is the critical path.* Escalate in the first week of August, not October. Parallel mitigation: begin phone outreach to the contactable 170,776 in Phase 1 rather than waiting.

**2 · The 3% response rate is wrong.** It is a planning assumption carried from the grassroots plan; nothing in Ishangam validates it. Test on Tier 1 in August, decide 15 September.

**3 · Registration density is not engagement density.** Ishangam holds no sessions, minutes or last-active data, so the tiering ranks *registrations*, which may include people who opened the app once in 2025. Pincode 562114 shows 7,073 users against 117 active meditators — a bulk-load artefact, already excluded, but only because it was large enough to see. Smaller ones are in there. Chase the usage data from MOM core.

**4 · The definition drifts.** If "volunteer" quietly reverts to meaning someone who gives weekends, every number in this plan is wrong and nobody will notice until November. Write the one-sit definition into the captain brief and the signup form.

---

## 7. Weekly operating cadence

| When | What | Who |
|---|---|---|
| Monday | Captain call — tier by tier, 30 min | Suhruth / Santosh |
| Wednesday | Data refresh from Ishangam; dashboard updated | Suhruth |
| Friday | Tier review — gaps, reallocations, escalations | Suhruth / Santosh |

**Track five numbers, weekly:**

1. Captains named → briefed → active
2. Cell leaders recruited
3. Hosts signed, cumulative against the curve
4. **First sit within 7 days — %** *(the leading indicator; everything else is lagging)*
5. Tier 1 response rate against the 3% assumption

---

## 8. Immediate actions, this week

| # | Action | By |
|---|---|---|
| 1 | Escalate the 1 Nov in-app access date — it gates the whole plan | 5 Aug |
| 2 | Fix the 14,000 → 16,700 signup arithmetic in the grassroots plan | 5 Aug |
| 3 | Stand up consecration intent capture — clipboard and QR, no approvals needed | before the event |
| 4 | Name the 20 Tier 1 captains from the seed roster | 17 Aug |
| 5 | Reconcile the centre count: plan says 18, Ishangam has 15, only 14 carry MOM records | 10 Aug |
| 6 | Send the usage data request to MOM core | 5 Aug |

---

*Companion files: `mom-bangalore-dashboard.html` (live view, both seeds embedded), `mom-bangalore-captain-seed.csv` (the roster), `mom-bangalore-pincode-seed.md` (method), `mom-bangalore-grassroots-plan.md`, `mom-bangalore-phase-plan.md`. ISHA KA / MOM Bangalore Movement.*
