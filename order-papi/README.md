# order-papi

Order Process API – Mule 4 application (API-Led Connectivity, **Process Layer**).  
Orchestrates system APIs (customer, inventory, payment, OMS, shipping) and exposes order process endpoints.

## What's in this repo

- **RAML** in `src/main/resources/api/` – used by APIkit for routing and validation.
- **Flows** in `src/main/mule/` – main listener + APIkit router + orchestration flows + system mock subflows.
- **Config** – environment-based files: `config-{env}.properties` and `config-secure-{env}.yaml` (selected using `mule.env`).
  - Available environments: `dev`, `qa`, `prod`

## Process-layer orchestration

This API sits between the Experience layer (order-xapi) and System layer. It:

- **GET /orders** – Calls OMS to list orders.
- **GET /orders/{orderId}** – Calls OMS to retrieve an order by ID.
- **POST /orders** – Orchestrates: customer validate → inventory validate → payment authorize → OMS create order → shipping create; returns created order (201).
- **PATCH /orders/{orderId}/status** – Calls OMS to update order status.

## Mock strategy (placeholders)

All system APIs use mock subflows when `useMock=true` (default) in `config-{env}.properties`:

- `sys-customer-validate-mock-flow`
- `sys-inventory-validate-mock-flow`
- `sys-payment-authorize-mock-flow`
- `sys-oms-list-orders-mock-flow`, `sys-oms-get-order-mock-flow`, `sys-oms-create-order-mock-flow`, `sys-oms-update-status-mock-flow`
- `sys-shipping-create-mock-flow`

Each subflow has a `TODO` comment where the future outbound HTTP call will be added when target details are available. Set `*.useMock=false` and configure `*.baseUri`, `*.path`, and timeouts to switch to real calls.

## API operations

| Method | Path | Description |
|--------|------|-------------|
| GET | /api/orders | List orders (paginated) |
| GET | /api/orders/{orderId} | Retrieve order by ID |
| POST | /api/orders | Create order (orchestrates system APIs) |
| PATCH | /api/orders/{orderId}/status | Update order status |
| GET | /api/health | API health (name, version, status) |

Base path is `/api/*` (configurable via HTTP listener).

## Build and run

```bash
mvn clean package "-Dmule.env=dev" "-Dmule.key=cursurdev12345678"
mvn mule:run "-Dmule.env=dev" "-Dmule.key=cursurdev12345678"
```

Default port: **8082**. Try:

- **List orders:** `GET http://localhost:8082/api/orders`
- **Get order:** `GET http://localhost:8082/api/orders/ORD-123`
- **Health:** `GET http://localhost:8082/api/health`
- **API Console:** `http://localhost:8082/console/`

## Deploy to CloudHub

1. Package: `mvn clean package -DskipTests`
2. In Anypoint Platform: Runtime Manager → Deploy application → Upload the JAR from `target/order-papi-1.0.0-SNAPSHOT-mule-application.jar`
3. Set properties (e.g. `http.port`, system API `baseUri`) in the CloudHub app configuration.

---

*Order Process API | Mule 4.4 | API-Led Connectivity*
