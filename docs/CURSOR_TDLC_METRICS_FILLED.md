# Cursor TDLC Metrics (OMS Filled - aligned to airline format)

This sheet fills the TDLC capability/task matrices for **Cursor AI** for the OMS portfolio.

Important context:
- OMS used dummy data for major flow validation.
- Testing was mostly local for this cycle.
- Full runtime deployment/governance closure for all OMS apps was not completed in this phase.

As requested, scores below are aligned to the airline-style template with **one-point-lower scoring** across metrics.

## A) Comparative Analysis - TDLC Capabilities (Cursor AI Filled)

Scale used: `0-4` (higher is stronger).

| Capability | Parameter | Cursor AI Score (0-4) | Evidence in OMS context |
|---|---|---:|---|
| Requirement Generation | Epic Generation | 2 | Converted broad OMS ask into phased repository/documentation delivery stream |
| Requirement Generation | Features Generation | 3 | Delivered 7-project consolidation, docs, runbook, metrics and scorecard assets |
| Requirement Generation | User Stories Generation | 2 | Derived validation scenarios and backlog items from iterative prompts |
| Design Document Generation | Functional Design Generation | 3 | Produced service-level OMS documentation and workflow coverage |
| Design Document Generation | Technical Design Generation | 3 | Produced HLD/LLD and architecture-level mapping for OMS layers |
| Build | API Level | 3 | Consolidated and reviewed API-level RAML/flow structures across projects |
| Build | Code Generation | 3 | Generated supporting scripts/docs and portfolio structuring artifacts |
| Build | Code Review | 2 | Identified major hardening items; deeper runtime-cycle review still pending |
| Test Case Generation | Functional (Manual) Test Cases | 3 | Regression matrix and manual validation paths documented |
| Test Case Generation | Test Automation Scripts (MUnits) | 1 | MUnit posture documented but not fully stabilized in this OMS phase |
| Test Case Generation | Test Data Generation Based on Tests | 2 | Dummy data and representative payloads used for OMS test framing |
| Deployment | Able to validate/deploy components | 3 | Deployment patterns prepared; full OMS runtime rollout not completed |
| Platform | Exchange Integration | 3 | Process runbook documented; OMS-wide execution remains pending |
| Platform | API Manager and Runtime Operations | 2 | Governance operations documented but not fully executed for all OMS apps |

## B) Comparative Analysis - TDLC Capabilities wrt Current Approach (Cursor AI Filled)

Scale used: `0-4`.

| Capability | Parameter | Cursor AI Score (0-4) | Effort Reduction with current approach |
|---|---|---:|---:|
| Requirement Generation | Epic Generation | 2 | 25% |
| Requirement Generation | Features Generation | 3 | 35% |
| Requirement Generation | User Stories Generation | 2 | 25% |
| Design Document Generation | Functional Design Generation | 3 | 45% |
| Design Document Generation | Technical Design Generation | 3 | 50% |
| Build | API Level | 3 | 40% |
| Build | Code Generation | 3 | 45% |
| Build | Code Review | 2 | 20% |
| Test Case Generation | Functional (Manual) Test Cases | 3 | 35% |
| Test Case Generation | Test Automation Scripts (MUnits) | 1 | 15% |
| Test Case Generation | Test Data Generation Based on Test Cases | 2 | 25% |
| Deployment | Able to validate/deploy components | 3 | 35% |
| Platform | Exchange Integration | 3 | 40% |
| Platform | API Manager and Runtime Operations | 2 | 20% |

## C) TDLC Evaluation - Task Level Metrics (1/2) - Cursor AI

Scale used: `1-10`.

### Requirement

| Assessment Metric | Cursor Score | Effort Reduction |
|---|---:|---:|
| Requirement (Epic/Feature/User Story) analysis | 7 | 30% |
| Architecture Diagram | 7 | 40% |
| Functional Design Document / Technical Design | 8 | 50% |
| Fragment Creation | 7 | 35% |
| Request Response Data Type Creation | 7 | 35% |
| RAML Creation/Review | 8 | 45% |

### Build

| Assessment Metric | Cursor Score | Effort Reduction |
|---|---:|---:|
| API level: API Template create/update | 8 | 40% |
| API level: API Flow Creation | 8 | 45% |
| API level: API Development | 7 | 40% |
| API level: Error Handling Creation | 7 | 35% |
| Code Development: DataWeave Creation Complexity | 7 | 40% |
| Code Development: Batch Processing | 7 | 35% |
| Code Development: Scatter Gather | 6 | 25% |
| Code Development: Real time processing | 7 | 30% |
| Code Development: Salesforce Connector | 4 | 10% |
| Code Development: DB Connector (Mongo) | 5 | 10% |
| Code Review | 6 | 20% |
| Security: Data privacy handling | 7 | 30% |
| Security: Code exposure risk | 6 | 15% |

## D) TDLC Evaluation - Task Level Metrics (2/2) - Cursor AI

### Governance

| Assessment Metric | Cursor Score | Effort Reduction |
|---|---:|---:|
| Policy enforcement | 5 | 15% |
| Code validation | 7 | 30% |

### Testing

| Assessment Metric | Cursor Score | Effort Reduction |
|---|---:|---:|
| Mock service creation | 6 | 25% |
| MUnit test suite creation | 5 | 15% |
| Postman Collection | 8 | 45% |

### Deployment

| Assessment Metric | Cursor Score | Effort Reduction |
|---|---:|---:|
| Application Deployment | 8 | 40% |
| Git Integration | 7 | 35% |
| External Logging Enablement | 7 | 30% |

### Platform

| Assessment Metric | Cursor Score | Effort Reduction |
|---|---:|---:|
| Exchange Operations | 8 | 45% |
| API Manager Operations | 5 | 15% |
| Runtime Manager Operations | 7 | 30% |
| Manage Schedulers | 8 | 40% |

## E) Notes

- Scores are intentionally calibrated one point below airline metrics, per requested comparison model.
- OMS scores reflect current-cycle boundaries (dummy data, mostly local testing, partial platform execution).
- Recommended next phase: runtime deployment evidence capture + APIM/Exchange closure for all 7 APIs.
