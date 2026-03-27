# order-xapi

Order Experience API – Mule 4 application (API-Led Connectivity, Experience Layer).  
Scaffolded from the **order-xapi** RAML spec (Design Center / APIkit).

## What’s in this repo

- **RAML** in `src/main/resources/api/` – used by APIkit for routing and validation.
- **Flows** in `src/main/mule/` – main listener + APIkit router + one flow per operation (GET/POST/PATCH).
- **Config** – environment-based files: `config-{env}.properties` and `config-secure-{env}.yaml` (selected using `mule.env`).
  - Available environments: `dev`, `qa`, `prod`

## API operations

| Method | Path | Description |
|--------|------|-------------|
| GET | /api/orders | List orders (paginated) |
| GET | /api/orders/{orderId} | Retrieve order by ID |
| POST | /api/orders | Create order |
| PATCH | /api/orders/{orderId}/status | Update order status |
| GET | /api/health | API health (name, version, status) |

Base path is `/api/*` (configurable via HTTP listener).

## Run locally

```bash
mvn clean package "-Dmule.env=dev" "-Dmule.key=cursurdev12345678"
mvn mule:run "-Dmule.env=dev" "-Dmule.key=cursurdev12345678"
```

Default port: **8081**. Try:

- **List orders:** `GET http://localhost:8081/api/orders`
- **Get order:** `GET http://localhost:8081/api/orders/ORD-123`
- **Health:** `GET http://localhost:8081/api/health`
- **API Console:** `http://localhost:8081/console/`

## Deploy to CloudHub

1. Package: `mvn clean package -DskipTests`
2. In Anypoint Platform: Runtime Manager → Deploy application → Upload the JAR from `target/order-xapi-1.0.0-SNAPSHOT-mule-application.jar`
3. Set properties (e.g. `http.port`) in the CloudHub app configuration.

## Scaffolding from Design Center

To regenerate flows from the same spec in Design Center:

1. Publish the **order-xapi** RAML to Exchange / Design Center.
2. In Design Center (or Studio): **Implement** the API and download the generated Mule project.
3. Replace or merge the flow XML and keep your custom logic (e.g. Process/OMS calls) in the operation flows.

This project is structured so flow names and paths match that scaffold (APIkit convention).

## Next steps (Process / System layers)

- **Process API:** Call from these flows (HTTP Request to `${process.api.baseUri}`) when the Process API app is deployed.
- **OMS (system):** `config-{env}.properties` has `oms.useMock`, `oms.baseUri`, `oms.apiPath`. When target OMS is available, set `oms.useMock=false` and `oms.baseUri` (and optionally credentials from `config-secure-{env}.yaml`) and add the outbound HTTP call in the Process/System layer.

---

*Order Experience API | Mule 4.4 | API-Led Connectivity*
