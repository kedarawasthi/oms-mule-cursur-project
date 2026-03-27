# OMS Regression Results - Detailed Matrix

Scope: consolidated 7-project OMS portfolio.

## 1) Execution Context

- Status: documentation and repository consolidation completed.
- Runtime regression execution: to be run per deployed environment.
- Source of expected behavior: RAML contracts in each project.

## 2) Baseline Happy Paths (Contract-Level)

| ID | API | Endpoint | Input | Expected | Observed |
|---|---|---|---|---|---|
| HP-01 | customer-sapi | `GET /health` | none | `200` health payload | Pending execution |
| HP-02 | inventory-sapi | `POST /inventory/validate` | valid items list | `200` validation result | Pending execution |
| HP-03 | payment-sapi | `POST /payments/authorize` | valid customer/amount/method | `200` authorized response | Pending execution |
| HP-04 | oms-sapi | `POST /orders` | valid create payload | `201` created order | Pending execution |
| HP-05 | shipping-sapi | `POST /shipments` | valid shipment payload | `201` created shipment | Pending execution |
| HP-06 | order-papi | `POST /orders` | valid end-to-end order payload | `201` orchestrated order response | Pending execution |
| HP-07 | order-xapi | `POST /orders` | valid client payload | `201` consumer-facing order response | Pending execution |

## 3) Error/Negative Paths (Contract-Level)

| ID | API | Endpoint | Input | Expected | Observed |
|---|---|---|---|---|---|
| ER-01 | customer-sapi | `GET /customers/{customerId}` | unknown customerId | `404` not found | Pending execution |
| ER-02 | order-papi | `POST /orders` | invalid payload | `400` validation error | Pending execution |
| ER-03 | order-papi | `POST /orders` | payment failure scenario | `402` payment failure | Pending execution |
| ER-04 | order-papi | `POST /orders` | insufficient inventory | `409` conflict | Pending execution |
| ER-05 | order-xapi | `GET /orders/{orderId}` | unknown orderId | `404` not found | Pending execution |

## 4) Execution Update Rule

For every test cycle, update:

- input payload
- expected status/body
- observed status/body
- pass/fail decision
- run timestamp/environment
