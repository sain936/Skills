# Advanced Projects

Require written scope and appropriate safety, privacy, and resource review.
Prefer non-production environments and synthetic or explicitly authorized data.

## Analytics warehouse

- Design a dimensional model and source-to-target mapping.
- Implement tested transformations and incremental processing.
- Validate reconciliations, lineage, access boundaries, and schema evolution.

## Production data pipeline

- Design ingestion, orchestration, quality checks, idempotency, retries,
  observability, and recovery.
- Measure performance and cost only with actual, documented runs.

## Predictive analytics

- Define the decision and baseline before selecting an ML model.
- Prevent leakage; use suitable validation, calibration, and interpretation.
- Document limitations, monitoring, and human oversight.

## Model deployment and MLOps

- Package and validate a model in a safe test environment.
- Specify deployment, versioning, monitoring, rollback, and data-drift checks.
- Do not deploy to production or incur cloud costs without explicit approval.

## RAG application

- Define data permissions and threat model.
- Evaluate ingestion, retrieval, grounding, answer quality, and privacy.
- Test prompt injection and access-control boundaries.

## Distributed processing or lakehouse

- Justify architecture against requirements and workload.
- Test data quality, fault tolerance, and recovery.
- Measure scalability, performance, and cost rather than asserting them.
