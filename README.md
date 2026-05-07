# Supplier Performance Analytics Accelerator

## Overview

The **Supplier Performance Analytics Accelerator** is a comprehensive supply chain intelligence platform that enables procurement and operations teams to monitor, score, and optimize supplier performance across delivery, quality, cost, and risk dimensions.

Built on Snowflake with Cortex AI, this accelerator provides real-time supplier scorecards, predictive cost forecasting, and intelligent root-cause analysis — all within your Snowflake environment.

## Key Features

- **Supplier Scorecards & Risk Classification** — Composite scoring across OTD, quality, cost, and fill rate with automatic risk categorization (HIGH/MEDIUM/LOW)
- **Delivery & Lead Time Analysis** — Track on-time delivery, delay patterns, carrier performance, and production impact by plant
- **Quality Analytics** — Defect type distribution, severity tracking, root cause clustering, and corrective action analysis
- **Cost & Benchmarking** — Spend concentration (HHI), freight analysis, supplier cost efficiency, and monthly spend trends
- **Predictive Forecasting** — 4-year forward spend outlook by category with ML-powered or trend-based projections
- **AI-Powered Insights** — Natural language analysis of your supply chain data using Snowflake Cortex

## Required Tables

After installation, bind the following 5 tables via the app's configuration page:

| Reference | Description | Key Columns |
|-----------|-------------|-------------|
| `FACT_SUPPLIER_SCORECARD` | Composite supplier scores and KPIs | SUPPLIER_ID, SUPPLIER_SCORE, RISK_CATEGORY, ON_TIME_DELIVERY_PCT, AVG_DEFECT_RATE_PCT |
| `FACT_DELIVERY` | Shipment tracking and delay data | TRACKING_ID, SUPPLIER_ID, DELAY_DAYS, IS_ON_TIME, ESTIMATED_LOSS_USD |
| `FACT_QUALITY` | Quality inspections and defects | INSPECTION_ID, SUPPLIER_ID, DEFECT_TYPE, SEVERITY, ROOT_CAUSE, PASS_FAIL |
| `FACT_PURCHASE_ORDERS` | Purchase orders and costs | PO_ID, SUPPLIER_ID, TOTAL_COST, FREIGHT_COST, FILL_RATE_PCT |
| `DIM_SUPPLIER` | Supplier master data (SCD Type-2) | SUPPLIER_ID, SUPPLIER_NAME, SUPPLIER_TIER, CATEGORY, REGION, IS_CURRENT |

## Installation Steps

1. **Install the app** from the Marketplace listing
2. **Grant privileges** — Grant the `SNOWFLAKE.CORTEX_USER` database role to the app for AI Insights (optional)
3. **Bind your tables** — Navigate to the app configuration page and map each of the 5 required tables to your existing data
4. **Launch the dashboard** — Open the Streamlit app from the installed application

## Sample Data

If you want to test the app before binding production data, run the `sample_data.sql` script (provided separately) to create a demo dataset with synthetic supplier performance data.

## Architecture

```
Application Package
├── manifest.yml          — App metadata, version, references
├── scripts/
│   └── setup.sql         — Creates schemas, views, Streamlit app
├── streamlit/
│   ├── streamlit_app.py  — Main dashboard application
│   └── environment.yml   — Python dependencies
└── readme.md             — This file
```

## Cortex AI (Optional)

The AI Insights tab uses Snowflake Cortex (llama3.1-70b) for natural language analysis. This feature works automatically in regions where Cortex is available. If Cortex is not available in your region, all other tabs function normally.

## Support

For issues or feature requests, contact the provider through the Marketplace listing page.
