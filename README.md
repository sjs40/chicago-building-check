# chicago-building-check — data files

Machine-readable data for [Chicago Building Check](https://github.com/sjs40/chicago-building-check),
aggregated from the City of Chicago's public **Building Violations** dataset
(Department of Buildings, Socrata `22u3-xenr`, updated daily).

Served to the live site via jsDelivr:
- `https://cdn.jsdelivr.net/gh/sjs40/chicago-building-check@main/data/buildings_top2000.json`
- `https://cdn.jsdelivr.net/gh/sjs40/chicago-building-check@main/data/stats.json`

## Files

- `data/buildings_top2000.json` — top 2,000 buildings **ranked by unresolved
  violations cited in the last 5 years** (raw lifetime open counts included per
  building). Per building: address, lat/lon, open / open-recent / complied /
  total counts, first/last violation dates, last inspection year, violations by
  year, top inspection categories, 10 most recent violations.
- `data/stats.json` — global stats (total rows, distinct buildings, open count,
  date range, recency cutoff used for ranking).
- `llms.txt` — dataset description + citation guidance for AI search.

## Staleness note

Violation statuses reflect the city's last recorded status and can be stale for
older records. Rankings weight recent violations (last 5 years) more heavily;
raw open counts are directional, not gospel.

## Regenerating

Built from `pipeline/` in the private build workspace (download.py →
aggregate.py over parquet parts). Re-run the pipeline and push the refreshed
JSONs here; the live site picks them up via jsDelivr (CDN cache can lag a few
minutes — purge at https://www.jsdelivr.com/tools/purge if needed).
