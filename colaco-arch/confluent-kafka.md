# Confluent Kafka

## Overview

CoLaCo uses a managed Confluent Kafka cluster as the central event streaming backbone. It receives CDC events from Debezium and feeds downstream systems, including the data platform.

## Components

### Confluent Cluster

| Attribute | Value |
|-----------|-------|
| Platform | Confluent (managed Kafka) |
| Topics | _To be confirmed_ |
| Producers | Debezium — see [debezium.md](debezium.md) |
| Consumers | Data platform (raw area) — see [data-platform.md](data-platform.md) |
| Owners | _To be confirmed_ |

## Data flow

```mermaid
flowchart LR
    debezium[Debezium\nsee debezium.md]
    subgraph Confluent
        kafka[[Kafka Topics]]
    end
    dp[Data Platform\nsee data-platform.md]

    debezium -->|change events| kafka
    kafka -->|event stream| dp
```

## Open questions

- What are the topic names and naming conventions?
- Is a Schema Registry in use? If so, what serialization format (Avro, Protobuf, JSON Schema)?
- What retention policies are configured?
- Are there consumers beyond the data platform?
- Who owns and operates the Confluent cluster?
