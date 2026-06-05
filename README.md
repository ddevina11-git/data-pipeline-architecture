# Data Pipeline Architecture Diagram & Explanation

## About This Repository

This repository shows my understanding of how data moves from source systems to dashboards. I am not a Data Engineer who builds pipelines daily, but as a Data Project Manager I need to understand the moving parts, trade-offs, and common terminology.

## What This Repository Contains

| File | Description |
|------|-------------|
| `architecture_diagram.png` | Simple diagram of an example data pipeline |
| `pipeline_explanation.md` | Plain English walkthrough of each component |
| `tool_rationale.md` | Why I would choose certain tools for different scenarios |

## My Understanding of Data Pipelines

I understand the following concepts at a high level:
- Extraction (getting data from source systems)
- Transformation (cleaning, joining, aggregating)
- Loading (moving data to a warehouse or lake)
- Batch vs real-time processing
- ELT vs ETL approaches

I cannot build a production pipeline from scratch, but I can:
- Read a pipeline diagram and explain each step
- Ask engineers intelligent questions about bottlenecks
- Estimate timeline impact of adding new data sources
- Understand why a pipeline might break
