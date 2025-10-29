## Task 2 - Using Azure stack for the pipeline

### Tools and services for the pipeline

#### 1. Ingestion

- Use *Azure Data Factory* to ingest daily files (assume csv/excel) into *Azure Blob storage* or *Data Lake*. This makes the data accessible within Azure, and can be scheduled to run automatically. Alternatively, if data is accessible via APIs, use *Databricks Notebooks* or similar functionality to programmatically access, error check and ingest data daily.
- Main considerations: handles missed schedules, messy inputs

#### 2. Transformation and cleaning

- Use *Azure Databricks* (works well with Spark, for larger data) or simpler *Data Factory mapping flows* to apply the cleaning and transformation steps.
- Main considerations: performs reliably, logs steps for audit

#### 3. Storage

- Store historic and daily updating cleaned data, either in *Azure SQL*, or as parquet files on *Data lake* or *Blob* storage. This provides easier access for analysis tasks, without dealing with the cleaning and ingestion processes.
- Main considerations: inexpensive long-term storage, easy access for analysis

#### 4. Analysis (scheduled) & Visualisation

- Schedule the run of a *Databricks notebook*, or *Azure Functions* to compute the stats used within the report.
- Use *PowerBI* to visualise the stats, allow interactive exploration of the data and provide a dashboard for consumption.
- Main considerations: analytics interface easy to use for Data Scientists and analysts, visualisation layer intuitive to use for non-technical audience

#### 5. Monitoring

- Pipeline health can also be tracked using built-in tools.
- Main considerations: clear metrics that are easy to understand

#### 1. Security & Governance

- Azure provides clear rule-based permissions and encryption allowing clear data lineage and compliance with the Bank's Privacy and FoI policies.
- Main considerations: well-defined policies, easy role assignment

### Use of Generative AI

We could leverage built-in tools on Azure to accelerate the development of an App or interface that provides supervisors with chatbot-like functionality.
> User: "which firms had the largest GWP swing in 2020?"
> Bot: "Firm x had the biggest drop. They also showed unstable behaviour in 2015."

Key step here is to summarise key metrics from structured tables, into a format that can be retrieved using natural language via embeddings.

Overall steps to implement:
i. Create a set of prompts, such as "which firms had the `{size_field}` `{direction_field}` `{metric_field}` in `{year_field}`" using mutable parameters.
ii. Generate summaries for every firm using the yearly data as an input, using a standard prompt: "generate a summary for firm `{x}` using data provided `{data}`"
iii. Link the summaries and prompt-set together in a database.
iv. Create an app (can be a *Static Web App*) that allows this querying.
v. Use *Cognitive Search* or *Embeddings* to retrieve the best responses.
