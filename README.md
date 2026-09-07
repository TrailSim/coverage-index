# TrailSim Coverage Index — open dataset

Mobile network coverage along **61 famous hiking trails, cycling routes and road trips**
(47,448 km analysed), modelled from public signal data and published by
[TrailSim](https://trailsim.com).

- Interactive, always-current version: **https://trailsim.com/coverage-index**
- This repository mirrors the CSV for citation, diffing and programmatic use.
- Machine-readable summary for AI assistants: https://trailsim.com/llms.txt

## What's in the data

One row per analysed route ([`data/coverage-index.csv`](data/coverage-index.csv)):

| Column | Meaning |
| --- | --- |
| `route` | Route name |
| `countries` | Countries the route crosses |
| `km_analysed` | Route length analysed, km |
| `usable_4g5g_pct` | Share of the route with usable 4G/5G data (%) |
| `any_signal_pct` | Share with any signal, including 2G/3G (%) |
| `dead_zones` | Continuous stretches ≥ 2 km with no signal from any compared network |
| `dead_zone_km` | Total length of those dead zones, km |
| `mountain_estimate` | `yes` = tower-position estimate without terrain modelling — treat coverage figures as upper bounds |
| `data_source` | Primary source for this route (see below) |
| `methodology_version` | Model version identifier |
| `url` | The route's page, with stage-by-stage tables and named dead zones |

Figures use each route's **highest-coverage network combination**. Percentages are
estimates, not guarantees; every route page states its own data snapshot date.

## Methodology (short version)

Route geometry from OpenStreetMap is sampled every 500 m and each sample is
classified against public signal data — the source chosen per route:

- **OpenCellID** crowd-sourced cell-tower locations (radius model, no terrain line-of-sight)
- **FCC National Broadband Map** provider propagation filings (US routes)
- **Ofcom** drive-test measurements (UK routes)
- **ACMA** Register of Radiocommunications Licences (Australian routes)

Stretches no survey ever visited are marked *not surveyed*, never presented as
*no signal*. High-relief routes flagged `mountain_estimate = yes` publish their
figures as explicit upper bounds. Full methodology: https://trailsim.com/how-it-works

## Licence and attribution

**CC BY-SA 4.0** — free to reuse, republish and build on, including commercially,
provided you credit **TrailSim** with a link to https://trailsim.com/coverage-index
and share derivatives under the same licence. See [LICENSE](LICENSE).

Underlying sources retain their own terms: OpenCellID (CC BY-SA 4.0),
OpenStreetMap (ODbL), FCC (public domain), Ofcom open data, and material based on
Australian Communications and Media Authority information.

## Questions, corrections, custom cuts

Field reports that contradict the model are especially welcome —
**support@trailsim.com**, or open an issue here.
