# MOM Bangalore — volunteer mobilisation

Data and planning artefacts for the Miracle of Mind Bangalore on-ground movement.
**Target: 10,000 active Bangalore volunteers by 1 December 2026**, feeding the ~10 million minutes December campaign.

## Start here

- **[`CONTEXT.md`](CONTEXT.md)** — how the data was obtained, what is trustworthy, what is not, and every open item. Read this first.
- **`mom-bangalore-dashboard.html`** — open in any browser. Five tabs: the argument, the mobilisation plan, the pincode seed, the captain seed, and the data limits. Self-contained, no build step, no server.
- **`mom-bangalore-captain-seed.csv`** — the 135-row working roster. Fill in `pin_charge_name`, `pin_charge_phone`, `status`.

## The short version

293,569 Miracle of Mind users in Bengaluru. **89.5% of them are not Isha meditators** — the volunteer pool sits almost entirely outside the centre system everyone assumed would supply it. Twenty pincodes carry half the 10,000 target. 1,088 people have already referred three or more others onto the app with no campaign and no incentive; every Tier 1 pincode has at least five of them.

## Data policy

**No personal data in this repository.** Counts only. Names and phone numbers stay inside Ishangam — pull call lists there by filtering `miracle.of.mind` on `record_center` and `total_referred >= 3`.

## Source

Ishangam `miracle.of.mind` (2,392,695 records nationally), queried 31 July 2026, joined to `res.partner` and the Ishangam meditator baseline of 10 July 2026.
