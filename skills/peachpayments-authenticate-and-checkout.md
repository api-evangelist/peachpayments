---
name: Authenticate and create a checkout
description: Obtain an OAuth token, list payment methods for a currency, create a Peach Payments checkout session, and confirm the result.
api: openapi/peachpayments-openapi.yml
operations: [createAccessToken, getPaymentMethodsForCurrency, createCheckout, getCheckoutStatus]
---

# Authenticate and create a checkout

Use this to start a Hosted or Embedded checkout with Peach Payments.

## Prerequisites
- A merchant `clientId`, `clientSecret`, and `merchantId` (from the Dashboard).
- The channel `entityId` for the currency you are charging (ZAR, KES, or MUR).
- Sandbox hosts for testing (see `sandbox/peachpayments-sandbox.yml`); live hosts for production.

## Steps
1. **Get a token** — `createAccessToken`: POST `clientId` + `clientSecret` + `merchantId` to `/api/oauth/token` (sandbox `sandbox-dashboard.peachpayments.com`). Keep the short-lived `access_token`; send it as `Authorization: Bearer {access_token}`.
2. **(Optional) List methods** — `getPaymentMethodsForCurrency`: confirm which brands (cards, PayShap, Capitec Pay, 1Voucher, M-PESA, etc.) are enabled for the `entityId` + `currency`.
3. **Create the checkout** — `createCheckout`: POST `authentication.entityId`, `amount` (decimal string, e.g. "100.00"), `currency`, a unique `nonce`, and `shopperResultUrl`. Optionally set `merchantTransactionId` (8-16 alphanumeric) as your correlation key. Use the checkout host (sandbox `testsecure.peachpayments.com`). Returns a `checkoutId`.
4. **Confirm** — `getCheckoutStatus`: poll with the `checkoutId` and read `result.code` / `result.description`. `000.000.*`/`000.100.110` (test) = success; `800.100.*` = decline (see `errors/peachpayments-decline-codes.yml`).

## Rules
- Each checkout request needs a fresh unique `nonce`; there is no Idempotency-Key header — reconcile with `merchantTransactionId`.
- Webhooks (`created`/`pending`/`successful`/`uncertain`/`cancelled`) are the authoritative signal; order them by payload `timestamp`. See `asyncapi/peachpayments-webhooks.yml`.
- Never log full card data — card processing runs on the PCI DSS Level 1 platform.
