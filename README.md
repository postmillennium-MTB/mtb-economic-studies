# Trail Investment ROI Calculator

### A transparent, evidence-based tool for evaluating the economic return on public trail investment

---

## Table of Contents

1. [Purpose and Intended Audience](#1-purpose-and-intended-audience)
2. [How to Use the Tool](#2-how-to-use-the-tool)
3. [Input Parameters](#3-input-parameters)
4. [International Settings — Units and Currency](#4-international-settings--units-and-currency)
5. [The Three Pre-Set Scenarios](#5-the-three-pre-set-scenarios)
6. [The Economic Model — Complete Formulas](#6-the-economic-model--complete-formulas)
7. [Assumptions, Justifications, and Sources](#7-assumptions-justifications-and-sources)
8. [What the Tool Does Not Model](#8-what-the-tool-does-not-model)
9. [A Note on Methodology and Limitations](#9-a-note-on-methodology-and-limitations)
10. [Highway Cost Comparison Context](#10-highway-cost-comparison-context)
11. [Contributing and Forking](#11-contributing-and-forking)
12. [Bibliography](#12-bibliography)

---

## 1. Purpose and Intended Audience

This tool exists to answer a question that comes up at nearly every city council meeting, parks commission hearing, and community planning session where trails are on the agenda:

> *"We know trails are nice. But do they pay back?"*

The answer, supported by more than 50 peer-reviewed and practitioner studies, is that they do — often substantially. But the magnitude varies enormously by community size, trail quality, visitor mix, and local economic conditions. A one-size-fits-all talking point does not serve advocates or decision-makers well.

This calculator is designed to let users plug in their own local numbers — construction cost estimates, home values, property tax rates, estimated visitor counts — and see a projection grounded in real data rather than a generic national average.

**Primary audiences:**

- **Community advocates** building the economic case for a trail project proposal
- **City council members and commissioners** evaluating whether public investment in trails is financially defensible
- **Parks and recreation directors** preparing budget justifications
- **Economic development staff** modeling outdoor recreation as an industry
- **Journalists and researchers** exploring the outdoor recreation economy at a local level

**What this tool is not:** It is not a certified economic impact study, an appraisal, or a financial forecast. It is a planning and advocacy aid. Results should be validated with local tax records, visitor surveys, and comparable trail data before being presented in a formal municipal context.

---

## 2. How to Use the Tool

The tool is a single self-contained HTML file. Open it in any modern web browser — no server, no installation, and no internet connection required. As of the June 2026 rebuild, every chart is drawn with hand-written JavaScript directly onto the page (no external charting library), so the tool has zero runtime dependencies: it works fully offline, including all four charts, animations, and the printed report. The only thing that touches the network is Google Fonts (for the display typeface) and the optional daily exchange-rate refresh (Section 4) — both degrade gracefully to system fonts and fixed fallback rates if you're offline.

**Step 1 — Choose a scenario.** The three buttons at the top right (Conservative / Moderate / Optimistic) pre-load a set of assumptions calibrated to different levels of trail development, visitor volume, and economic context. This is the fastest way to get a meaningful baseline.

**Step 2 — Adjust inputs for your community.** Every slider represents a variable you should try to localize. The most important ones to get right are:
- Miles of trail (your actual project scope)
- Construction cost per mile (get a local contractor estimate)
- Annual visitors per mile (survey existing comparable trails if possible)
- Homes within ½ mile (pull from your county GIS or assessor data)
- Average home value (use county assessor median for nearby parcels)
- Property tax rate (your municipality's current millage rate)
- City sales tax rate (your city's share of the combined sales tax rate)

**Step 3 — Adjust modeling assumptions.** The visitor ramp-up, annual growth rate, percentage of out-of-town visitors, and maintenance inflation rate all materially affect multi-year projections. Read the sections below to understand what each one means before adjusting.

**Step 4 — Read the results.** The four metric cards at the top of the results panel provide the headline numbers. The breakeven chart shows the full trajectory — its three lines draw in sequence (Total Cost, then Municipal Revenue, then Economic Impact) each time you load the page or change an assumption, so it's easier to follow which line is which. Click any line's legend button to show or hide it. The year-by-year table lets you examine every year's individual values, and the infrastructure cost comparison card near the bottom can be collapsed by clicking its header if you want to shorten the page for a presentation.

**Step 5 — Adjust for international presentation (optional).** Click the **€** button next to Print / Save PDF to open the International Settings panel. Choose **Metric** or **Both** to display distances in kilometres, and select a currency for local context. A disclaimer will appear reminding you that all benchmarks are from US research — adjust the visitor spending and construction cost sliders with locally sourced data before presenting formally outside the United States. See Section 4 for full details.

**Step 6 — Print or save as PDF (optional).** Click **Print / Save PDF** (or use your browser's normal Print command — Ctrl/Cmd+P) and choose **Save as PDF** as the destination, or print to paper. The report is 3 pages — key outcomes, assumptions and the breakeven chart; benefit and visitor charts; the year-by-year table with methodology and a QR code. If the Partnerships panel is open when you print, the full Partnerships section is added as 3 more pages: who pays (with the funding bars), the cost over time and the line-by-line ledger, and the notes, sources and limits. It prints identically whatever size your window or screen is, uses the paper size your browser selects (Letter or A4), and is designed to stay legible in black and white. In the print dialog, leave **Background graphics** on, and switch **Headers and footers** off for the cleanest result (the report carries its own footer and page numbers). The saved PDF is named after the scenario and date.

The **QR code** on page 3 opens this calculator with the same assumptions, so a printed or PDF report can always be traced back to the exact inputs that produced it. It appears only when the calculator is opened from its web address (not from a downloaded file). It restores the main calculator's inputs, units, currency and theme; the Partnerships panel's own sliders are not part of any shareable link (the same is true of **Copy Link**), so a Partnerships section has to be re-adjusted by hand.

---

## 3. Input Parameters

### Trail Project

| Parameter | Default (Moderate) | Range | Notes |
|---|---|---|---|
| Miles of trail | 10 mi | 1–60 mi | Total miles in the proposed project |
| Construction cost / mile | $50,000 | $10K–$120K | One-time capital cost; does not inflate |
| Maintenance / mile / year | $2,500 | $500–$8,000 | Base year cost; inflates annually if selected |
| Grant funding | 0% | 0–80% | Share of construction covered by RTP, RAISE, CMAQ, or state grants; reduces the municipal share used for breakeven and ROI |

### Visitor Activity

| Parameter | Default (Moderate) | Range | Notes |
|---|---|---|---|
| Annual visitors / mile | 1,000 | 100–5,000 | Target count at full capacity, after ramp-up |
| Avg spending / visit | $175 | $50–$600 | Blended day-trip and overnight average |
| Overnight visitors | 30% | 0–80% | Share of visitors who stay at least one night |
| Out-of-town visitors | 60% | 0–100% | Share of visitors whose primary residence is outside the community |
| City sales tax rate | 4.25% | 0.25–8.0% | The city's share of the combined sales tax; not the full combined rate |

### Visitor Growth & Ramp-up

| Parameter | Default (Moderate) | Range | Notes |
|---|---|---|---|
| Annual visitor growth rate | 3% | 0–10% | Compounding annual increase applied after ramp-up ends |
| Visitor ramp-up period | 2 years | 0–5 years | Years to reach full visitor capacity from trail opening |

### Real Estate Impact

| Parameter | Default (Moderate) | Range | Notes |
|---|---|---|---|
| Homes within ½ mile | 100 | 0–1,500 | Count of residential parcels within ½ mile of any trail segment |
| Average home value | $350,000 | $100K–$1.2M | Median assessed or market value for those parcels |
| Property value premium | 5% | 0–15% | Estimated uplift in home values attributable to trail proximity |
| Property tax rate | 1.2% | 0.3–3.5% | Municipal property tax rate (millage) as a percentage |

### Economic Factors

| Parameter | Default (Moderate) | Range | Notes |
|---|---|---|---|
| Economic multiplier | 1.5× | 1.0–2.5× | Applied only to out-of-town visitor spending |
| Projection horizon | 20 years | 5–30 years | Length of the financial projection |
| Maintenance inflation | 2% | Off / 1–5% | Annual CPI escalation applied to maintenance costs |

---

## 4. International Settings — Units and Currency

The calculator's internal model runs entirely in US dollars and imperial units (miles). This reflects the research literature it is built on — nearly all the underlying studies were conducted in the United States and report values in USD and miles. An International Settings panel provides display-layer conversion for users presenting outside the United States or working with international audiences.

### Opening the Panel

Click the **€** button in the top-right header, next to the Print / Save PDF button. The button turns blue when the panel is open; click it again to close it. The panel stays open across recalculations and is saved in shared links.

---

### 4.1 Units

Three display modes are available:

| Mode | Behavior |
|---|---|
| **Imperial** (default) | All distances in miles; per-distance costs in $/mile. The native format of the underlying research. |
| **Metric** | Distances in km; per-distance costs converted to $/km (= $/mile ÷ 1.60934). |
| **Both** | Shows both values side by side on each label — e.g., *10 mi \| 16.1 km* or *$50K/mi \| $31K/km*. |

**What changes:** the miles-of-trail display, construction cost per distance, maintenance cost per distance, visitors per distance, the property radius description ("½ mile" → "0.8 km"), and all matching labels in chart tooltips and the printed report.

**What does not change:** the underlying calculations. Every projection runs in imperial units internally. Metric is a display conversion applied after computation. Switching modes does not alter any projected outcome — breakeven year, ROI %, economic impact, and jobs figures are identical regardless of which unit mode is selected.

**Conversion used:** 1 mile = 1.60934 km. Per-distance costs are divided by 1.60934 (a lower number per km is correct — there are more kilometres in a mile-length trail than miles).

---

### 4.2 Currency

Five currencies are available:

| Button | Currency | Display symbol |
|---|---|---|
| USD (default) | US Dollar | $ |
| Australian flag | Australian Dollar | A$ |
| Canadian flag | Canadian Dollar | CA$ |
| EU flag | Euro | € |
| Union Jack | British Pound | £ |

Selecting a currency multiplies every displayed monetary value by the current exchange rate for that currency against USD. This affects metric cards, slider value labels, chart tooltips, callout text, the year-by-year table, and the printed report.

**What does not change:** the underlying model. All calculations run in USD. ROI percentages, breakeven year, and job estimates are dimensionless and unaffected by currency selection.

---

### 4.3 Exchange Rates — Source and Reliability

Exchange rates are fetched on page load from a **pinned, dated version** of this feed:

```
https://cdn.jsdelivr.net/npm/@fawazahmed0/currency-api@2026.10.21/v1/currencies/usd.json     (example: the version dated 21 Oct 2026)
```

This is a free, no-registration currency feed published as an npm package and served via the jsdelivr content delivery network. It publishes one version per day, named for its date, and a published version never changes. The tool therefore asks for today's (UTC) version, then yesterday's, then the day before (`RATES_DAYS_BACK`), and uses the first one that exists; it never requests `@latest`. The panel shows "rates as of [date]" using the date inside the snapshot it actually used. A response whose AUD, CAD, EUR or GBP rate is more than 30% from the built-in snapshot (`RATES_SANITY`) is rejected as bad data.

**Fallback rates** (`exRates` and `FALLBACK_RATES_DATE` in `index.html`) are used if the fetch fails (offline use, CDN outage, or a rejected response). The panel then says "approximate rates as of [date]" and the printed report says the rate is an approximate built-in one. The tool functions normally; only the precision of the currency conversion is affected.

| Currency | Fallback rate (1 USD =) | As of |
|---|---|---|
| AUD | 1.546 | June 2026 |
| CAD | 1.362 | June 2026 |
| EUR | 0.918 | June 2026 |
| GBP | 0.783 | June 2026 |

**Long-term reliability note:** The exchange rate feed is a personal open-source project. It is well-maintained as of mid-2026, but its continued availability is not guaranteed — the developer could abandon it, restructure the URL format, or the CDN could change its terms. For institutional or long-term deployments, the European Central Bank publishes a free exchange rate API that has been publicly available since the late 1990s and is maintained by a permanent institution. To change the source, update the `fetchRates()` function and the hardcoded `exRates` fallback object in the JavaScript section of the HTML file. The hardcoded fallback rates should also be refreshed whenever the tool is forked or re-deployed.

---

### 4.4 The US-Research Disclaimer

Whenever Metric or Both is selected, or whenever a non-USD currency is chosen, the following notice appears at the bottom of the International Settings panel:

> *"All spending benchmarks, construction costs, and property value research are drawn from studies conducted in the United States. Values shown here are approximate conversions — the underlying research data is USD-based and imperial units. Treat converted figures as directional context, not locally validated estimates."*

A link in the notice opens the Data Sources & Methodology section at the bottom of the calculator.

**Why the disclaimer exists.** The research benchmarks in this tool — visitor spending averages ($103–$416/visit), construction cost ranges ($35K–$80K/mile), property value premiums (3–15%), economic multipliers — are drawn from studies of US trail systems in US economic conditions. Multiplying $175 by an AUD exchange rate does not produce a validated Australian visitor spending figure. Trail visitor behavior, labor markets, land acquisition costs, property tax structures, and retail economics differ meaningfully across countries.

**What the tool is and is not useful for outside the United States:**

Useful for:
- Understanding the structure and logic of a trail ROI argument
- Comparing the order of magnitude of trail costs against road infrastructure in your country
- Generating a starting framework for a locally sourced analysis

Not a substitute for:
- Local visitor surveys using regional spending benchmarks
- Country-specific construction cost estimates
- Locally validated property value premium studies

The visitor spending and construction cost sliders are the variables most likely to need local calibration. Property value premium research exists in Australia, Canada, and the UK and can replace the US-sourced defaults.

---

### 4.5 URL State

The Copy Link button encodes the selected unit mode and currency in the shared URL alongside all slider values. A recipient opening the link will see the same display settings you had when you copied it.

---

## 5. The Three Pre-Set Scenarios

Each scenario represents a realistic but distinct context. They are calibrated to actual case study data from the research literature, not invented symmetrically around a midpoint.

### Conservative

Intended to represent a smaller rural or suburban community building a modest trail system that primarily serves local residents, with limited destination appeal in the early years. Visitor spending benchmarks are drawn from the Duluth, MN study (the lowest-spending destination in the TPL/IMBA meta-analysis).

| Parameter | Value | Rationale |
|---|---|---|
| Miles | 15 | Modest first phase |
| Construction cost/mi | $35,000 | Partially volunteer-built or low-complexity terrain |
| Maintenance/mi/yr | $1,500 | Minimal corridor; volunteer-supplemented |
| Visitors/mile/yr | 500 | Small community, limited marketing |
| Avg spend/visit | $103 | Duluth, MN benchmark (TPL 2025) |
| Overnight visitors | 15% | Primarily day-use |
| Out-of-town visitors | 40% | Mostly local/regional |
| Sales tax rate | 4.25% | Held constant across all scenarios |
| Property value premium | 3% | Lower end of NAR/Crompton research range |
| Visitor growth/yr | 1% | Slow build |
| Ramp-up period | 3 years | Conservative adoption |
| Maintenance inflation | 3% | Full CPI escalation |

### Moderate

Represents a mid-sized community investing in a professionally designed trail system with genuine destination appeal. Visitor spending benchmarks reflect a regional average across the TPL/IMBA case studies.

| Parameter | Value | Rationale |
|---|---|---|
| Miles | 10 | Focused quality network |
| Construction cost/mi | $50,000 | Professional design; mixed terrain |
| Maintenance/mi/yr | $2,500 | Mid-range professional maintenance |
| Visitors/mile/yr | 1,000 | Mid-range destination |
| Avg spend/visit | $175 | Regional mid-range average |
| Overnight visitors | 30% | Mixed day-trip and overnight |
| Out-of-town visitors | 60% | Genuine destination appeal |
| Sales tax rate | 4.25% | Held constant across all scenarios |
| Property value premium | 5% | Midpoint of NAR/Crompton research range |
| Visitor growth/yr | 3% | Moderate growth; below global MTB CAGR |
| Ramp-up period | 2 years | Standard adoption curve |
| Maintenance inflation | 2% | Moderate CPI |

### Optimistic

Represents a purpose-built destination trail system with strong marketing, significant out-of-town draw, and visitor spending at the upper end of the research range. Modeled after destinations like Kingdom Trails (VT), Chattanooga (TN), or the Chequamegon area (WI).

| Parameter | Value | Rationale |
|---|---|---|
| Miles | 20 | Destination-scale network |
| Construction cost/mi | $60,000 | Professional build with features |
| Maintenance/mi/yr | $3,000 | Higher-quality maintenance standard |
| Visitors/mile/yr | 2,000 | Strong destination draw |
| Avg spend/visit | $416 | TPL/IMBA 2025 national average across 50 studies |
| Overnight visitors | 50% | Majority stay overnight |
| Out-of-town visitors | 75% | Primarily destination visitors |
| Sales tax rate | 4.25% | Held constant across all scenarios |
| Property value premium | 8% | Upper-mid range; consistent with active trail destination |
| Visitor growth/yr | 6% | Strong growth; below global MTB CAGR of 8.9% |
| Ramp-up period | 1 year | Fast adoption with marketing |
| Maintenance inflation | 0% | Off; real-dollar comparison |

---

## 6. The Economic Model — Complete Formulas

The model computes all values year-by-year from Year 1 through the projection horizon (and up to Year 65 to find the breakeven point if it falls outside the displayed range). Nothing is computed as a flat annuity. Every year's values depend on ramp-up, growth, and inflation compounding from the prior year.

### 5.1 Input Variables

```
miles           = total trail miles
buildcost       = construction cost per mile ($)
maint           = base maintenance cost per mile per year ($)
visitors        = target annual visitors per mile at full capacity
spend           = average spending per visit ($)
overnight       = fraction of visitors who stay overnight (0–1)
nonlocal        = fraction of visitors who are out-of-town (0–1)
salestax        = city's sales tax rate (0–1)
homes           = number of homes within ½ mile of trail
homeval         = average home value ($)
propprem        = property value premium from trail proximity (0–1)
proptax         = property tax rate (0–1)
multiplier      = economic multiplier applied to out-of-town spending
visitorgrowth   = annual visitor growth rate (0–1)
rampup          = number of years to reach full visitor capacity (integer)
inflation       = annual maintenance cost escalation rate (0–1)
years           = projection horizon (integer)
```

### 5.2 Derived Constants (computed once)

```
capitalCost     = miles × buildcost
municipalCap    = capitalCost × (1 - grant)
maintBase       = miles × maint
baseVisitors    = miles × visitors
propTaxAnn      = homes × homeval × propprem × proptax
propValueAdded  = homes × homeval × propprem
```

**`propTaxAnn`** is treated as constant across all years. The property value premium is assumed to be realized in Year 1 and held flat in real terms. This is a conservative treatment; in practice, trail-adjacent property values may continue to appreciate.

### 5.3 Effective Spending Per Visit

Overnight visitors spend approximately twice as much as day visitors because they pay for lodging and additional meals. Rather than modeling two separate visitor populations, the tool blends them into a single effective spend figure:

```
effectiveSpend = spend × (1 + overnight)
```

**Derivation:** Let `d` = day-trip spend = `spend`, and overnight spend = `2 × spend`. The blend of a population that is `overnight` fraction overnight and `(1 - overnight)` fraction day-trippers gives:

```
effectiveSpend = spend × (1 - overnight) + (2 × spend) × overnight
              = spend × (1 - overnight + 2 × overnight)
              = spend × (1 + overnight)
```

*Example:* With `spend = $175` and `overnight = 0.30`, `effectiveSpend = $175 × 1.30 = $227.50`.

### 5.4 Year-by-Year Visitor Count

For each year `yr` from 1 to `maxYears`:

**Ramp-up factor:**

```
if rampup = 0 OR yr > rampup:
    rampFactor = 1.0

else if rampup = 1:
    rampFactor = 0.40   (single-year ramp: 40% capacity in Year 1)

else:
    rampFactor = 0.40 + 0.60 × (yr - 1) / (rampup - 1)
```

This produces a linear interpolation from 40% capacity in the first ramp-up year to 100% in the final ramp-up year. The 40% starting point is calibrated from observed ramp-up curves at Duluth (MN), Blue Derby (Tasmania), and Kingdom Trails (VT).

**Growth factor** (compounds from end of ramp-up):

```
growthYrs = max(0,  yr - rampup)       if rampup > 0
growthYrs = yr - 1                      if rampup = 0

growthFactor = (1 + visitorgrowth) ^ growthYrs
```

**Visitors in year `yr`:**

```
visitorsYr = baseVisitors × rampFactor × growthFactor
```

*Example (Moderate scenario, Year 5 with 2-year ramp-up and 3% annual growth):*
- `rampFactor = 1.0` (ramp-up ended after Year 2)
- `growthYrs = 5 - 2 = 3`
- `growthFactor = 1.03^3 = 1.0927`
- `visitorsYr = (10 mi × 1,000/mi) × 1.0 × 1.0927 = 10,927 visitors`

### 5.5 Annual Spending

```
totalSpendYr  = visitorsYr × effectiveSpend
nonLocalSpend = totalSpendYr × nonlocal
localSpend    = totalSpendYr × (1 - nonlocal)
```

### 5.6 Annual Municipal Revenue

Sales tax is collected regardless of whether the visitor is local or out-of-town, because both groups transact within the municipality:

```
salesTaxYr = totalSpendYr × salestax
muniYr     = salesTaxYr + propTaxAnn
```

Note that `propTaxAnn` does not vary by year in this model. It is the incremental property tax revenue generated by the trail-proximity premium on nearby homes.

### 5.7 Annual Economic Impact

The economic impact to the local economy treats local and out-of-town visitors differently. Out-of-town visitors bring money that would not otherwise enter the local economy, so their spending is amplified by the economic multiplier. Local visitors are largely spending money they already have; their dollars recirculate rather than grow the economy, so the multiplier is 1.0.

```
econYr = (nonLocalSpend × multiplier) + (localSpend × 1.0)
       = nonLocalSpend × multiplier + localSpend
```

*Example (Moderate, Year 5 as above with nonlocal = 0.60, multiplier = 1.5):*
```
totalSpendYr  = 10,927 × $227.50 = $2,485,893
nonLocalSpend = $2,485,893 × 0.60 = $1,491,536
localSpend    = $2,485,893 × 0.40 = $994,357

econYr = ($1,491,536 × 1.5) + $994,357
       = $2,237,304 + $994,357
       = $3,231,661
```

This treatment is consistent with the methodology in the Duluth, MN study (Savolt, 2017), which explicitly separated local and non-local impacts, and with the methodological critique in Buning & Lamont (2021), which found that failure to separate local and out-of-town spending is the most common source of inflated economic impact figures in practitioner studies.

### 5.8 Annual Maintenance Cost with Inflation

Trail maintenance is heavily labor-driven. Labor costs compound with general CPI inflation, which historically runs 2–4% in the United States. The nominal maintenance cost in year `yr` is:

```
maintYr = maintBase × (1 + inflation) ^ (yr - 1)
```

Year 1 maintenance = `maintBase` (the base-year value entered by the user). Year 20 maintenance at 3% inflation = `maintBase × 1.03^19 = maintBase × 1.754`. In other words, nominal maintenance costs grow by approximately 75% over 20 years at 3% inflation.

When inflation is set to "Off" (0%), all years use `maintBase` unchanged. This is appropriate for analyses conducted in constant (real) dollars, but it understates nominal future costs.

### 5.9 Cumulative Values

Each year `yr` accumulates from all prior years:

```
cumCost[yr] = capitalCost + Σ(maintYr) for yr' = 1 to yr
cumMuni[yr] = Σ(muniYr)  for yr' = 1 to yr
cumEcon[yr] = Σ(econYr)  for yr' = 1 to yr
```

### 5.10 Breakeven Year

The breakeven year is defined as the first year in which cumulative municipal revenue equals or exceeds the initial construction cost, ignoring maintenance costs:

```
municipalCap = capitalCost × (1 - grant)
breakeven    = min(yr) such that cumMuni[yr] ≥ municipalCap
```

If no grant funding is applied (`grant = 0`), `municipalCap` equals the full construction cost. When grant funding is selected, the breakeven threshold is the municipality's own share — the question being answered is whether the *municipality's* outlay is recovered, since grant dollars are not a local cost.

**Why is maintenance excluded from breakeven?** Because the breakeven question being answered is: *"Does the community's tax revenue from this trail eventually pay back the upfront capital investment?"* Maintenance is an ongoing operational expense, like maintaining a park or a road, and is typically budgeted separately from capital recovery. Including maintenance in the breakeven denominator would never produce a breakeven for most public infrastructure, including roads, parks, and utilities.

The cost line in the breakeven chart does include cumulative maintenance, so the visual shows total cost including maintenance — it is only the single breakeven threshold that compares municipal revenue against construction cost alone.

The model searches up to Year 65. If no breakeven is found within 65 years, the result is displayed as "> 65 years."

### 5.11 10-Year Return on Construction Cost

```
roi10 = (cumMuni[10] / municipalCap - 1) × 100%
```

This is expressed as a percentage return on the municipality's construction outlay (after grant funding, if any) over 10 years, using only direct municipal revenue (tax receipts). A value of +50% means cumulative municipal tax revenue over 10 years equals 150% of the municipal construction share.

### 5.12 Jobs Estimate

```
jobs = round(econYr[matureYear] / 45,000)
```

**Source status: the $45,000 divisor is a rule of thumb, not a sourced figure.** Earlier versions of this README attributed it to IMBA regional studies and to the TPL/IMBA 2025 report. Checked in October 2026 against the full TPL Green Paper (*Economic Benefits of Mountain Biking*, 2025) and IMBA's 2025 Annual Report: neither states a $45,000 figure. The annual report only repeats the headline ("up to 1,626 jobs and $54.1 million in labor income each year", 13 communities).

What the Green Paper's own site tables imply (computed from the tables, 19 site entries):

| Ratio | Range across sites | Typical |
|---|---|---|
| Labor income per job | about $24,000 to $40,000 | about $32,000 (all-sites aggregate: $54.1M / 1,626 = $33,300) |
| Economic output per job | about $75,000 to $128,000 | about $85,000 to $90,000 |
| Value added per job | about $39,000 to $81,000 | about $52,000 |

The tool divides **annual economic impact** (visitor spending including the multiplier, not labor income) by $45,000. The closest like-for-like ratio in the Green Paper is economic output per job, roughly $75,000 to $128,000, so the tool's job count is likely high by a factor of about 1.7 to 2.8 against TPL's own ratios. It is shown as indicative on the page. **Open decision:** replace the divisor with a TPL-derived output-per-job figure (and name the source), or relabel the headline as "jobs, rule-of-thumb basis".

where `matureYear = rampup + 1` (first year at full capacity, before growth).

### 5.13 Mature Year (for Donut Chart)

The donut chart shows the annual benefit breakdown for the "mature year" — the first year the trail reaches full capacity, before growth compounds further. This provides a representative annual snapshot.

```
matureIndex = rampup       (0-indexed; corresponds to year rampup + 1)
```

If `rampup = 0`, mature year = Year 1. If `rampup = 2`, mature year = Year 3.

---

## 7. Assumptions, Justifications, and Sources

### 6.1 Visitor Spending Benchmarks

**Conservative: $103/trip**
Drawn from the University of Minnesota Duluth study (Savolt, 2017), the lowest per-visit spending recorded among all destinations in the TPL/IMBA 2025 meta-analysis. Appropriate for local trail systems with limited overnight accommodation and primarily day-use visitors.

**Moderate: $175/trip**
A regional middle estimate between the Duluth low ($103/day) and the Vermont Kingdom Trails figure ($176/day). Consistent with typical small-to-mid-size destination trails with some overnight accommodation.

**Optimistic: $416/trip**
The national average across all 50 studies in the TPL/IMBA 2025 meta-analysis (Horn et al., 2025). This reflects a broad mix of rural destination trails, bike parks, and events. The range across all studies was $103 to $1,107 per trip; the Chequamegon area (WI) recorded $1,107/trip as the highest in the dataset.

### 6.2 Overnight Visitor Spending Multiplier

The assumption that overnight visitors spend approximately twice as much as day visitors is consistent with general tourism research and specifically cited in the TPL/IMBA 2025 report, which notes that overnight visitors pay for lodging, additional meals, and extended retail purchases that day visitors do not. The $416/trip average in the meta-analysis blends day-trip and overnight visits; the 2× multiplier for overnight is applied by the model before that blend is taken into account, so users can adjust the overnight fraction independently.

### 6.3 Economic Multiplier

**Range: 1.2–1.8×**

The economic multiplier (also called the IMPLAN or input-output multiplier) captures the ripple effect of visitor spending. When a mountain biker spends $175 at a local restaurant, the restaurant owner uses some of that revenue to pay local staff, who spend some of their wages locally, and so on. Each round is smaller than the last. The total economic activity generated per dollar of initial visitor spending is the multiplier.

The 1.5× default reflects the regional average for rural/small-city tourism multipliers in IMPLAN-based studies. Smaller, more isolated communities tend to have lower multipliers (1.2–1.3×) because more money leaks out of the local economy to regional suppliers. Larger, more diversified economies may have multipliers of 1.7–2.0×.

Critically, this tool applies the multiplier only to out-of-town visitor spending. Local visitor spending is assigned a multiplier of 1.0 because local residents are largely substituting trail-related spending for other spending they would have made in the same local economy. Applying the full multiplier to local spending inflates the economic impact figure and has been identified as a common methodological error in practitioner studies (Buning & Lamont, 2021).

### 6.4 Property Value Premium

**Range: 0–15%, default 3–8% by scenario**

The research on trail proximity and property values is remarkably consistent: trails increase, or at worst do not decrease, nearby home values. The typical finding is a 3–5% premium for homes within approximately ½ mile of a trail.

Key findings from the literature:

- Crompton & Nicholls (2019): reviewed 20+ studies; concluded 3–5% premium is the most widespread finding for single-family homes near trails.
- Nicholls & Crompton (2005): found premiums of 5–10% in various locations.
- Indianapolis Cultural Trail: $1 billion increase in assessed property values within 500 feet of the trail between 2008 and 2014.
- Little Miami Scenic Trail (OH): each additional foot closer to the trail added approximately $7 to home value, suggesting a significant premium for directly adjacent properties.
- San Antonio, TX: 2% increase for homes near trails; 5% for homes adjacent to greenbelt-surrounded trails.
- Burke-Gilman Trail (Seattle): properties near but not immediately adjacent sell for ~6% more on average.

The ½-mile radius used in this tool is consistent with the typical study boundary in the peer-reviewed literature.

### 6.5 Visitor Ramp-up

**Default: 2 years (Moderate); starts at 40% capacity in Year 1**

New trail systems rarely achieve their long-run visitor counts immediately. Word-of-mouth, destination reputation, trail review platforms (Trailforks, MTB Project), and event programming all take time to develop. Evidence from case studies:

- Blue Derby, Tasmania: sustained multi-year visitor growth after opening, achieving peak recognition when it won international trail awards in 2017 and 2019.
- Kingdom Trails, Vermont: grew from a regional trail to an international destination over several years following systematic investment and marketing.
- Duluth, MN: visitation grew substantially as the trail network expanded and regional awareness increased.

The 40% starting capacity figure is a calibrated approximation consistent with these trajectories. Users who have evidence that their planned trail will be immediately well-used (e.g., a trail that connects to an existing popular network) should set ramp-up to 0 or 1 year. Users expecting a slow build in a new destination should use 3–5 years.

### 6.6 Annual Visitor Growth Rate

**Range: 0–10%; defaults: 1% conservative, 3% moderate, 6% optimistic**

The global mountain bike market is growing at a compound annual growth rate of approximately 5.8–8.9% (Technavio, 2025). Individual trail destinations typically grow more slowly than the overall market because they are constrained by geography, accommodation capacity, and marketing budget. Appropriate local growth rate estimates:

- Established regional trails with modest marketing: 1–2%
- Mid-tier destination with active promotion: 3–4%
- Purpose-built destination with strong branding: 5–7%
- Exceptional new destination (rare): 8–10%

Growth compounds from the first year after the ramp-up period ends. It is applied to the full-capacity baseline visitor count, not the ramp-up-reduced count.

### 6.7 Maintenance Inflation

**Default inflation rates: 3% conservative, 2% moderate, Off for optimistic**

Trail maintenance costs are dominated by labor: trail crew wages, equipment operator costs, and contractor fees for drainage work, erosion repair, and surface grading. These costs compound with general wage inflation and CPI.

At 3% annual inflation, the nominal maintenance cost in Year 20 is approximately 81% higher than in Year 1. A trail system that costs $2,500/mile/year to maintain today would nominally cost $4,516/mile/year in Year 20 at 3% CPI.

When analyzing in constant (real) dollars — as is common in academic economic impact studies — setting inflation to "Off" is correct, but only if you also interpret all projected revenues in constant dollars. When presenting to a city council considering a budget appropriation, nominal (inflating) costs are more relevant because budget line items are nominal.

The default for the Moderate scenario (2% inflation) represents a conservative real-terms escalation that acknowledges labor cost growth without assuming the highest plausible CPI scenario.

### 6.8 Local vs. Out-of-Town Visitor Split

**Default: 40% out-of-town (conservative), 60% (moderate), 75% (optimistic)**

This is arguably the single most important variable in the model. It directly determines how much of the visitor activity represents genuine new economic activity versus recirculation of existing local spending.

**Why it matters so much:** Suppose a trail attracts 10,000 annual visitors. If all 10,000 are local residents who now bike at the trail instead of going to the gym or shopping at a mall in the same town, the economic impact of visitor spending is zero (or even slightly negative, if the trail shifted spending from higher-tax-generating businesses). If all 10,000 are visitors from other cities who are spending money they would otherwise have spent somewhere else, the impact of their spending is substantial new economic activity.

Real-world destination trail systems typically report 50–80% out-of-town visitors among those surveyed. However, local trail systems with no destination profile may have 80–90% local users. Community advocates should survey local trail users if possible, or use comparable trail data from their region.

The model does not reduce local visitor economic impact to zero — local visitors still generate sales tax revenue and spend at local businesses. The difference is that their spending does not grow the economy through the multiplier effect, because it substitutes for other local spending.

---

## 8. What the Tool Does Not Model

The following economic benefits are documented in the research literature but are not included in this tool. They are excluded not because they are unreal, but because they are harder to quantify reliably at a community level, and including speculative figures in a tool intended for advocacy and municipal planning would undermine credibility.

### 7.1 Healthcare Cost Savings

The American Heart Association (2011) found that for every $1 invested in trails, approximately $3 is saved in direct healthcare costs through increased physical activity and improved cardiovascular health. In Northwest Arkansas, mountain biking trails were specifically associated with $8.7 million per year in avoided healthcare costs (TPL/IMBA, 2025). For municipalities with self-funded employee health insurance or significant Medicaid exposure, this is a real budget consideration but is difficult to localize without health outcome data.

### 7.2 New Resident Attraction and Workforce Effects

A survey in Tasmania's Break O'Day Council found that approximately 25% of people moving to the area were influenced by the MTB trail network (Break O'Day Council, 2025). The Carolina Thread Trail study (ITRE/NC State, 2022) documented trails as a draw for young professionals choosing where to live. West Virginia's Ascend WV program explicitly uses outdoor recreation access as a workforce attraction strategy. These effects are real and increasingly well-documented, but translating them into a per-mile dollar figure for a specific community requires local migration and demographic data that is not generally available.

### 7.3 Event Revenue

Major mountain bike events — races, festivals, competitions — generate economic impacts that dwarf regular trail use in a single weekend. The Crankworx Whistler Festival (2023) generated approximately $38.5 million USD from a single event with 300,000 attendees. Smaller local events can generate $200,000–$500,000 in a rural community over a weekend. This is excluded because it is highly variable and depends on event programming decisions that are separate from trail infrastructure.

### 7.4 New Business Formation

Historic examples include Milford, Delaware (where a greenway trail investment correlated with a net gain in new downtown businesses and 250+ new downtown jobs) and Oakridge, Oregon (a former logging town that revitalized its economy around mountain biking). These long-run economic restructuring effects are plausible but too slow-moving and speculative to model with precision.

### 7.5 Stormwater and Environmental Value

Trail and greenway corridors reduce impervious surface runoff, reducing municipal stormwater management costs. The Carolina Thread Trail study (ITRE, 2022) calculated dollar values for carbon storage, sequestration, and emissions reductions attributable to the trail greenway. These are real but small relative to the visitor economic impact figures and require ecological data.

### 7.6 Consumer Surplus and Recreational Value

Academic studies (Moran, Tresidder & McVittie, 2006; Bickel, 2020) use travel cost methods to estimate the total welfare value visitors receive, including the portion they would have paid if charged a fee. Glentress, Scotland estimated £80 per visit in consumer surplus against approximately 120,000 annual visits. This represents real welfare, but is not a municipal revenue figure and is less useful for budget-oriented advocacy.

### 7.7 Reduced Road Infrastructure Costs

Increased cycling as a transportation mode reduces vehicle miles traveled on municipal roads, extending road life and reducing road maintenance costs. The National Bicycle and Pedestrian Clearinghouse estimated that 50% of car trips are less than 3 miles — many of which could be made by bicycle on connected trail systems. This is more relevant to urban trail and greenway planning than to backcountry singletrack.

---

## 9. A Note on Methodology and Limitations

### On the academic literature

Buning & Lamont (2021), in a critical review of 33 academic and practitioner mountain bike economic impact studies, found "widespread inconsistency in instrumentation and variable measurement contributing to a fragmented body of knowledge." Specific problems they identified included:

- Failure to separate local versus non-local visitor spending (leads to inflated multiplier effects)
- Inconsistent definitions of the "study area" (some studies count regional impacts, some only local)
- Variation in survey methodology (on-trail intercept surveys vs. online surveys produce different demographics)
- Inclusion of "resident value" alongside "tourism value" without clear delineation
- Inadequate seasonal adjustment (most surveys are conducted in peak season)

This tool attempts to address the most important of these by: (1) explicitly separating local and non-local visitor spending with different multipliers; (2) providing the local vs. out-of-town slider so users can reflect their own community's visitor mix; and (3) clearly labeling "direct municipal revenue" (actual tax receipts) separately from "economic impact" (total economic activity, which is not a government revenue figure).

### On the property value research

Crompton & Nicholls (2019) note that most property value studies rely on hedonic price modeling — statistical models that isolate the contribution of trail proximity from other factors (school quality, neighborhood, age of home, etc.). These models require large datasets of comparable sales and sophisticated econometrics. The 3–15% range in the literature reflects genuine variation across contexts, not methodological uncertainty about a single "true" value. Communities with higher baseline property values, better trail access, and more active outdoor cultures tend to show larger premiums.

### What this tool should and should not be used for

**Appropriate uses:**
- Internal planning to understand the range of possible returns before committing to a project
- Community presentations to illustrate the economic logic of trail investment
- Identifying which input variables matter most (sensitivity analysis by moving individual sliders)
- Comparing scenarios for a city council presentation

**Inappropriate uses:**
- Presenting specific dollar figures as though they were economic forecasts or appraisals
- Replacing a formal economic impact study for a major public investment decision
- Litigation, bond prospectus preparation, or formal feasibility studies

If you are working on a major trail project (over $1 million in public investment), we recommend commissioning a formal economic impact study using IMPLAN, REMI, or a comparable regional input-output model calibrated to your specific community.

---

## 10. Highway Cost Comparison Context

The highway cost comparison is included to give decision-makers a sense of proportionality. Trail infrastructure is extremely inexpensive compared to road infrastructure, yet it is often treated as a discretionary luxury rather than essential public infrastructure.

The bars can be drawn on a **log scale** (the default) or a **linear scale**, using the switch at the top of the card. On the log axis each step along the bar multiplies the cost, which keeps a $70K trail mile and a $4M road mile on one chart but makes the trail look about 40% as long as the road when it costs about 2% as much. The linear axis is true to proportion; the singletrack bars become slivers (a 0.4% minimum width is drawn so they stay visible, so the slivers are not to scale against each other). A second switch, **Typical / Range**, is built but currently hidden (see below); when enabled it changes what each row draws. *Typical* draws one value per type. *Range* draws a floating bar from the low to the high figure in the table below, with a dark tick at the typical value; the current project has a single value, so it shows as a tick only. A floating range claims only a position, not a length from zero, which makes it the more honest of the two on the log axis. Both choices are remembered in the browser only (`pmr-roi-hwy-scale`, `pmr-roi-hwy-range`); the chart works with them empty. The scale labels and reading notes live in the `HWY_SCALES` registry and the lows, highs and typical values in `INFRASTRUCTURE_COSTS`, both in `index.html`.

| Infrastructure type | Chart value (per mile) | How it is derived | Source |
|---|---|---|---|
| Volunteer-built singletrack | $10,000 (range $2,000–$15,000) | Judgment pick inside the range | **Partly supported, mostly an estimate.** The San Luis Valley Great Outdoors toolkit ("Developing Trail Systems", pp. 61-68) says natural-surface singletrack construction is typically $15,000-$40,000 per mile, can cost "less than $5,000 per mile" in the easiest scenario with copious skilled volunteers, and can exceed $100,000 per mile in difficult terrain. Estimates are construction only, excluding planning, design and permits. The $2,000-$15,000 range itself is not printed in any source found |
| Professional contractor-built singletrack | $70,000 (range $60,000–$80,000) | Judgment pick inside the printed range | Singletracks.com contractor survey, April 2026 |
| Paved multi-use path | $792,000 | $150 per linear foot × 5,280 ft | NJDOT Transportation Alternatives Program, *2024 Cost Estimate Guidelines and Recommendations for Pedestrian, Bicycle and Traffic Calming Projects*: 10-ft shared use path, asphalt on a dense-graded aggregate base, conceptual-level typical cost |
| 2-lane rural road | $3,932,000 | $1,966K per lane mile × 2 lanes | FHWA HERS, rural minor arterial, flat terrain, new alignment |
| 4-lane suburban highway | $22,036,000 | $5,509K per lane mile × 4 lanes | FHWA HERS, urban other principal arterial, large urbanized area (population over 200,000), new alignment, normal cost |
| Urban 6-lane interstate | $48,948,000 | $8,158K per lane mile × 6 lanes | FHWA HERS, urban freeway/expressway/interstate, large urbanized area, new alignment, normal cost |

**Where the road figures come from.** The FHWA Highway Economic Requirements System publishes "Typical Costs per Lane Mile Assumed in HERS by Type of Improvement" (Highway Investment Analysis Methodology, Appendix A, 2015 Conditions and Performance report, Exhibit A-1, fhwa.dot.gov/policy/2015cpr/appendixa.cfm). The values are in **thousands of 2012 dollars** and vary by road class, terrain (flat, rolling, mountainous) and city size. The figures were read from FHWA's page and from the same tables reproduced as Tables 15 and 16 (pp. 29–30) of *The Cost of Roadway Construction and Maintenance in New Jersey* (Rutgers/NJDOT, FHWA-NJ-2019-005, September 2019). The chart multiplies by lane count to get a per-mile figure. The 4-lane and 6-lane row labels ("suburban", "urban") are this tool's mapping onto HERS categories, a judgment call.

**Place matters, and HERS shows it by terrain and city size, not by state.** Rural minor arterial, new alignment: $1,966K (flat), $2,532K (rolling) and $5,900K (mountainous) per lane mile, so a 2-lane mile runs $3.9M, $5.1M or $11.8M. Urban freeway in a major urbanized area (population over 1 million) is $16,315K per lane mile at normal cost and $62,414K at high cost (tunnels, double-decking, expensive right-of-way). The chart shows the flat, normal-cost baseline, which is the low end.

**Dollar years.** The road rows are 2012 dollars, not inflated to 2026, because no construction-cost index was verified for the conversion. They therefore *understate* current road costs, which makes the comparison conservative for trails. Trail rows are 2026 dollars.

**Cross-checks (not used in the chart).** Ohio: the Portsmouth Bypass, a 16-mile four-lane limited-access highway, was reported at about $429 million in 2014 (ODOT / Portsmouth Gateway Group), about $26.8M per mile or $6.7M per lane mile; this is a proposal-stage figure, not an audited final cost. Hawaii: the Saddle Road (Daniel K. Inouye Highway) project covered nearly 48 miles for roughly $316.5 million per trade-press reports (about $6.6M per mile; arithmetic is this README's, and the lane count was not checked), with the U.S. Army contributing more than $100 million. Both sit above the flat-terrain HERS baseline for their size, which is consistent with the terrain and scope effects HERS describes.

**Paved path caveat.** $792K is a typical conceptual-level cost on an open corridor. Planning documents elsewhere put paved paths from roughly $0.55M to $0.8M per mile on simple corridors to $1.4M or more where the path sits beside a road or in an urban or constrained setting (search-result figures from Wichita, KS, Indiana DOT's 2019 trails memo and Chapel Hill, NC; not opened). "Closer to $1M per mile" is realistic for many real projects; the chart shows the documented typical figure.

**Range view.** The Typical / Range switch is switched off while the road ranges are loose (`HWY_RANGE_ENABLED` in `index.html`; set it to `true` to bring it back). The ranges stay in `INFRASTRUCTURE_COSTS`, built from the same HERS rows: 2-lane rural flat to mountainous; 4-lane from small urbanized normal to large urbanized high cost; 6-lane interstate from small urbanized normal to major urbanized normal.

**Earlier audit (superseded).** The previous road rows came from a Quora answer and a vendor blog and disagreed with each other by 4–10×; they are replaced by the HERS figures above. Brooks & Liscow (2023) remain a useful independent check: mean US Interstate construction was about $11.5M per mile in 2016 dollars over the 1956–1993 build-out, in line with the rural HERS interstate rows.

**Still open:** the volunteer-built row has no verified source, and the HERS figures could be refreshed from a newer edition or state DOT bid-price data.

The bar chart uses a logarithmic scale because the actual dollar differences span five orders of magnitude (roughly 10,000× from volunteer trail to urban interstate). Linear scaling would render trail costs invisible on the chart. The logarithmic transformation preserves the relative visual proportions while making all bars legible.

---


### Background textures

Each color theme also has its own background texture (the colors themselves are unchanged). The textures are masks hosted at `postmillenniumrenaissance.com/textures/masks/` (served with open CORS, so they work from a github.io iframe) and tinted with `--tex-ink`; two empty `<div class="texture">` / `<div class="texture-2">` elements sit at the top of `<body>` and the CSS lives in the "PMR BACKGROUND TEXTURES" block at the end of the stylesheet. The generator's declarations are unchanged and only scoped per theme.

| Theme | Texture | Source patent(s) |
|---|---|---|
| Ore Pass (default) | `day-1927-74141`, one seamless layer | US 74,141 (Day, 1927) |
| Gauntlet Gold | `fisher-1882-13110` fading left to right, `fisher-1882-13108` fading right to left | US 13,110 and 13,108 (Fisher, 1882) |
| Myers Flyer | `us-d268339` fading top to bottom, `crowe-1882-13106` fading bottom to top | US D268,339 (Inae and Fukuchi, Mitsuboshi Belting, 1983); US 13,106 (Crowe, 1882) |

- `isolation:isolate` on `<body>` is load-bearing: without it the body's own background paints over the `z-index:-1` texture and it disappears.
- Textures are hidden in print. The credit lines for the active theme's texture are shown in the line under the page content, after the related-tool button (`.tex-credit`); keep them when editing.
- **To give a new theme a texture:** copy a block in that CSS section, change the theme selector, `--tex-ink` and the mask files, and add its credit to `.tex-credit`. Keep opacity low; the text sits on top.
- The mask files load from the web, so with the page opened as a local file the textures appear only while online.

## 11. Contributing and Forking

This tool is intentionally simple: a single HTML file with no build process, no dependencies to install, and no server required. As of the June 2026 rebuild, that includes the charts — earlier versions loaded Chart.js from a CDN, which meant the four charts (and the printed report, which captures them as images) would silently fail if that CDN was ever blocked, down, or unreachable offline. All charting is now hand-written directly in the file: look for the "NO-DEPENDENCY CHART ENGINE" comment block in the JavaScript section. If you're forking this and want to add a new chart, that block has the shared pieces (canvas sizing, tooltip, entrance animation, axis gridlines) — you shouldn't need to touch a charting library's API, because there isn't one. Contributions are welcome.

**To suggest improvements:**
- Open an issue describing the change and its evidentiary basis
- If proposing a new economic factor, please cite at least two peer-reviewed or government-published sources

**Planned future enhancements (not yet implemented):**
- Healthcare cost savings module (with toggle)
- Event revenue module (with toggle)
- New resident attraction module
- Non-US spending benchmark presets (Australia, Canada, UK/EU) as alternatives to the US scenario defaults

**If you fork this for a specific community:**
Consider replacing the default slider values with pre-populated local data (assessor median home value, current tax rates, comparable trail visitor counts from the nearest regional system). The closer the defaults are to local reality, the more credible the tool will be when presented to decision-makers.

**Printing and the PDF report — notes for maintainers:**
The printed report (the `#rpt` block, filled by `buildReport()`) is a separate document layout from the on-screen page, not a restyled copy of it. The conventions below exist because each one fixed a real failure:
- *Charts are re-rendered offscreen, never screenshotted.* `capturePrintCharts()` re-runs each chart's own `render()` at a fixed size (`PRINT_CHART_SIZES`) and 3× resolution. Screenshotting the live canvases made chart size and text depend on the viewer's screen, and produced blank 1×1-pixel charts whenever the Partnerships panel had hidden them. Any new chart must resolve its colors **inside** `render()` (via `T()`), not once when it is created, or it will print in the screen palette; and it needs an entry in `PRINT_CHART_SIZES`.
- *Each theme carries a print palette* (`THEMES.<name>.print`) plus three print inks in its CSS block (`--r-accent`, `--r-sky`, `--r-callout`). To add a theme, supply all of them. Print rules: report text ≥ 7:1 contrast and ≥ 8pt; every chart line and solid fill ≥ 4.5:1 against white; the three donut tones ≥ 20 CIELAB-lightness apart so they stay distinct in grayscale; faint fills (below-cost bars, ramp-up bars) must carry a dark outline.
- *Color is never the only cue.* The three breakeven lines differ by dash pattern (`LINE_STYLE_PRINT`), bars are solid vs. hollow, and every chart has a legend and the donut a value table, so a black-and-white printout loses nothing.
- *Pages must each fit one sheet on the smaller of both papers* (7.27 in wide × 10 in tall of usable area, after the 0.5 in `@page` margins). Adding content to a page can silently push its footer onto an extra sheet — re-check the page count with the worst case (grant banner and currency banner both showing, Partnerships open) on both Letter and A4.
- *Partnerships content has one source.* The on-screen panel and the printed pages are both built from `WHY_FUNDING` (who-pays sources; add one entry to add a source), `whyFlags`, `whyTimeNote`, `whyLedgerRows` and `WHY_CAVEATS_HTML`. Change wording or a figure there, never in just one of the two. In print the funding bars carry a texture per source (`pattern`), because five colors alone merge on a black-and-white printer.
- *The QR code is generated in the file* (`qrEncode()`, byte mode, version 1–20, level M) rather than loaded from a CDN, to keep the tool zero-dependency and offline-capable. It is verified by decoding its output with an independent decoder over hundreds of random strings at every version, and by scanning a real printed PDF; repeat that if you touch it. It encodes the same link Copy Link produces (`reportShareURL()`), and is omitted when the page is not served over http(s).
- *Ctrl/Cmd+P works* because a `beforeprint` listener builds the report on demand; previously only the button did, and everything else printed a blank page.

**Updating the exchange rate fallback values:**
The hardcoded fallback rates in the `exRates` object near the top of the JavaScript section should be refreshed whenever you fork the tool for a new deployment. Find the line:

```javascript
let exRates={USD:1,AUD:1.4259,CAD:1.4062,EUR:0.8906,GBP:0.7476};   // plus FALLBACK_RATES_DATE just above it
```

Replace the values with current rates from any reliable source (Google Finance, XE.com, or the ECB). This ensures the fallback is reasonably accurate for users who open the tool offline or if the live rate feed becomes unavailable.

**Replacing the exchange rate API:**
If you need a more institutionally stable rate source — for example, for a government or university deployment — the European Central Bank publishes free daily exchange rates and has maintained public data access since the late 1990s. Replace the `fetchRates()` function's fetch URL with the ECB's data API endpoint and parse the response format accordingly.

---

## 12. Bibliography

The following studies, reports, and data sources directly informed the assumptions, benchmarks, and methodology used in this calculator. They are listed by category.

---

### Meta-Analyses and Literature Reviews

**Horn, J.T., et al. (2025).** *Economic Benefits of Mountain Biking.* Trust for Public Land (TPL) in partnership with the International Mountain Bicycling Association (IMBA). Washington, D.C.: Trust for Public Land. Link: https://nemba.org/sites/default/files/2025-04/green-paper-mtb.pdf (full PDF, hosted by NEMBA; opened October 2026)
- Primary source for visitor spending benchmarks ($103–$1,107/trip range; $416/trip national average)
- Source for labor income estimates (1,626 jobs / $54.1M labor income across 13 locations)
- Source for new resident attraction data (25% migration influence in Break O'Day Council, Tasmania)
- Meta-analysis of 50 individual studies across 13 trail systems

**Buning, R.J. & Lamont, M. (2021).** "Mountain bike tourism economic impacts: A critical analysis of academic and practitioner studies." *Tourism Economics*, 27(3), 500–509. DOI: 10.1177/1354816620901955. Link: https://doi.org/10.1177/1354816620901955 (publisher blocks automated checks; resolves from the DOI)
- Source for methodological critique of local vs. non-local spending conflation
- Reviewed 33 academic and practitioner studies; identified widespread inconsistency in variable measurement
- Informed the decision to separate local and out-of-town multiplier effects in this tool

**Crompton, J.L. & Nicholls, S. (2019).** "The Impact of Greenways and Trails on Proximate Property Values: An Updated Review." *Journal of Park and Recreation Administration*. Link: https://doi.org/10.18666/JPRA-2019-9906 (opened October 2026)
- Source for 3–5% property value premium as "most widespread outcome" for homes near trails
- Review of 20+ property value studies using hedonic price models
- Cited by NAR Field Guide on Trails and Property Values (2020)

---

### Regional and Destination-Specific Studies

**Savolt, A. (2017).** *Economic Impact of Off Road Cycling in Duluth: An Expenditures Approach.* University of Minnesota Duluth, University Honors Capstone Project / Undergraduate Research Opportunities Program. Faculty Advisor: Christopher McIntosh. Link: https://conservancy.umn.edu/items/ae2b41c8-92a4-4bde-9124-6ce2403e92a5 (University of Minnesota Digital Conservancy; blocks automated checks, found via search)
- Source for $103/day minimum spending benchmark (conservative scenario)
- Source for local vs. non-local separation methodology ($10.9–14.5M local; $25.8–34.4M non-local)
- Found total annual economic impact of $36.6–48.9M on a 70-mile network costing $6.1–7M to build

**Anderson, A., Harmsen, T. & Mahler, E. (2025).** *(Author list unverified: a search found Anderson and Harmsen named on the report and no "Mahler".)* *Maximising the Value of Mountain Biking Tourism to the Tasmanian Economy.* Episteme Consulting for Mountain Biking Network Tasmania (MTB-N). October 2025.
- Source for ramp-up period calibration (Blue Derby, Maydena Bike Park growth trajectories)
- Source for 25% migration influence data (Break O'Day Council survey)
- MTB visitors spend 26% more than regular holiday visitors to Tasmania
- Blue Derby: $50.9M direct expenditure, $26.6M value-added to state economy, 274 FTEs
- Maydena Bike Park: $49.8M direct expenditure, $28.1M value-added, 240.8 FTEs

**Walton Family Foundation / PeopleForBikes (2018).** *Bicycling Provides $137 Million in Economic Benefits to Northwest Arkansas.*
- Source for $8.7M annual avoided healthcare costs associated with MTB trails
- Source for $27M in bike tourism spending at local businesses annually
- 90,000+ mountain bike tourists in a 12-month period

**Bert, S. / Institute for Transportation Research and Education (ITRE), NC State University (2022).** *Economic Impact Assessment: Carolina Thread Trail.*
- Source for $1 invested = $1.72 additional annual impact (4 greenways, $26.7M investment)
- Documented 190 jobs per trail mile; $19.4M in local business sales; $684,000 in tax revenue
- Documented stormwater savings, carbon sequestration, and air quality benefits as monetizable trail values

**Vermont Business Magazine / TPL-IMBA (2025).** Kingdom Trails data cited in *Economic Benefits of Mountain Biking* (Horn et al., 2025).
- $10.3M annual economic impact from 94,000 visitors; $176/day average spending
- Documented use of trails as employee recruitment tool by Vermont businesses

**University of Wisconsin-Madison Extension (2014).** Study of the American Birkebeiner trail system (CAMBA trails).
- $26.4M regional economic impact from combined mountain biking and skiing

---

### Property Value Research

**National Association of Realtors (NAR) Library & Archives (2020).** *Field Guide to the Effects of Trails and Greenways on Property Values.* Washington, D.C.: NAR.
- Cited studies showing 3–5% property value premium; up to 15% in some cases
- Reviewed implications for property saleability and time-on-market

**Nicholls, S. & Crompton, J.L. (2005).** "The Impact of Greenways and Trails on the Value of Adjacent Properties." *Journal of Park and Recreation Administration*, 23(2), 35–55.
- Source for 5–10% premium finding in multiple study sites
- Foundational peer-reviewed source for trail-property value relationship

**Majors, J. & Burow, S. (2015).** *Assessment of the Impact of the Indianapolis Cultural Trail: A Legacy of Gene and Marilyn Glick.* Indiana University Public Policy Institute, report 15-C02, March 2015. https://archives.indianapolis.iu.edu/server/api/core/bitstreams/e2424f48-5496-420c-979e-4c91b85370fb/content (opened October 2026; coverage also at indystar.com and planetizen.com)
- Verified (pp. 24-26): gross assessed value of the 1,747 parcels within 500 feet of the 8-mile trail rose $1,013,544,460 from 2008 to 2014, a 148% increase.
- The authors caution that part of the rise is a return to pre-recession values that "likely would have occurred regardless of the Trail construction", and that some owners added amenities because of the trail. Read it as assessed value near a trail, not as a measured trail premium.
- **Mean per parcel is not a typical home.** The report gives a mean change of $580,180 per parcel ($1,013,544,460 / 1,747 = $580,163; the small difference is the report's rounding or parcel count). The parcels are commercial, lodging, residential, government and nonprofit properties, and **25 properties account for 68% of the increase** (the top ten are hotels, office towers and the Eli Lilly campus, each up $30.7M to $62.3M). A median or a residential-only figure is not in the report, so none is quoted.
- **No true control group.** The report compares each trail segment with the Census tract that contains it, and the tract includes the trail-side parcels themselves, so it is not an independent comparison. Results are mixed: Mass Avenue segment +58%, mean change $159,431 vs $94,622 for its tract; Fountain Square +31% vs +16% for its tract (mean $20,464 vs $8,568); but Fletcher Place segment mean $456,126 vs $518,480 for its tract, and Virginia Avenue segment mean $280,962 vs $526,400 for its tracts. Fletcher Place's tract includes the Eli Lilly campus and Anthem. No matched control parcels, no hedonic regression. The authors also say only two years separate the trail's completion from the last year of data.
- Also reports average expected trail-user expenditure of $53 and that 95% of surveyed users feel safe

**Seattle Engineering Department (1987).** *Evaluation of the Burke-Gilman Trail's Effect on Property Values and Crime.*
- Properties near (not adjacent to) the Burke-Gilman Trail sell for ~6% more; adjacent properties show 0–0.5% premium
- Early foundational study; methodology less sophisticated than modern hedonic models but directionally consistent with later research

**Karadeniz, D. (2008).** *The Impact of the Little Miami Scenic Trail on Single Family Residential Property Values.* Unpublished Master's Thesis, University of Cincinnati School of Planning.
- Each additional foot closer to the Little Miami Scenic Trail added ~$7 to home value

---

### Trail Construction and Maintenance Costs

**Singletracks.com (April 2026).** Heil, G., "How much does it cost to build a mountain bike trail?" Singletracks Mountain Bike News, first published April 15, 2026. https://www.singletracks.com/mtb-trails/how-much-does-it-cost-to-build-a-mountain-bike-trail/
- Verified against the page (October 2026): "$60,000-$80,000 per mile for a professionally-built trail in 2026. But it could be much, much more."
- Also gives a maintenance rule of thumb: budget 5% of the total installed cost per year (at least $4,000 per mile per year on an $80,000 build)
- An earlier version of this entry quoted a different article title; the title above is the one on the page

**American Trails (2007).** *Construction and Maintenance Costs for Trails*, excerpted from the Draft Milwaukee County Trails Network Plan (Milwaukee County Department of Parks, Recreation, and Culture, January 2007). https://www.americantrails.org/resources/construction-and-maintenance-costs-for-trails (page text checked October 2026 from a copy supplied by Jon)
- **Maintenance (routine, per mile per year):** $1,500 (Iowa DOT Iowa Trails 2000 plan, mixed surfaces); $2,525 (Milwaukee County Parks, all asphalt); $1,200 as an absolute minimum and $2,077 for government-run trails (Rails-to-Trails Conservancy maintenance manual); $2,042 per mile of unpaved trail (Wisconsin DNR draft cost model). So the page's range is about **$1,200 to $2,525**, mostly paved or mixed-surface trails. It does **not** give $5,000, and it is not a singletrack figure.
- **Construction (10-ft asphalt, Milwaukee area):** $149,206 to $301,014 per mile (Honey Creek, Root River, Kinnickinnic, Hank Aaron State Trail estimates: $149,206; $301,014; $176,470; $224,307).
- An earlier version of this README, and the tool, cited this page for "$1,500–$5,000/mile/year". The $5,000 upper bound was not on the page; the tool text now states the page's actual figures

**IMBA Trail Solutions / Rock Solid Trail Contracting (various projects, cited in Singletracks 2026).**
- Informed the understanding of variable cost drivers: terrain, features, rock armoring, drainage

---

### Highway and Road Infrastructure Costs

**Brooks, L. & Liscow, Z. (2023).** "Infrastructure Costs." *American Economic Journal: Applied Economics.* Cited at AEA Research Highlights, April 2023.
- Documents dramatic per-mile cost increases in US highway construction from 1956–1993
- Context for understanding why trail infrastructure provides exceptional value per dollar

**FHWA, Highway Economic Requirements System (2015 Conditions and Performance report, Appendix A, Exhibit A-1).** "Typical Costs per Lane Mile Assumed in HERS by Type of Improvement," thousands of 2012 dollars. fhwa.dot.gov/policy/2015cpr/appendixa.cfm.
- Source for the 2-lane, 4-lane and 6-lane road rows (see §10 for the exact rows and arithmetic)

**Carnegie, J. (2019).** *The Cost of Roadway Construction and Maintenance in New Jersey.* Rutgers Alan M. Voorhees Transportation Center for NJDOT, FHWA-NJ-2019-005. Tables 15–16, pp. 29–30 reproduce the HERS table above.

**NJDOT Transportation Alternatives Program (2024).** *Cost Estimate Guidelines and Recommendations for Pedestrian, Bicycle and Traffic Calming Projects.* Source for the paved multi-use path row ($150 per linear foot, 10-ft asphalt shared use path).

**Superseded and no longer used for the chart:** Midwest Industrial Supply (2018) blog ($4–6M/mile 4-lane, $7–11M/mile interstate) and a Quora compilation ($3–150M/mile ranges). They disagreed with each other and name no lane count, right-of-way assumption or dollar year.

**Federal Highway Administration (FHWA).** Highway History and Cost Documentation. fhwa.dot.gov.
- Historical reference: East River Drive in Manhattan ~$2M/mile (historical)

---

### Broader Outdoor Recreation Economy

**Bureau of Economic Analysis (BEA) (2024).** *Outdoor Recreation Satellite Account, United States, 2022.* U.S. Department of Commerce.
- Outdoor recreation economy: $1.2 trillion in output (2023); 2.3% of GDP
- Employs 5+ million workers; 3.1% of national workforce

**Technavio (2025).** *Mountain Bike Market Size, Share, Growth, Trends Report 2025–2035.*
- Mountain bike market CAGR: 8.91–8.92% from 2025–2035
- Market value: $13.3B (2024) → projected $33.9B (2035)
- Source for "Optimistic" visitor growth rate calibration

**Headwaters Economics (various).** *Outdoor Recreation Economy Research.* headwaterseconomics.org.
- Source for understanding amenity-driven population growth and "amenity trap" dynamics
- Population growth, employment, and salary data for communities near federal public lands

**American Heart Association (2011).** Literature review on trails and healthcare costs, cited in American Trails *Health Benefits of Trails.*
- $1 invested in trails → $3 in direct healthcare cost savings
- Source for the "not currently modeled" healthcare savings discussion

**Outdoor Industry Association (2019).** *Outdoor Recreation Participation Report.*
- Trail sports account for 3 of the 5 most popular outdoor recreation activities in the United States

**ITRE (Institute for Transportation Research and Education), NC State University (2018).** Economic impact study of greenways in Indiana.
- Source for "15 jobs facilitated per trail mile" finding cited in secondary sources

---

### Additional References Cited in the Tool

**San Luis Valley Great Outdoors (SLV GO) toolkit (c. 2021).** "C. Developing Trail Systems," pp. 61-68, including "Costs estimating for trail development." https://material-civet.files.svdcdn.com/production/images/documents/Developing-Trail-Systems.pdf?dm=1620062839 (supplied by Jon; read in full October 2026)
- Planning-level, Colorado San Luis Valley conditions, construction only: natural-surface singletrack typically $15,000-$40,000 per mile; under $5,000 per mile in the easiest case with skilled volunteers; over $100,000 per mile in difficult rocky terrain or with blasting; separately, planning, design and engineering *services* (inventory, assessment, concept plan, alignment design, specifications) are $1,500-$5,000 per mile, which is not a construction cost and is added on top of the build cost. Purpose-built MTB: flow trail $25,000-$40,000, flow trail with features $35,000-$70,000, downhill $20,000-$40,000. Pump tracks $12,000-$60,000 depending on size (relevant to the pump-track tool). Asphalt trail $13.50 per square yard (2 in.), concrete shared-use path $40 per square yard
- Shows the Singletracks $60,000-$80,000 figure is the high end of published professional-build costs, not the whole range

**Next Level Trails Real Estate Guidelines & Procedures Handbook (Indiana DNR, April 2020).** Supplied by Jon while looking for the NAR Field Guide. It is a land-acquisition handbook for a grant program and contains no property-value findings, so it does **not** support the 3-5% property premium and is not cited for it. The NAR *Field Guide to the Effects of Trails and Greenways on Property Values* (2020) is still not located; the 3-5% range rests on Crompton & Nicholls (2019).

**Independent Sector (2025).** *Value of Volunteer Time* (2024 national figure: $34.79 per hour, released April 2025 with the University of Maryland Do Good Institute). https://independentsector.org/volunteer_time (publisher blocks automated checks; found via search)
- Source for the volunteer-labor rate in the Partnerships panel

**National Association of Homebuilders (2016), cited in Trail Impact Series: Economies, University of Connecticut CLEAR.**
- Study of 4,300 home buyers: proximity to parks and walking/jogging trails among most desired amenities across age groups

**Break O'Day Council (2025).** Survey results cited in Anderson et al. (2025).
- ~25% of people moving to the area influenced by MTB trail network

**West Virginia University / Brad and Alys Smith Outdoor Economic Development Collaborative.** *Ascend WV and First Ascent WV programs.*
- Documented workforce attraction through outdoor recreation access

**Carolina Thread Trail (2022).** carolinathreadtrail.org.
- Documents role of trails in attracting young professionals; cited in site selector reports for business development

---

*This README was written to accompany version 2.2 of the Trail Investment ROI Calculator (June 2026). Version 2.2 removes the tool's last external JavaScript dependency: all four charts (breakeven line chart, benefit-breakdown donut, milestone bars, visitor bars) are now drawn with hand-written canvas code instead of loading Chart.js from a CDN, so the tool runs correctly fully offline with zero network access, including chart rendering, animation, and the printed PDF report. This version also adds a sequential reveal animation to the breakeven chart (Total Cost, then Municipal Revenue, then Economic Impact draw in order on load and on every assumption change) and makes the infrastructure cost comparison card collapsible. Version 2.1 added the International Settings panel: metric/imperial/both unit toggle, and currency display conversion (USD, AUD, CAD, EUR, GBP) with daily-updated exchange rates via CDN. The calculator remains a single-file HTML tool requiring no installation. It is intended for use by trail advocates, municipal planners, parks directors, and community decision-makers. All dollar figures reflect nominal USD as of the cited study dates; users should apply their own inflation adjustments when comparing studies from different years.*

*Prepared with research support from the TPL/IMBA Economic Benefits of Mountain Biking report (2025), the IMBA Investing in Trails study collection, and additional peer-reviewed and practitioner literature as cited above.*
