# Columbus data

Automatically refreshed exports of the Columbus data service (free mode, GitHub Actions),
in the formats the Columbus Atlas prototype (Solkarte) reads.

- `latest/` - current files (replaced on every successful run)
- `archive/YYYY-MM-DD/` - files of each successful run (height maps only when they changed)
- `state/` - manifest of the service state (the state itself is a release asset)

Every value carries provenance: see `catalogue.provenance.json`, the `provenance` block in
`spacecraft.json`, the height-map `.json` files and `status.json`. Missing values are empty,
never estimated. A run whose plausibility checks fail publishes nothing.

## Files

| file | content |
|---|---|
| `catalogue.csv` | asteroids; prototype columns (epoch = JD TDB) + condition_code |
| `catalogue.provenance.json` | per-row source dataset and epoch |
| `spacecraft.json` | heliocentric ecliptic J2000 positions (au), spacecraft + references |
| `heightmap_*.png` / `.json` | lunar south-pole height maps (RGB-encoded heights) and metadata |
| `status.json` | job outcomes and data state per source |

## Sources

- NASA/JPL Solar System Dynamics: SBDB Query and Lookup APIs, Close-Approach Data (CAD) API,
  Horizons API, NHATS API - https://ssd-api.jpl.nasa.gov
- NASA PGDA product 81, LOLA 5 m/px south-pole mosaic; Barker et al. 2021,
  doi:10.1016/j.pss.2020.105119 - https://pgda.gsfc.nasa.gov/products/81
- IAU Gazetteer of Planetary Nomenclature (crater reference for plausibility checks)

## Licence

LICENCE PLACEHOLDER - to be decided. The upstream terms of the sources above apply to the data.

## Data state (run 2026-11-01T00:07:43.370170+00:00)

| source | version | finished (UTC) | records | newest run |
|---|---|---|---|---|
| sbdb | 1 | 2026-10-31T23:41:06.345484 | 536 | succeeded |
| cad | 2 | 2026-11-01T00:04:57.441919 | 3175 | succeeded |
| horizons | 2 | 2026-11-01T00:05:16.367703 | 7679 | succeeded |
| horizons_elements | 1 | 2026-10-31T23:45:02.703039 | 211 | succeeded |
| nhats | 1 | 2026-10-31T23:41:10.634443 | 7164 | succeeded |
| pgda_lola | 1 | 2026-11-01T00:07:42.572393 | 1 | succeeded |
