# CRM

## Overview

CoLaCo's CRM domain manages customer contact data. The primary store is a cloud-managed PostgreSQL instance on Azure. Changes to that database are streamed in real time via the Debezium CDC connector into Confluent Kafka — see [confluent-kafka.md](confluent-kafka.md).

## Components

### PostgreSQL (Azure)

| Attribute | Value |
|-----------|-------|
| Provider | Azure Database for PostgreSQL |
| Primary use | CRM contact records |
| Owners | CRM Team |

## Data model

TODO

## Open questions

- Who owns / operates the PostgreSQL instance?
- What Kafka topics carry CRM events?
