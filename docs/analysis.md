# The analysis: five story points, one argument

Built as a Tableau Story. Each point carries exactly one new idea, and each
idea needs the one before it.

## 1. Here's what we sell

*Chart: Sales by Sub-Category (sorted bar)*
*Caption: Our biggest sellers are Phones ($330K) and Chairs ($328K). Tables is #4.*

Across 2016–2019 the business sold $2.30M in the USA across 17 sub-categories.
If the ad budget followed sales volume, it would go to Phones, Chairs, Storage
and Tables. Note that fourth name — it comes back in a moment.

This is the view most people would budget from.

## 2. Selling a lot doesn't mean earning a lot

*Chart: Sales vs. Profit by Sub-Category (scatter)*
*Caption: Sales and profit barely track each other (r = 0.42). Copiers earns $55.6K; Tables loses $17.7K.*

The turn. If sales and profit moved together, the dots would sit in a tight
line from bottom-left to top-right. They don't — it's a loose cloud, a weak
positive relationship at r = 0.42.

Two dots make the point on their own:

- **Copiers** — 68 orders, the fewest of anything we sell, and the highest
  profit in the business at **+$55,618** (37% margin).
- **Tables** — $206,966 in sales, 4th biggest seller, and it **loses $17,725**
  (−8.6% margin).

Three sub-categories lose money outright: Tables (−$17,725), Bookcases
(−$3,473), Supplies (−$1,189).

The **Profit Target** parameter lives here: drag the slider and the dashed
reference line rises, recolouring every sub-category above or below the bar
leadership sets.

## 3. The discount is what's doing it

*Chart: Profit by Discount Level (bar)*
*Caption: Every discount level above 20% loses money. At or below 20% we earn +$422K; above 20% we lose −$135K.*

The cause. Discounts come in fixed steps, so we can just line them up:

- At **0–20% off**: **+$421,773** profit
- At **above 20% off**: **−$135,376** loss

Not one level above 20% makes money. At 70% off the margin is −99%; at 80%
it's −180% — roughly two dollars lost for every dollar of revenue.

This reframes Tables completely: **+$184 per item at 0% off**, roughly even at
20%, about **−$224 per item at 40%+**. **63.6% of Tables line items lose
money.** The product is fine. The pricing is not.

Past 20% off, every extra sale makes the problem bigger.

## 4. The same rule shows up across the map

*Chart: Profit by State (filled map)*
*Caption: All 10 loss-making states discount above 28%. No profitable state averages above 20%.*

The proof it's a rule, not a coincidence — the strongest number in the deck:

- **All 10 states that lose money average a discount above 28%.**
- **Not one of the 39 profitable states averages above 20%.**
- Across states with meaningful volume, average discount and margin correlate
  at **r = −0.98** — as close to a straight line as real business data gets.

Texas is Tables all over again, geographically: **#3 in sales at $170,188,
and it loses $25,729** (−15% margin, 37% average discount). California, #1 at
$457,688, discounts only 7% and earns a 17% margin.

Two different cuts of the data — by product and by geography — land on the
same 20% line. That's what turns an observation into a rule you can budget
against.

## 5. So here's where the money goes

*Chart: the full dashboard*
*Caption: Fund the high-margin lines we haven't scaled. Fix pricing on the big sellers. Stop buying growth that loses money.*

The decision — **Fund / Fix / Stop**:

**FUND** — high margin, small base, room to grow. Paper (43%), Copiers (37%),
Accessories (25%), Labels (44%), Envelopes (42%). This is where an extra
advertising dollar turns into profit instead of volume.

**FIX PRICING FIRST** — don't advertise until the discount comes down. Binders
is the most-ordered sub-category (1,316 orders) at a 37% average discount and
14.9% margin. Storage and Chairs run thin at 8–10%.

**STOP FUNDING GROWTH** — Tables, Bookcases, Machines, Supplies. Losing money
or close to nothing.

The one-liner: **point the ad budget at margin we haven't scaled, not at
volume we're already discounting away.**

---

### Verified numbers

| Fact | Figure |
|---|---|
| Total sales / profit / margin | $2,297,201 · $286,397 · 12.5% |
| Order lines | 9,994 (17 sub-categories, 49 states, 2016–2019) |
| Biggest seller | Phones, $330,007 |
| Most-ordered | Binders, 1,316 orders — 37.2% avg discount, 14.9% margin |
| Highest profit | Copiers, +$55,618 (37% margin) on 68 orders |
| Loss-makers | Tables −$17,725 · Bookcases −$3,473 · Supplies −$1,189 |
| Sales ↔ profit correlation | r = 0.42 (weak positive) |
| Profit at ≤20% discount | +$421,773 |
| Profit at >20% discount | −$135,376 |
| Tables per item | +$184 at 0% → −$4 at 20% → −$63 at 30% → −$224 at 40%+ |
| Tables line items losing money | 63.6% |
| Loss-making states | 10 — every one averages >28% discount |
| Profitable states above 20% discount | 0 |
| State avg-discount ↔ margin | r = −0.98 |
| Texas | $170,188 sales (#3), −$25,729 profit, 37% avg discount |
| California | $457,688 sales (#1), +$76,381 profit, 7% avg discount |
| Capping discounts at 20% | $286,397 → $421,773 (+$135,376, +47%), keeping 86% of orders |
