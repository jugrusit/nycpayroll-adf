Project: NYC Payroll Data Lakehouse

Tools Used: Azure Data Factory, ADLS Gen2, Azure SQL DB, Azure Synapse Serverless, Data Flows

Goal: Build a full end‑to‑end data pipeline that ingests NYC payroll data, cleans and transforms it, aggregates by agency and fiscal year, writes results to SQL & ADLS, and exposes them via Synapse external tables.

Key steps:
1. Created an ADLS Gen2 storage account with raw, history, and staging folders.
2. Loaded Employee, Agency, Title, and Payroll (2020/2021) CSV data into ADLS.
3. Built 6 Mapping Data Flows in ADF:
  - 3 master loads
  - 2 payroll loads
  - 1 summary aggregation (with TotalPaid = Regular + OT + Other).
4. Created an orchestrated pipeline:
 - Master loads run in parallel
 - Payroll loads run sequentially
 - Summary flow runs last
5. Wrote summary results to:
  - SQL table (NYC_Payroll_Summary)
  - ADLS staging folder (/dirstaging)
6. Created Synapse external table and validated results.
7. Published ADF to GitHub.

Outcome:
The final pipeline runs successfully end‑to‑end, and the Synapse external query returns correct summary rows for FiscalYear and AgencyName.
