# Methodology

## Data Source

This dataset is compiled from Myanmar's General Administration Department (GAD) administrative division records, supplemented by open geographic data sources.

## Processing

1. Source data is parsed and validated against the JSON Schema
2. Parent references, ancestor chains, and children counts are computed
3. English slugs are generated for URL-safe folder naming
4. Multi-format export: JSON, NDJSON, CSV
5. Hierarchy folder structure with READMEs generated via EJS templates

## Update Frequency

Data is updated when significant administrative boundary changes occur.

## Accuracy

- All division names, codes, and hierarchy relationships come directly from source data
- Statistics are computed from data, never hardcoded
- Build script is idempotent: same input always produces same output