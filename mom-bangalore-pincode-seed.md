# Pincode seed for the Bangalore MOM on-ground movement

**Prepared:** 31 July 2026 · **Source:** Ishangam `miracle.of.mind` joined to `res.partner.zip`, queried 31 Jul 2026
**Companion files:** `mom-bangalore-captain-seed.csv` (the working roster), `mom-bangalore-dashboard.html` (the live view)

---

## What this replaces

The grassroots plan assumed ~100 pincode captains, each holding one pincode, with no data behind the allocation. This seeds that structure with real numbers: **135 Bangalore pincodes, each with an app-user estimate, an active-meditator count, and a volunteer target that sums to the campaign's 10,000.**

## How the numbers were built

Ishangam's `ip_pincode` field is IP geolocation and unusable — every Bengaluru record carrying it shows the same value. The real pincodes come from a different route: **76,002** of the 128,393 centre-assigned Bangalore MOM records carry a `contact_id_fkey` link to a contact record, and **71,750** of those resolve to one of the 135 Bangalore pincodes.

That is **24% of the 293,569-user Bengaluru base**. So:

- **Ranking is trustworthy.** Which pincodes are dense and which are thin is based on 71,750 real observations.
- **Absolute counts are not.** The `mom_users_estimated` column distributes the full 293,569 across pincodes using the matched sample's shape. That assumes matched users are geographically representative of unmatched ones. Matched users are people Isha already holds a contact record for, so this assumption is doing real work and should be stated whenever the number is quoted.
- **Volunteer targets** = 3% of the estimate, per the grassroots plan's assumption. They sum to **8,806**, not 10,000 — the shortfall is deliberate and discussed below.

`562114` (Hoskote) is excluded from the allocation: it shows 7,073 matched users against 117 active meditators, a ratio 30× the city norm, and traces to the same bulk load that inflates Budigere Cross. Verify it before letting it back into any plan.

---

## The finding that should change the structure

**20 pincodes carry half the target. 48 carry 80%. The remaining 87 carry 1,818 between them.**

| Tier | Pincodes | Volunteer target | Share |
|---|---|---|---|
| **Tier 1** | 20 | 4,304 | 49% |
| **Tier 2** | 28 | 2,684 | 30% |
| **Tier 3** | 87 | 1,818 | 21% |

A flat 100-captain structure spends the same recruiting effort on a pincode worth 12 volunteers as on one worth 369. **Recommendation: staff Tier 1 with dedicated full-time captains and a cell-leader layer beneath each; run Tier 2 with one captain per pincode; cluster Tier 3 into ~15 multi-pincode captaincies.** That is roughly 63 captains instead of 100, with the saved capacity redeployed into Tier 1 depth — where the volunteers actually are.

### Tier 1 — the twenty that matter

| Pincode | Area | Centre | Est. MOM users | Active meditators | App/meditator | Target |
|---|---|---|---|---|---|---|
| 560076 | Bilekahalli / Bannerghatta Rd | Bannerghatta Road | 12,305 | 1,456 | 8.5 | 369 |
| 560068 | Bommanahalli / Singasandra | Electronic City | 10,526 | 1,272 | 8.3 | 316 |
| 560078 | JP Nagar | Bannerghatta Road | 10,490 | 1,221 | 8.6 | 315 |
| 560037 | Marathahalli | Marathahalli | 9,868 | 1,368 | 7.2 | 296 |
| 560064 | Yelahanka | Hebbal | 9,595 | 1,322 | 7.3 | 288 |
| 560100 | Electronic City | Electronic City | 9,364 | 1,308 | 7.2 | 281 |
| 560043 | Kalyan Nagar / HBR Layout | Banaswadi | 8,860 | 1,115 | 7.9 | 266 |
| 560066 | Whitefield | Whitefield | 7,803 | 1,150 | 6.8 | 234 |
| 560061 | Uttarahalli / Subramanyapura | Kanakapura Road | 6,582 | 790 | 8.3 | 197 |
| 560102 | HSR Layout | Koramangala | 6,091 | 950 | 6.4 | 183 |
| 560085 | Banashankari III / Girinagar | Girinagar | 6,055 | 674 | 9.0 | 182 |
| 560097 | Vidyaranyapura | Hebbal | 5,991 | 699 | 8.6 | 180 |
| 560016 | Ramamurthy Nagar / Dooravani Nagar | Banaswadi | 5,765 | 689 | 8.4 | 173 |
| 560067 | Kadugodi | Marathahalli | 5,252 | 734 | 7.2 | 158 |

The remaining six Tier 1 pincodes are in the CSV. Every one of these is an apartment-dense corridor, which lines up with the plan's own yield ranking — apartment/RWA cells first.

---

## How to use the CSV

`mom-bangalore-captain-seed.csv`, one row per pincode, sorted by tier then target. Three columns are deliberately blank — `captain_name`, `captain_phone`, `status` — because filling them is the actual Phase 1 work. Suggested sequence:

1. **Tier 1 first, this week.** 20 names. Pull candidates from the centre nearest each pincode; the `centre` column tells you which coordinator to ask.
2. **Set `status` to `named` → `briefed` → `active`.** One column, three states, no new tooling.
3. **Tier 2 through August.** 28 more.
4. **Tier 3 as clusters in September**, not as 87 individual asks.

The `app_per_active_meditator` column is the argument to hand each captain: at 8.5, pincode 560076 has eight and a half app users for every active meditator in it. Their recruiting pool is not the centre — it is the eight.

---

## Three things this seed does not solve

**The target still does not close.** Targets sum to 8,806 against 10,000, and that is at 3% of the *whole* app base. Only 170,776 of 293,569 Bengaluru users have a phone number on record; 3% of the contactable subset is 5,123. Adding the centre ecosystem's realistic ceiling of 2,736 gives **7,859**. In-app notification — reaching the ~123,000 users with no phone on record — is what closes the gap. That makes the 1 Nov in-app access date a hard dependency on the critical path, not a nice-to-have.

**Activity is still unknown.** Ishangam holds no sessions, minutes or last-active data. Every "user" in this seed is a registration, which may be someone who opened the app once in 2025. Until MOM core supplies usage, the tiering ranks *registration density*, not *engaged-user density*, and those may not be the same map. This is the single highest-value thing still outstanding — see `mom-app-data-request.md`.

**The 3% assumption is unvalidated.** It came from the grassroots plan and nothing in Ishangam confirms it. If the true response rate is 1.5%, every target in this seed halves and the structure needs re-cutting. Worth pressure-testing on Tier 1 in August, while there is still time to change course.

---

*Prepared alongside `mom-bangalore-grassroots-plan.md` and `mom-bangalore-phase-plan.md`, ISHA KA / MOM Bangalore Movement.*
