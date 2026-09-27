# orb-satellite-viirs-repo

The University of Delaware ORB lab's **VIIRS** anomaly products: a data repository of the oceansensing ocean map system, with its own
Pages site, its own schedule and its own gigabyte, and no code of its own.

**Nothing is published yet.** `PLAN.md` is the founding plan; `CLAUDE.md` carries what must not be
got wrong and the shared doc doctrine.

## What it publishes

Two fields from ORB's experimental VIIRS 8-day anomaly composite (`viirs_chl_anomaly_8day`), over 16-52 N, 100-50 W: the **chlorophyll-a anomaly** (`chlanom-viirs.json`, mg m-3) and the **sea surface temperature anomaly** (`ssta-viirs.json`, degrees C), each a linear difference from ORB's climatology, regridded to 0.04 degree with `regional: true` and `windowDays: 8`.

These products are published **operationally but not drawn on the website's map**; the map's status
line still reports them when they fall behind, which is how their health stays visible.

## Where the data comes from

The University of Delaware's Ocean Remote sensing laboratory (ORB) serves its processed products openly from its own ERDDAP, `https://basin.ceoe.udel.edu/erddap`, with no login. Every dataset there carries the same license text: the data *"may be used and redistributed for free but is not intended for legal use, since it may contain inaccuracies"*. More of that server's products are expected to join (the owner, 2026-09-27), which is why the site's fetcher, `scripts/fetch-erddap.py`, is written for the server and takes a product as a row. **Read 2026-09-27**: `viirs_chl_anomaly_8day`, creator Matthew Oliver, 4500 x 5000 at 0.008 degree latitude by 0.01 longitude, one 8-day composite per day since 2018-01-01. The newest day was 5.7 days old that afternoon, and 4 of the 33 days before it were missing. Chlorophyll anomaly p1 -6.4, median 0.00, p99 +0.84 mg m-3 (coastal tails to +/-97); SST anomaly p1 -3.1, p99 +3.3 degrees C; 53% of cells hold a value.

## How it runs

The orchestrator (the site's private `pipeline/`), the fetchers and the
published-file contract all come from `oceansensing.github.io`, checked out at
run time. This repository carries `pipeline/products.toml` and its publish
workflow, and nothing else executable. Each run publishes to GitHub Pages and
to Cloudflare R2 from one build. Related repositories: the other University of Delaware ORB repositories, `orb-satellite-viirs-repo`, `orb-satellite-goes-repo` and `orb-satellite-pace-repo`.

**Which document gets what, and what "update docs" means across all
twenty repositories, is the doctrine block at the top of `CLAUDE.md`**: the
same text in all twenty, held equal by the site's `check:docs`.

## Structure

```
README.md       what this is
CLAUDE.md       what must not be got wrong, and the shared doc doctrine
PLAN.md         the founding plan and running record
DECISIONS.md    dated one-way decisions, D1 onward
pipeline/       products.toml, the declaration the orchestrator reads
.github/        the publish workflow
```
