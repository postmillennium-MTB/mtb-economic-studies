# Trail Investment ROI Calculator: working notes for Claude

A single-file tool (`index.html`): markup, CSS, JavaScript and data in one file, no build step and no dependencies. Part of Post Millennium Renaissance; it runs inside an iframe on postmillenniumrenaissance.com/roi/. See the `pmr-build-standard` skill for architecture and audit rules.

## Who you are working with

Jon has no coding background and edits through GitHub's web UI. Deliver complete files, not diffs. Name what a choice costs, not only what it buys. Ask before restructuring.

## Sourcing

Never invent a figure or a URL. A gap beats a guess. Every benchmark traces to a named source (README sections 7 and 12). Say plainly when a figure is an estimate or a judgment pick.

## Kept in step with the other copy of the Why / Partnerships model

The Partnerships comparison (Option 1 municipal-only vs Option 2 with a non-profit) exists in two tools that are maintained separately and must not drift apart:

| Tool | Repo | Where it lives |
|---|---|---|
| Trail Investment ROI Calculator | `postmillennium-MTB/mtb-economic-studies` | the **Partnerships** button and panel |
| Trail Advocacy Atlas | `postmillennium-MTB/Trail-Advocacy-Atlas` | the **Why** tab (`#why`) |

**What must stay identical in both:**
- `computeWhy()`: the cost model. As of October 2026 the two copies are identical apart from comments and quote style.
- `WHY_INPUTS`: every slider's `min`, `max`, `step` and `value`. Also identical as of October 2026. Hint wording may differ, but any figure quoted in a hint may not.
- The funding-source and warning-flag rules (the ROI Calculator keeps them in `WHY_FUNDING` and `whyFlags`; the Atlas implements the same logic inside its own render code and has no such registries).
- Sourced figures: professional singletrack **$60,000–$80,000 per mile** (Singletracks.com contractor survey, April 2026), routine maintenance **$1,500–$5,000 per mile per year** (American Trails), volunteer time **$34.79/hr** (Independent Sector, 2024).
- The caveats section heading, **"Data sources & methodology notes"**, and the substance of its paragraphs (the ROI Calculator shows it as a fold, the Atlas as a section).

**What is allowed to differ:** layout and styling, the surrounding page chrome (the ROI Calculator's scenario buttons, currency and unit switcher and print report do not exist in the Atlas), and sentence-level wording that does not change a figure or a claim.

**Rule for every session:** if you change anything in the lists above in one repo, say so in your handover and either make the same change in the other repo in the same working session or tell Jon exactly what is left to port. Never fix a figure or a source in one copy and leave the other stale. Before a PR that touches the Why / Partnerships model, compare `computeWhy()` and the `WHY_INPUTS` numbers against the other repo.

