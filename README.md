# Peach Payments (peachpayments)

Peach Payments is a pan-African payment orchestration gateway founded in 2012 in Cape Town, South Africa, operating across South Africa, Kenya, and Mauritius. Its PCI DSS Level 1 platform exposes REST APIs for Checkout (Hosted, Embedded, Embedded Express), server-to-server Payments, Payment Links, Payouts, and Reconciliation, supporting cards plus local methods like PayShap, Capitec Pay, 1Voucher, Mobicred, M-PESA, and MauCAS in ZAR, KES, and MUR.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/peachpayments/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/peachpayments/refs/heads/main/apis.yml)

## Tags

- Payments
- Fintech
- Africa
- Payment Gateway
- Checkout
- Payouts

## Timestamps

- **Created:** 2026-07-17
- **Modified:** 2026-07-17

## APIs

### Peach Payments Authentication API

OAuth 2.0 client-credentials token endpoint (POST /api/oauth/token) that exchanges clientId, clientSecret, and merchantId for a short-lived Bearer access_token used across Checkout, Payouts, and Reconciliation. Sandbox host sandbox-dashboard.peachpayments.com; live host dashboard.peachpayments.com.

- **Human URL:** [https://developer.peachpayments.com/docs/checkout-embedded-authentication](https://developer.peachpayments.com/docs/checkout-embedded-authentication)
- **Base URL:** `https://dashboard.peachpayments.com`

#### Tags

- OAuth
- Authentication
- Token

#### Properties

- [Documentation](https://developer.peachpayments.com/docs/checkout-embedded-authentication)
- [OpenAPI](openapi/peachpayments-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)

### Peach Payments Checkout API

Create Hosted, Embedded, and Embedded Express checkout sessions (POST /v2/checkout), query status, and list available payment methods per currency. Bearer-token authenticated with an entityId and per-request nonce. Sandbox host testsecure.peachpayments.com; live host secure.peachpayments.com.

- **Human URL:** [https://developer.peachpayments.com/docs/checkout-overview](https://developer.peachpayments.com/docs/checkout-overview)
- **Base URL:** `https://secure.peachpayments.com`

#### Tags

- Checkout
- Hosted
- Embedded

#### Properties

- [Documentation](https://developer.peachpayments.com/docs/checkout-overview)
- [API Reference](https://developer.peachpayments.com/reference/payment)
- [OpenAPI](openapi/peachpayments-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/peachpayments.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)

### Peach Payments Payments API

Server-to-server debit (DB) and refund (RF) transactions across cards and local African brands including PayShap, Capitec Pay, 1Voucher, Mobicred, RCS, M-PESA, blink by Emtel, MCB Juice, and MauCAS. Authenticated with an inline userId/password/entityId object. Sandbox host testapi-v2.peachpayments.com; live host api-v2.peachpayments.com.

- **Human URL:** [https://developer.peachpayments.com/reference/payment](https://developer.peachpayments.com/reference/payment)
- **Base URL:** `https://api-v2.peachpayments.com`

#### Tags

- Payments
- Server to Server
- Refunds

#### Properties

- [Documentation](https://developer.peachpayments.com/docs/payments-api-flows)
- [API Reference](https://developer.peachpayments.com/reference/payment)
- [OpenAPI](openapi/peachpayments-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/peachpayments.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)

### Peach Payments Payment Links API

Generate, list, and cancel shareable single-use and bulk payment links for a channel (entityId). Bearer-token authenticated. Sandbox host testapi.peachpayments.com.

- **Human URL:** [https://developer.peachpayments.com/docs/payment-links-overview](https://developer.peachpayments.com/docs/payment-links-overview)
- **Base URL:** `https://links.peachpayments.com`

#### Tags

- Payment Links
- Invoicing

#### Properties

- [Documentation](https://developer.peachpayments.com/docs/payment-links-overview)
- [OpenAPI](openapi/peachpayments-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/peachpayments.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)

### Peach Payments Payouts API

Merchant-initiated payouts, bank account verification, and bulk payout processing with proof-of-payout PDFs. OAuth Bearer authenticated. Sandbox host sandbox-payouts.peachpayments.com; live host payouts.peachpayments.com.

- **Human URL:** [https://developer.peachpayments.com/docs/payouts-api-1](https://developer.peachpayments.com/docs/payouts-api-1)
- **Base URL:** `https://payouts.peachpayments.com`

#### Tags

- Payouts
- Disbursements
- Bank Verification

#### Properties

- [Documentation](https://developer.peachpayments.com/docs/payouts-api-1)
- [OpenAPI](openapi/peachpayments-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/peachpayments.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)

### Peach Payments Reconciliation API

Settlement and transaction reconciliation reporting (GET /api/merchants/{merchantId}/transactions-recon over a date range). OAuth Bearer authenticated. Sandbox host sandbox-reconciliation.ppay.io; live host reconciliation.peachpayments.com.

- **Human URL:** [https://developer.peachpayments.com/docs/bus-ops-recon-api](https://developer.peachpayments.com/docs/bus-ops-recon-api)
- **Base URL:** `https://reconciliation.peachpayments.com`

#### Tags

- Reconciliation
- Settlement
- Reporting

#### Properties

- [Documentation](https://developer.peachpayments.com/docs/bus-ops-recon-api)
- [OpenAPI](openapi/peachpayments-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)

## Common Properties

- [Agentic Access](agentic-access/peachpayments-agentic-access.yml)
- [Trust Center](security/peachpayments-trust-center.yml)
- [Vulnerability Disclosure](security/peachpayments-vulnerability-disclosure.yml)
- [Domain Security](security/peachpayments-domain-security.yml)
- [Authentication](authentication/peachpayments-authentication.yml)
- [GitHub Organization](https://github.com/peach-payments)
- [LinkedIn](https://www.linkedin.com/company/peach-payments)
- [Website](https://www.peachpayments.com/)
- [Documentation](https://developer.peachpayments.com/)
- [Plans](plans/peachpayments-plans-pricing.yml)
- [Rate Limits](rate-limits/peachpayments-rate-limits.yml)
- [Fin Ops](finops/peachpayments-finops.yml)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
