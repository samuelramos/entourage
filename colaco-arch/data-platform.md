# Data Platform

## Overview

CoLaCo's data platform ingests event streams from Confluent Kafka and processes them through three layers — raw, bronze, and gold — stored on Azure storage and processed with Databricks.

## Storage

### Azure Storage

Azure is the primary storage layer for all data platform layers in production.

| Attribute | Value |
|-----------|-------|
| Role | Primary storage for the data platform |
| Owners | _To be confirmed_ |

## Processing

### Databricks

Databricks is the compute and processing layer for the data platform.

| Attribute | Value |
|-----------|-------|
| Role | Data processing across raw, bronze, and gold layers |
| Owners | _To be confirmed_ |

## Layers

### Raw

Landing zone for incoming Kafka events. Data is written to Azure storage with no transformation — preserving the original event payload exactly as received.

| Attribute | Value |
|-----------|-------|
| Table format | _To be confirmed_ |
| Storage | Azure storage |
| Sources | Confluent Kafka — see [confluent-kafka.md](confluent-kafka.md) |
| Transformation | None |
| Owners | _To be confirmed_ |

### Bronze

_To be confirmed_ — expected to hold cleaned or validated data derived from the raw layer.

| Attribute | Value |
|-----------|-------|
| Table format | _To be confirmed_ |
| Storage | Azure storage |
| Sources | Raw layer |
| Transformation | _To be confirmed_ |
| Owners | _To be confirmed_ |

### Gold

_To be confirmed_ — expected to hold aggregated or business-ready data derived from the bronze layer.

| Attribute | Value |
|-----------|-------|
| Table format | _To be confirmed_ |
| Storage | Azure storage |
| Sources | Bronze layer |
| Transformation | _To be confirmed_ |
| Owners | _To be confirmed_ |

## Data flow

```mermaid
flowchart LR
    subgraph Confluent
        kafka[[Kafka Topics]]
    end
    subgraph "Data Platform (Azure + Databricks)"
        raw[Raw\nlanding zone]
        bronze[Bronze\ncleaned]
        gold[Gold\nbusiness-ready]
        raw --> bronze --> gold
    end

    kafka -->|event stream| raw
```

## Development Environment

In local development, Azure storage is replaced by **MinIO** — an S3-compatible object store that mirrors the Azure Blob / ADLS interface so local workloads run without cloud credentials.

**Apache Iceberg** is currently being evaluated as a table format but is not yet used in any environment (local or production).

| Component | Role | Status |
|-----------|------|--------|
| MinIO | Local stand-in for Azure storage | Local dev only |
| Apache Iceberg | Candidate table format | Under evaluation |

## Open questions

- Who owns and operates the data platform?
- What specific Azure storage service is used (ADLS Gen2, Blob Storage)?
- What other Kafka topics (beyond CRM) feed into the raw layer?
- What is the Bronze transformation logic?
- What is the Gold aggregation / serving model?
- What table format is used in production?
- How is schema evolution handled across layers?
- Will Iceberg be adopted — and if so, in which layer first?
