# OMS Platform Operations Runbook

This runbook mirrors the airline engagement process and applies it to the OMS portfolio.

## 1) Design Center Process (Per API)

Repeat for each API (`customer-sapi`, `inventory-sapi`, `oms-sapi`, `order-papi`, `order-xapi`, `payment-sapi`, `shipping-sapi`):

1. Create/verify Design Center project.
2. Upload RAML sources from `src/main/resources/api`.
3. Validate parser and examples.

## 2) Exchange Publication Process (Per API)

1. Publish RAML as `rest-api` asset with semantic versioning.
2. If version already published (`409`), publish next version.
3. Update Exchange home page documentation.

## 3) API Manager Process (Per API)

1. Create API instance from Exchange asset/version.
2. Configure Autodiscovery ID in application/runtime properties.
3. Apply required policies (Basic Auth / Client ID Enforcement as needed).

## 4) Contract and Client App Process

1. Create SLA tiers (e.g., Bronze/Silver).
2. Create consumer app (or approve app access request).
3. Approve contract binding to API instance + SLA tier.
4. Share generated consumer credentials securely.

## 5) CloudHub 2.0 Deployment Process

1. Build and package Mule app.
2. Deploy using `cloudhub-dev` profile and connected app credentials.
3. Validate deployment status and logs.
4. Execute smoke/regression tests and capture evidence.

## 6) Operational Checklist

- [ ] Design Center synced for all 7 APIs
- [ ] Exchange assets published for all 7 APIs
- [ ] API Manager instances provisioned and mapped
- [ ] Contracts/client apps approved where required
- [ ] CloudHub deployments healthy
- [ ] Regression matrix updated with input/output evidence
