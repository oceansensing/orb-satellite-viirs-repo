# orb-satellite-viirs-repo: the founding plan and running record

The University of Delaware ORB lab's **VIIRS** anomaly products. Created on GitHub by the owner and given its documents by the site's
`pipeline/scaffold/new-origin.py`. **Nothing is published yet.**

## What it is for

Two fields from ORB's experimental VIIRS 8-day anomaly composite (`viirs_chl_anomaly_8day`), over 16-52 N, 100-50 W: the **chlorophyll-a anomaly** (`chlanom-viirs.json`, mg m-3) and the **sea surface temperature anomaly** (`ssta-viirs.json`, degrees C), each a linear difference from ORB's climatology, regridded to 0.04 degree with `regional: true` and `windowDays: 8`.

## Where the data comes from

The University of Delaware's Ocean Remote sensing laboratory (ORB) serves its processed products openly from its own ERDDAP, `https://basin.ceoe.udel.edu/erddap`, with no login. Every dataset there carries the same license text: the data *"may be used and redistributed for free but is not intended for legal use, since it may contain inaccuracies"*. More of that server's products are expected to join (the owner, 2026-09-27), which is why the site's fetcher, `scripts/fetch-erddap.py`, is written for the server and takes a product as a row. **Read 2026-09-27**: `viirs_chl_anomaly_8day`, creator Matthew Oliver, 4500 x 5000 at 0.008 degree latitude by 0.01 longitude, one 8-day composite per day since 2018-01-01. The newest day was 5.7 days old that afternoon, and 4 of the 33 days before it were missing. Chlorophyll anomaly p1 -6.4, median 0.00, p99 +0.84 mg m-3 (coastal tails to +/-97); SST anomaly p1 -3.1, p99 +3.3 degrees C; 53% of cells hold a value.

## Open

1. Re-measure `max_age_hours` after a week of scheduled runs.
2. The server's other products, as the owner names them.
