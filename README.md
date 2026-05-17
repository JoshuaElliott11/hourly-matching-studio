# Hourly Matching Studio

A single-page web app for comparing **annual** versus **24/7 hourly** carbon-free matching for any portfolio of on-site renewables, PPAs, battery storage, and grid supply.

Live site: https://joshuaelliott11.github.io/hourly-matching-studio/

## What it does

Most corporate clean-energy claims today are scored annually: total MWh of renewable certificates against total MWh of consumption. Under the GHG Protocol Scope 2 revision (final standard expected 2027) and SBTi V2 (mandatory for new net-zero targets from 1 January 2028), the reportable figure is shifting to **hourly matching**: clean supply delivered in the same hour as load.

This app lets you:

- Load one of six pre-built scenarios that contrast the two methodologies (e.g. a 100% annual claim that collapses to 35% under hourly scoring)
- Adjust load, on-site solar, wind, battery, gas CHP, PPA volume and shape, grid CO₂ intensity, and carbon price
- Upload your own hourly load profile (CSV, 8,760 rows)
- See annual %, hourly %, residual emissions, and carbon-priced exposure
- Inspect a stacked dispatch chart, monthly comparison bars, hour-of-day × month heatmap, average daily shape, cumulative emissions, and a coverage-band histogram
- Export a print-ready PDF report and a CSV of the 8,760-hour simulation

## How to use it

1. Open the live site (or `index.html` locally in any modern browser)
2. Click a scenario card at the top
3. Adjust any of the sliders and dropdowns in the configuration panel
4. Click **Run simulation**
5. Use **Export report (PDF)** or **Download CSV** for offline use

No build step, no server, no dependencies beyond Chart.js loaded from a CDN.

## Disclaimer

This is a personal exploratory project. **It is not a production tool, not a certified accounting platform, and not affiliated with the GHG Protocol, SBTi, EnergyTag, or any regulator.**

- All generation profiles (solar, wind, load) are produced from deterministic mathematical models, not real measured data
- Capacity factors, dispatch logic, battery efficiency, and grid intensity shapes are simplified
- Pre-built scenarios are illustrative, designed to demonstrate the annual-vs-hourly contrast, not to represent any real site
- Numbers from this app should not be used in regulatory filings, CDP submissions, SBTi disclosures, or any document where accuracy matters

Treat it as a teaching tool for the concept of hourly matching, not as a calculator.

## Methodology summary

- **Annual matching**: Σ(clean energy procured) ÷ Σ(load), capped at 100%
- **Hourly matching**: Σ min(clean_h, load_h) ÷ Σ load_h, load-weighted
- **PPA shapes**: firmed baseload counts in every hour; solar-shaped, wind-shaped, and distant-solar (8-hour timezone offset) count only when the underlying generator is producing
- **Dispatch order**: on-site renewables → battery (charged only from clean surplus, 90% round-trip) → gas CHP → grid
- **Emissions**: hourly grid intensity (with configurable shapes) × grid MWh, plus gas CO₂ factor × gas MWh

## Background reading

- GHG Protocol Scope 2 public consultation (October 2025): https://ghgprotocol.org/blog/upcoming-scope-2-public-consultation-hourly-matching-and-deliverability
- EnergyTag (granular certificate standards): https://energytag.org/
- 24/7 Carbon-Free Energy Compact: https://www.un.org/en/energycompact/page/247-carbon-free-energy-compact
- SBTi Corporate Net-Zero Standard V2 draft

## Licence

MIT. See `LICENSE`.
