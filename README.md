# Operational Analytics Lakehouse

## Overview

This project demonstrates an end-to-end operational analytics
pipeline built using Databricks, Python, PySpark, SQL and Delta Lake.

The objective is to transform raw multi-outlet operational data
into trusted analytical datasets that can support dashboards,
automated executive reporting and AI-driven analytics.

## Business Problem

The dataset captures:

- Store opening and closing checklists
- Hygiene and food safety audits
- Equipment audits
- Operational issue reports
- Ticket management and SLA tracking
- Outlet and employee hierarchy

The platform is designed to answer:

- Which outlets are underperforming?
- Why is compliance falling?
- What operational issues recur most frequently?
- Are critical issues being resolved within SLA?
- What should management prioritize?

## Architecture

CSV Sources
→ Bronze
→ Silver
→ Data Quality
→ Gold Dimensions/Facts
→ Business Marts
→ Reporting / Alerts / AI

## Tech Stack

- Databricks
- Python
- PySpark
- SQL
- Delta Lake
- Unity Catalog
- Lakeflow Jobs
- Medallion Architecture

## Data Layers

### Bronze
Raw ingestion with source metadata.

### Silver
Cleaned and typed operational entities.

### Gold
Dimensional models and business-ready marts.

## Ingestion Strategy

| Dataset | Strategy |
|---|---|
| Forms | Full refresh |
| Outlets | Full refresh |
| Users | Full refresh |
| Form submissions | Incremental |
| Form details | Incremental |
| Tickets | Delta MERGE |

## Gold Models

Dimensions:
- dim_outlet
- dim_user
- dim_form
- dim_question

Facts:
- fact_submission
- fact_answer
- fact_ticket

Business marts:
- mart_outlet_compliance
- mart_question_failure
- mart_ticket_sla

## Key Engineering Features

- Medallion architecture
- Idempotent ingestion
- Incremental processing
- Delta MERGE for mutable tickets
- Data-quality assertions
- Referential-integrity validation
- Business-valid NULL handling
- Workflow orchestration

## Reporting Use Cases

The Gold layer can support:

- Metabase dashboards
- Executive reporting
- Automated WhatsApp/email summaries
- AI SQL agents
