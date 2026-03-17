# CI Federation Execution Plan (Asana-Ready)

## Objective

Create a federated CI operating model where Azure remains the only Kubernetes deploy authority,
while GitHub/GitLab/Bitbucket provide non-deployment value (security, quality, AI validation, governance).

## Owner

- Primary assignee: <chad@pixelatedempathy.com>

## Target Goal Dates

- Goal 1: Ownership matrix finalized and approved - 2026-03-20
- Goal 2: Duplicate jobs removed and single-owner CI lanes active - 2026-03-31
- Goal 3: Cross-platform release readiness gate wired into Azure deploy - 2026-04-10
- Goal 4: Dashboard + operating review cadence active - 2026-04-17

## Scope

- In scope:
  - Pipeline ownership model
  - Trigger strategy by path/branch/event
  - Security and quality gate consolidation
  - AI validation lane specialization
  - Azure pre-deploy release-readiness gate
- Out of scope:
  - Migration away from Azure deploy
  - Full replacement of existing CI providers

## Platform Responsibilities

- Azure DevOps: image build provenance, AKS deployment, infra apply, environment approvals
- GitHub Actions: CodeQL, SARIF security reporting, scheduled security checks
- GitLab CI: MR quality gate (lint/type/test), compliance evidence artifacts
- Bitbucket Pipelines: AI/data pipeline validation and governance checks

## Operating Rules

1. One deploy authority: Azure only.
2. One owner per CI capability (no duplicate scans/tests unless justified).
3. Build once/deploy once lineage for release artifacts.
4. Azure deploy stage requires upstream readiness checks to be green.
5. All failed scheduled checks auto-create or update a tracked work item.

## Success Metrics

- Duplicate CI job count reduced by >= 60%
- Median PR feedback time <= 12 minutes for fast checks
- Security SLA: critical findings triaged in < 24h
- Deployment rollback rate reduced month-over-month
- AI validation failure detection with issue auto-tracking enabled

## Risks and Mitigation

- Risk: Missing visibility when jobs are split across systems
  - Mitigation: Weekly rollup dashboard and single readiness status in Azure
- Risk: Team confusion on "where to look"
  - Mitigation: Ownership matrix + runbook + escalation owner per lane
- Risk: Drift between scripts across platforms
  - Mitigation: Shared command contract from package scripts and uv/pnpm standards

## Implementation Cadence

- Week 1: Inventory + ownership
- Week 2: Consolidate + de-duplicate
- Week 3: Gate integration + dry runs
- Week 4: Operationalize metrics and review cadence

## Delivery Artifacts

- Asana import CSV: docs/plans/2026-03-17-ci-federation-asana-tasks.csv
- This planning document: docs/plans/2026-03-17-ci-federation-asana-plan.md
