---
name: Take a server-to-server payment and refund it
description: Run a Peach Payments server-to-server debit (DB) with an inline auth object, check its status, then refund it (RF).
api: openapi/peachpayments-openapi.yml
operations: [createPayment, getPaymentStatus]
---

# Take a server-to-server payment and refund it

Use this for the server-to-server Payments API (host `api-v2.peachpayments.com`, sandbox `testapi-v2.peachpayments.com`). This API does NOT use the OAuth Bearer flow — it takes an inline `authentication` object.

## Steps
1. **Debit** — `createPayment`: POST `authentication` (`userId` + `password` + `entityId`), `merchantTransactionId` (8-16 alphanumeric), `amount` (decimal string), `currency` (ISO-4217), `paymentBrand` (e.g. `PAYSHAP`, `CAPITECPAY`, `ONEVOUCHER`, `MPESA`, `VISA`), and `paymentType: DB`. Provide method-specific `virtualAccount` details when the brand requires them (PayShap bank + cellphone, Capitec Pay ID, 1Voucher PIN). Returns an `id` and a `result`.
2. **Check status** — `getPaymentStatus`: GET `/payments/{uniqueId}` (the returned `id`). Read `result.code`. Note the documented limit of two transaction-status requests per minute per transaction.
3. **Refund** — call `createPayment` again with `paymentType: RF` referencing the original transaction to reverse/refund.

## Rules
- Success = `result.code` `000.000.*` (or `000.100.110` in the test system). Declines are `800.100.*` (see `errors/peachpayments-decline-codes.yml`) and are usually masked to buyers as a generic decline.
- There is no Idempotency-Key header — use a unique `merchantTransactionId` per attempt and query by it to detect duplicates.
- Keep credentials server-side; never expose the inline `userId`/`password` to a client.
