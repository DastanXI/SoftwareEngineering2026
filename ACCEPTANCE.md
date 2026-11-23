# Acceptance criteria (must remain true after every change)

| ID  | Criterion | Covered by |
|-----|-----------|------------|
| AC1 | An added expense is persisted to the data file and reloaded intact. | `test_add_persists_and_reloads` |
| AC2 | `total()` equals the sum of all stored amounts. | `test_total_is_sum` |
| AC3 | `summary()` returns correct per-category totals. | `test_summary_by_category` |
| AC4 | `export` supports `csv`, `json`, `text` with the documented layout; unknown format is rejected by the CLI with exit code 1. | `test_export_formats`, `test_cli_unknown_format` |
| AC5 | CLI `add` and `total` exit 0 on valid input. | `test_cli_add_and_total` |
