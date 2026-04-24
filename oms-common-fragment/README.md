# OMS Common Fragment Library

Reusable RAML 1.0 fragment library for the Order Management System (OMS) integration suite. This fragment eliminates duplication by centralising types, traits, examples, and security schemes shared across all seven OMS APIs.

## What's Included

| Component | File | Description |
|-----------|------|-------------|
| **Entry Point** | `oms-common-library.raml` | Main library — import this in your API spec |
| **Common Types** | `types/common-types.raml` | `Error`, `HealthResponse`, `Address` |
| **Order Types** | `types/order-canonical-types.raml` | `Order`, `OrderList`, `CreateOrderRequest`, `OrderItemInput`, `OrderItem`, `UpdateOrderStatusRequest` |
| **Common Traits** | `traits/common-traits.raml` | `paginated`, `responses-400`, `responses-401`, `responses-404`, `responses-500`, `responses-errors` |
| **Security** | `security-schemes/basic-auth.raml` | Basic Authentication scheme with `describedBy` |
| **Examples** | `examples/*.json` | Standardised error payloads (400, 401, 402, 404, 409, 500) and health response |

## Usage

### Local (relative path)

If using this fragment from within the same repository:

```raml
#%RAML 1.0
title: My OMS API
uses:
  common: ../../oms-common-fragment/oms-common-library.raml
```

### Exchange (after publishing)

After publishing to Anypoint Exchange, each API spec imports via `exchange_modules`:

```raml
#%RAML 1.0
title: My OMS API
uses:
  common: exchange_modules/com.example.oms/oms-common-fragment/1.0.0/oms-common-library.raml
```

### Applying Types and Traits

```raml
# Use common Error type
responses:
  500:
    body:
      application/json:
        type: common.commonTypes.Error

# Use health response type
/health:
  get:
    responses:
      200:
        body:
          application/json:
            type: common.commonTypes.HealthResponse

# Apply pagination trait
/orders:
  get:
    is: [ common.commonTraits.paginated, common.commonTraits.responses-401, common.commonTraits.responses-500 ]

# Use order types
  post:
    body:
      application/json:
        type: common.orderTypes.CreateOrderRequest
    responses:
      201:
        body:
          application/json:
            type: common.orderTypes.Order

# Use security scheme
securitySchemes:
  basic: common.securitySchemes.basic
securedBy: [ basic ]
```

## Fragment Structure

```
oms-common-fragment/
├── oms-common-library.raml         # Main entry point
├── exchange.json                   # Exchange metadata
├── README.md
├── types/
│   ├── common-types.raml           # Error, HealthResponse, Address
│   └── order-canonical-types.raml  # Order domain types
├── traits/
│   └── common-traits.raml          # paginated, responses-4xx/5xx
├── security-schemes/
│   └── basic-auth.raml             # Basic Authentication
└── examples/
    ├── error-400.json
    ├── error-401.json
    ├── error-402.json
    ├── error-404.json
    ├── error-409.json
    ├── error-500.json
    └── health-response.json
```

## APIs That Should Consume This Fragment

| API | Layer | What It Reuses |
|-----|-------|----------------|
| `order-xapi` | Experience | Error, HealthResponse, Order types, traits, security |
| `order-papi` | Process | Error, HealthResponse, Order types, Address, traits, security |
| `oms-sapi` | System | Error, HealthResponse, traits, security |
| `customer-sapi` | System | Error, HealthResponse, traits, security |
| `inventory-sapi` | System | Error, HealthResponse, traits, security |
| `payment-sapi` | System | Error, HealthResponse, traits, security |
| `shipping-sapi` | System | Error, HealthResponse, Address, traits, security |

## Publishing to Exchange

```bash
# From the oms-common-fragment directory
anypoint-cli exchange asset upload \
  --organization "com.example.oms" \
  --name "oms-common-fragment" \
  --version "1.0.0" \
  --classifier "raml-fragment" \
  --mainFile "oms-common-library.raml"
```

Or via Design Center: import this folder as a RAML Fragment project and publish.
