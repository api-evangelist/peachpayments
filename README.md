# Peach Payments (peachpayments)

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

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
