# Pipeline Explanation: E-commerce Analytics Pipeline

## The Business Scenario

An e-commerce company wants a daily dashboard showing:
- Sales by hour
- Top products
- Customer acquisition by channel

## The Pipeline (Step by Step)

### Step 1: Source Systems
Data comes from multiple places:
- Transactional database (PostgreSQL) – orders, customers, products
- Web analytics tool (Google Analytics) – page views, sessions
- Marketing platform (Facebook Ads) – campaign spend

### Step 2: Extraction
Each morning at 2:00 AM, an orchestration tool (like Airflow or Azure Data Factory):
- Connects to each source system
- Pulls data from the previous day only
- Stages raw data in cloud storage (Azure Blob Storage or S3)

### Step 3: Transformation
A transformation tool (like dbt or Azure Synapse):
- Cleans the data (removes nulls, standardizes formats)
- Joins tables (e.g., orders + customers + products)
- Calculates metrics (e.g., revenue per customer, conversion rate)
- Writes transformed data to a data warehouse (Snowflake)

### Step 4: Loading
The final, clean, aggregated data is stored in Snowflake. This is the single source of truth for reporting.

### Step 5: Visualization
Power BI connects directly to Snowflake. The dashboard refreshes automatically at 6:00 AM, so executives see yesterday's data when they arrive.

## What Can Go Wrong (Risks I Would Manage as a PM)

| Risk | Impact | Mitigation |
|------|--------|-------------|
| Source API changes | Extraction fails | Build monitoring; have vendor contact ready |
| Data volume grows | Pipeline runs longer than window | Partition data; consider incremental loads |
| Transformation logic wrong | Wrong numbers in dashboard | Unit tests; peer review before deployment |
| Snowflake outage | No dashboard refresh | SLA with Snowflake; backup connection |

## Why This Matters for a Project Manager

I do not need to build this pipeline. But I need to:
- Explain it to stakeholders who ask "why does it take so long?"
- Estimate how much effort a new data source will add
- Ask engineers: "Is this batch or real-time?" "What is our SLA?"
- Recognize when a project risk is technical vs non-technical
