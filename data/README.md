# Data Structure

medallion architecture convention

![medallion data architecture](https://databricks.com/wp-content/uploads/2020/06/medallion-architecture.png)

| `Folder in data` | `Description` |
| ---------------------- | --- |
| `bronze/`       | The raw ingestion layer. Contains data ingested from source systems in its original, unmodified format. This layer ensures traceability and auditability. Typically stored as CSV, JSON, Parquet, or any semi-structured format. Data here may contain duplicates, nulls, and untyped values. No business logic is applied. |
| `silver/`       | The refined transformation layer. Contains cleaned, typed, and validated data derived from the bronze layer. Business rules are applied here such as type casting, null handling, deduplication, normalization, and enrichment. The output of this layer serves as input to analytical processes and model training. |
| `gold/`         | The curated business-level layer. Contains data that is aggregated and optimized for analytics, reporting, and model consumption. Gold datasets are designed to answer specific business questions or serve as feature-ready data sources. These are typically consumed by dashboards, ML models, or decision support tools. |

---

## Layered Purpose

- 🥉 **Bronze Layer**: Immutable and auditable source of truth.
- 🥈 **Silver Layer**: Cleaned, validated, and semantically enriched.
- 🥇 **Gold Layer**: Final stage for consumption by ML/BI, highly structured and business-aligned.

---

## Best Practices

- Ensure that each layer has clear lineage and reproducibility.
- Avoid back-editing data in the bronze layer.
- Use versioning or time-partitioning for traceability and reprocessing.
- Maintain schema documentation per layer for discoverability and governance.

---

## References

- [Medallion Architecture - Databricks](https://www.databricks.com/glossary/medallion-architecture)
- [Delta Lake Design Patterns](https://www.databricks.com/blog/2020/06/30/modern-data-engineering-with-delta-lake.html)
- [Lakehouse Architecture](https://docs.databricks.com/lakehouse/index.html)
