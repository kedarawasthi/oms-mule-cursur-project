# OMS Mule Portfolio - Resource Index

## 1) Consolidated API Projects (7)

- `customer-sapi` - Customer validation and retrieval (System API)
- `inventory-sapi` - Inventory availability validation (System API)
- `oms-sapi` - Order persistence and lifecycle updates (System API)
- `order-papi` - Process orchestration across system APIs (Process API)
- `order-xapi` - Consumer-facing order API (Experience API)
- `payment-sapi` - Payment authorize/capture/reverse (System API)
- `shipping-sapi` - Shipment create/get/cancel (System API)

## 2) Build and Deployment Artifacts

Each project includes:

- `pom.xml` (Mule Maven plugin + CloudHub profile)
- `mule-artifact.json`
- `src/main/mule/*.xml` flow definitions
- `src/main/resources/config*.yaml|properties` environment configs

## 3) API Specifications (RAML)

- `customer-sapi/src/main/resources/api/customer-sapi.raml`
- `inventory-sapi/src/main/resources/api/inventory-sapi.raml`
- `oms-sapi/src/main/resources/api/oms-sapi.raml`
- `order-papi/src/main/resources/api/order-papi.raml`
- `order-xapi/src/main/resources/api/order-xapi.raml`
- `payment-sapi/src/main/resources/api/payment-sapi.raml`
- `shipping-sapi/src/main/resources/api/shipping-sapi.raml`

## 4) Documentation Set

- `README.md`
- `docs/MASTER_DOCUMENTATION.md`
- `docs/RESOURCE_INDEX.md`
- `docs/HLD_LLD.md`
- `docs/PROJECT_LIFECYCLE_AND_WORKFLOWS.md`
- `docs/PLATFORM_OPERATIONS_RUNBOOK.md`
- `docs/REGRESSION_TEST_RESULTS_DETAILED.md`
- `docs/PROMPT_EXECUTION_LEDGER.md`
- `docs/CURSOR_TDLC_METRICS_FILLED.md`
- `docs/EXECUTIVE_SCORECARD.md`
- `docs/MASTER_DOCUMENTATION.docx`

## 5) Utility Script

- `scripts/generate-doc-pack.py` - builds consolidated Word doc from markdown sources.
