# MOM app data request — Bangalore, by pincode

**To:** Miracle of Mind product / analytics
**From:** Suhruth (KA volunteer-movement vertical, MOM Bangalore December campaign)
**Date:** 31 July 2026
**Deadline that matters:** the grassroots plan needs in-app access to the Bangalore user base by **1 Nov 2026**. This request is the *read-only* precursor — it does not need the in-app messaging decision to be settled, and it should not wait for it.

---

## 1. Why this is being asked

The December campaign target is 10,000 active Bangalore volunteers. The 18 Bangalore centres cannot produce that number: ~35,978 active meditators (Ishangam, 10 Jul 2026) at the historical 3–8% volunteering conversion tops out around 2,000–2,800. The plan therefore assumes ~8,000 of the 10,000 come from the MOM app base, on the assumption of ~300–350K monthly Bangalore users and a 3% response.

**That assumption has never been checked against real data.** Nobody in the 30 July meeting had a Bangalore user count, let alone a pincode split. Before the volunteer arithmetic goes in front of anyone, we need to know whether the app base is 300K or 80K, and where in the city it sits.

The organising unit for the campaign is **pincode**, not centre catchment — roughly 100 captains, each holding one pincode. A pincode-level app count is what lets each captain be given a real number to work against.

---

## 2. What is being asked for

One CSV, one row per Bangalore pincode.

### Required

| Column | Definition |
|---|---|
| `pincode` | 6-digit Indian pincode, as stored on the user record |
| `mom_users` | Cumulative registered users whose location resolves to that pincode |
| `mom_active_30d` | Of those, users with ≥1 completed session in the last 30 days |

### Strongly wanted

| Column | Definition |
|---|---|
| `mom_sessions_30d` | Completed sessions in the last 30 days |
| `mom_minutes_30d` | Total minutes meditated in the last 30 days |
| `mom_new_30d` | New registrations in the last 30 days |
| `mom_engaged_30d` | Of the active users, those with **≥4** completed sessions in the last 30 days |

### The three activity tiers we will report against

Do not send a single "active" number — it will be the first thing challenged in the room. Send the components and we derive the tiers:

| Tier | Definition | Derived as |
|---|---|---|
| **Engaged** | ≥4 completed sessions in 30 days | `mom_engaged_30d` |
| **Active** | ≥1 completed session in 30 days | `mom_active_30d` |
| **Dormant** | registered, 0 sessions in 30 days | `mom_users − mom_active_30d` |

Volunteer recruitment realistically draws on **engaged**, not active — a user who meditated once in a month is not going to host a sit for ten people. If the engaged count is small, the 3% assumption is in trouble and we need to know that in August, not November.

### Nice to have (a second file is fine)

- The same five columns as a **monthly series for the last 6 months**, so we can see whether Bangalore is growing or flat, and set a defensible organic baseline for the December minutes target.
- A flag or separate rows for **users whose pincode is unknown/unresolved** — we need the size of that bucket, not for it to be silently dropped.

### Format

```
pincode,mom_users,mom_active_30d,mom_engaged_30d,mom_sessions_30d,mom_minutes_30d,mom_new_30d
560076,8420,3110,940,19800,152300,410
560100,7180,2540,780,15600,118400,362
UNKNOWN,41200,9800,2600,52100,391000,2100
```

Header row required; column order does not matter; extra columns are ignored.

---

## 3. Definitions we need pinned down before the numbers mean anything

Please state which convention the export uses. Different answers change the volunteer arithmetic by a factor of three or more.

1. **How is a user's pincode derived?** Self-declared at signup, device location, billing, or inferred? What share of Bangalore users have *any* pincode on record?
2. **What is a "user"?** Installs, registrations, or accounts with ≥1 completed session ever? The plan's 300–350K figure was described as "monthly users" — if that means MAU, `mom_users` and that figure are not the same thing and we should not treat them as such.
3. **Does "active" mean opened the app, or completed a session?** We want completed sessions.
4. **Are minutes actual meditated time or scheduled/session-length time?** For a 10-million-minutes public claim this has to be the former, and we need to be able to say so.
5. **Is the 30-day window rolling or calendar-month?** State the exact as-of date.

---

## 4. What no PII means here

Aggregate counts per pincode only. **No names, no phone numbers, no email addresses, no device IDs, no individual records.** If any pincode has fewer than, say, 10 users, suppress or bucket it rather than reporting a number that could identify someone. Nothing in this request needs user-level data.

The separate question of *messaging* those users in-app is a different ask with a different approval path — it is not bundled here, and this request should not be held up behind it.

---

## 5. What happens the moment this lands

The dashboard is already built and waiting: `mom-bangalore-dashboard.html`. It carries the pincode→centre backbone for 135 Bangalore pincodes across 15 centres, plus the Ishangam meditator baseline per pincode. Drop this CSV into it and it immediately produces:

- Bangalore app users, active users and minutes, by centre and by pincode
- Volunteers implied at the 3% planning assumption, per centre — the number each centre coordinator gets briefed on
- **App users per active meditator** per pincode — where the untapped pool actually is, as opposed to where Isha is already strong
- The white-space view: pincodes with a large app base and thin Isha presence, which is where captains are hardest to recruit and most needed

---

## 5b. One thing to settle on our side, not yours

The plan says **18 Bangalore centres**. Ishangam lists **15** for Bangalore urban (Banaswadi, Bangalore Rural, Bannerghatta Road, Budigere Cross, Electronic City, Girinagar, Hebbal, Indiranagar, Jayanagar, Kanakapura Road, Koramangala, Malleswaram, Marathahalli, Vijayanagar, Whitefield). Either three centres are missing from Ishangam, or the 18 counts sub-centres/FCs that Ishangam doesn't hold separately. This needs reconciling before any centre count is quoted publicly — it is a five-minute question for the regional team and it will otherwise get asked in the room.

---

## 6. Three questions the data will settle, that nothing else can

1. **Is 300–350K Bangalore users real?** If the true number is closer to 100K, 10,000 volunteers is 10% of the app base, not 3%, and the volunteer target has to be re-argued before it is announced.
2. **How many minutes does Bangalore already produce organically?** The working estimate is ~4M/month. The lever-by-lever bridge reaches 11.06M gross but only 7.06M incremental. If the real organic baseline is 6M, "10 million minutes in December" is a much smaller ask than it sounds — and we should know that before Sadhguru announces it, not after.
3. **Where are the users?** If the app base is concentrated in 15 pincodes, the 100-captain structure is over-built and should be re-cut. If it is spread evenly, the structure is right.

---

*Prepared alongside `mom-bangalore-grassroots-plan.md` and `mom-bangalore-phase-plan.md`, ISHA KA / MOM Banglore Movement.*
