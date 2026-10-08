# Methodology

How the workbook is built, and what was checked.

## Data

Superstore sample workbook, sheet `Orders`: 9,994 order lines, 2016–2019, USA.
Reconciled three times against the build: **$2,297,201 sales, $286,397 profit.**
Same file throughout — the numbers in `analysis.md` all trace to it.

Sample data, disclosed as such. The value here is the mechanism, not the
dataset.

## Discovery notes

- The state-level cut was computed after the first draft, not before. It was
  meant to answer "across the USA" and turned into the second independent
  proof of the discount ceiling (r = −0.98). The map was rebuilt as **Profit
  by State** instead of Sales by State for that reason — a sales map only
  shows California is big, which everybody knows.
- The discount ladder: discounts come in fixed steps (0/10/15/20/30/40/45/50/
  60/70/80%), so the ceiling check is a direct read, no modelling.
- Dead end worth naming: a KPI-swap parameter (dropdown changing every chart's
  measure) was considered and cut — it's navigation, not argument, and this
  piece is a recommendation.

## Interactions (4 in the live workbook, against a 2 minimum)

1. **Filter action** — click a sub-category; scatter, discount chart and map
   filter to it. (Known scoping quirk — see QA notes.)
2. **Highlight action** — hover a scatter point; the sub-category lights up on
   the bar chart and scatter. Scoped to sheets containing Sub-Category only.
3. **Profit Target parameter** — slider (−$20K to $60K) driving a reference
   line plus the `Above Target?` calculation (`SUM(Profit) >= Profit Target`),
   recolouring the scatter blue/orange.
4. **Highlighter** — type-ahead search for a sub-category by name.

### Post-publication prototype: Discount Ceiling parameter

Built after the workbook was published to make the recommendation testable: a slider (0–80%)
feeding `Within Discount Ceiling` (`[Discount] <= [Discount Ceiling]`),
applied as a filter across all sheets. At 20%: profit $286,397 → $421,773
(+$135,376, +47%), margin 12.5% → 21.8%, 86% of orders and 84% of sales
retained. It is not in the published workbook — the numbers are the verified
analysis, and the parameter is the honest "what I'd build next".

## Calculated fields

- `Above Target?` — `SUM(Profit) >= [Profit Target]`
- `Profit or Loss` — `IF SUM(Profit) >= 0 THEN 'Profit' ELSE 'Loss' END`
- `Within Discount Ceiling` — `[Discount] <= [Discount Ceiling]`
  (post-publication prototype — not in the published workbook)
- `Margin` — `SUM(Profit) / SUM(Sales)`
- `State Code` — 49-state name→postal-code mapping (see below)

One colour rule throughout: blue = profit, orange = loss, diverging scale
centred on zero. Readable for red-green colour blindness.

### State Code

```tableau
CASE [State]
WHEN "Alabama" THEN "AL"
WHEN "Arizona" THEN "AZ"
WHEN "Arkansas" THEN "AR"
WHEN "California" THEN "CA"
WHEN "Colorado" THEN "CO"
WHEN "Connecticut" THEN "CT"
WHEN "Delaware" THEN "DE"
WHEN "District of Columbia" THEN "DC"
WHEN "Florida" THEN "FL"
WHEN "Georgia" THEN "GA"
WHEN "Idaho" THEN "ID"
WHEN "Illinois" THEN "IL"
WHEN "Indiana" THEN "IN"
WHEN "Iowa" THEN "IA"
WHEN "Kansas" THEN "KS"
WHEN "Kentucky" THEN "KY"
WHEN "Louisiana" THEN "LA"
WHEN "Maine" THEN "ME"
WHEN "Maryland" THEN "MD"
WHEN "Massachusetts" THEN "MA"
WHEN "Michigan" THEN "MI"
WHEN "Minnesota" THEN "MN"
WHEN "Mississippi" THEN "MS"
WHEN "Missouri" THEN "MO"
WHEN "Montana" THEN "MT"
WHEN "Nebraska" THEN "NE"
WHEN "Nevada" THEN "NV"
WHEN "New Hampshire" THEN "NH"
WHEN "New Jersey" THEN "NJ"
WHEN "New Mexico" THEN "NM"
WHEN "New York" THEN "NY"
WHEN "North Carolina" THEN "NC"
WHEN "North Dakota" THEN "ND"
WHEN "Ohio" THEN "OH"
WHEN "Oklahoma" THEN "OK"
WHEN "Oregon" THEN "OR"
WHEN "Pennsylvania" THEN "PA"
WHEN "Rhode Island" THEN "RI"
WHEN "South Carolina" THEN "SC"
WHEN "South Dakota" THEN "SD"
WHEN "Tennessee" THEN "TN"
WHEN "Texas" THEN "TX"
WHEN "Utah" THEN "UT"
WHEN "Vermont" THEN "VT"
WHEN "Virginia" THEN "VA"
WHEN "Washington" THEN "WA"
WHEN "West Virginia" THEN "WV"
WHEN "Wisconsin" THEN "WI"
WHEN "Wyoming" THEN "WY"
END
```

## QA notes

Findings from the pre-publication QA pass — recorded as found, not as fixed.
I checked the published workbook's XML on Oct 7 and both of these are still
in it, so they ship here as known issues with their fixes:

- Story point 5 is pinned to a saved Tables filter while its caption argues
  for Paper/Copiers/Accessories. Fix: open Story 1 → point 5 → click an empty
  area → Update.
- The filter action ("Click Sub-Category to filter") is sourced from the
  whole dashboard and passes All Fields, so clicking a bar also filters the
  bar chart itself. Fix: re-scope the source to the two sub-category charts
  and untick "Sales by Sub-Category" as a target.
- The highlight action is correctly scoped (scatter → bar + scatter; excludes
  the map and the discount chart).

## Limitations & next steps

**What the data can't prove.** Superstore is sample data with suspiciously
clean discount steps (0/10/15/20/30/…). Real promo data is messier — stacked
coupons, category-wide events, clearance. The 20% line is a finding about
this dataset, not a law of retail.

**What I'd do with real data.** Control for the promo calendar and category
mix before trusting the ceiling; check whether the line survives once those
are held constant. Then pilot the cap on one bleeding sub-category (Tables)
as a holdout test before rolling it out — the Discount Ceiling prototype above
is the shape of that test.

**How I'd roll it out.** Phase 1: cap at 20% on Tables and Binders, watch
margin weekly with order volume as the guardrail (the model says we keep 86%
of orders — verify it). Phase 2: extend to Storage and Chairs once pricing is
fixed. Phase 3: re-point the ad budget at the Fund list and measure
incremental margin, not clicks.
