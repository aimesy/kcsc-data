# KCSC data repository instructions

- This repository contains public KCSC archive payloads and derived data products.
- Commit `archive/cases/*.json`, `archive/cases-index/`, `data/*.parquet`, `data/manifest.json`, and `data/normalization-summary.json`.
- Do not commit credentials, saved browser storage state, cookies, raw browser profiles, logs, or `/etc/kcsc` contents.
- Do not commit mutable VPS runtime directories. Raw NDJSON export pointers belong on the VPS unless a future task explicitly promotes them as public source artifacts.
- Regenerate this repository from `/srv/kcsc` with `scripts/normalize_cases.py`, then update `data/manifest.json` and the sharded `archive/cases-index/` with `scripts/build_data_manifest.py`.
