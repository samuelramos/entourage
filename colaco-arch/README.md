# CoLaCo Architecture

Enterprise architecture design for CoLaCo.

## Overview

This repository captures CoLaCo's IT architecture as structured, version-controlled reference material — for onboarding, decisions, and system understanding.

## Goals

- Document existing systems and integrations accurately.
- Identify owners, dependencies, and open questions.
- Provide diagrams for key data flows and component relationships.

## Domains

| Domain | File | Status |
|--------|------|--------|
| CRM | [crm.md](crm.md) | Draft — open questions remain |

## Diagrams

| Diagram | File | Description |
|---------|------|-------------|
| CRM data flow | [diagrams/crm-data-flow.puml](diagrams/crm-data-flow.puml) | PostgreSQL → Debezium → Confluent Kafka |

## Notes

- Owners for several components are still being identified (marked _To be confirmed_).
- PlantUML is used for all diagrams.
