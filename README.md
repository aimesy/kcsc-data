# KCSC canonical data

Generated cross-court data contract output for King County Superior Court.

- `archive/cases/<case_number>.json` contains one canonical JSON document per case.
- `archive/cases-index.ndjson` is the compact case startup index.
- `data/*.parquet` contains flat derived tables built from the canonical JSON.
- `data/manifest.json` lists current table paths, counts, and byte sizes for
  static viewers.

Document byte capture is not implemented yet for KCSC. The current normalizer
does not emit `documents.parquet`; raw KCSC document-list rows are preserved in
canonical JSON under `kcsc.document_rows_deferred`.

Typical command from `/srv/kcsc`:

```bash
/srv/kcsc/.venv/bin/python scripts/normalize_cases.py \
  --input /srv/kcsc-data/raw \
  --archive /srv/kcsc-data/archive/cases \
  --out /srv/kcsc-data/data
python scripts/build_data_manifest.py --data-root /srv/kcsc-data
```

Current generated counts:

- `archive/cases/*.json`: 822 canonical cases.
- `archive/cases-index.ndjson`: 822 rows.
- `data/cases.parquet`: 822 rows.
- `data/docket_entries.parquet`: 3,545 rows.
- `data/parties.parquet`: 366 rows.
- `data/attorneys.parquet`: 269 rows.
- `data/representation.parquet`: 271 rows.
- `data/calendar.parquet`: 501 rows.
- `data/payments.parquet`: 0 rows with schema.
- `data/documents.parquet`: intentionally not emitted until KCSC document byte capture exists.
