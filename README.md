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
| `catalogue.csv` | asteroids; prototype columns (epoch JD TDB), condition_code, transfers |
| `catalogue.provenance.json` | per-row source dataset and epoch; transfer method and grid |
| `spacecraft.json` | heliocentric ecliptic J2000 positions (au), spacecraft + references |
| `heightmap_*.png` / `.json` | lunar south-pole height maps (RGB-encoded heights) and metadata |
| `heightmap_*_layers.png` / `.json` | illumination, Earth visibility, slope (RGBA) + metadata |
| `heightmap_*_psr.png` | permanently shadowed regions (255 = PSR) |
| `status.json` | job outcomes and data state per source |

## Sources

- NASA/JPL Solar System Dynamics: SBDB Query and Lookup APIs, Close-Approach Data (CAD) API,
  Horizons API, NHATS API - https://ssd-api.jpl.nasa.gov
- NASA PGDA product 81, LOLA 5 m/px south-pole mosaic; Barker et al. 2021,
  doi:10.1016/j.pss.2020.105119 - https://pgda.gsfc.nasa.gov/products/81
- IAU Gazetteer of Planetary Nomenclature (crater reference for plausibility checks)
- NASA PGDA product 90, LOLA DEM 80-90 S (LDEM_80S_80MPP_ADJ), context terrain for
  horizons - https://pgda.gsfc.nasa.gov/products/90
- NAIF SPICE generic kernels (DE440s, lunar orientation DE421) for Sun/Earth
  directions - https://naif.jpl.nasa.gov
- Transfer columns: computed by Columbus (Lambert two-body, prototype conventions) from the
  stored element sets; see `reach_method` in `catalogue.provenance.json`

## Licence

LICENCE PLACEHOLDER - to be decided. The upstream terms of the sources above apply to the data.

## Data state (run 2026-11-04T10:52:26.371008+00:00)

| source | version | finished (UTC) | records | newest run |
|---|---|---|---|---|
| sbdb | 2 | 2026-11-02T10:58:51.115948 | 536 | succeeded |
| cad | 6 | 2026-11-04T10:52:07.256349 | 3177 | succeeded |
| horizons | 6 | 2026-11-04T10:52:26.105074 | 7746 | succeeded |
| horizons_elements | 2 | 2026-11-02T10:59:15.550617 | 0 | succeeded |
| nhats | 2 | 2026-11-02T10:58:55.098040 | 7165 | succeeded |
| pgda_lola | 1 | 2026-11-01T00:07:42.572393 | 1 | succeeded |
| reach | 2 | 2026-11-02T11:01:00.844717 | 327 | succeeded |
| moon_layers | 1 | 2026-11-01T01:40:37.026231 | 1700416 | succeeded |
