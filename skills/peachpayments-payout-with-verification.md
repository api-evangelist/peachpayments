---
name: Verify a bank account and pay out
description: Authenticate, verify a beneficiary bank account, initiate a Peach Payments payout, and confirm it.
api: openapi/peachpayments-openapi.yml
operations: [createAccessToken, verifyBankAccount, createPayout, getPayout]
---

# Verify a bank account and pay out

Use this for merchant-initiated payouts / disbursements (host `payouts.peachpayments.com`, sandbox `sandbox-payouts.peachpayments.com`).

## Steps
1. **Get a token** — `createAccessToken`: obtain a Bearer `access_token` (same as checkout). Send `Authorization: Bearer {access_token}`.
2. **Verify the beneficiary** — `verifyBankAccount`: POST `accountNumber`, `bankCode`, `accountHolder`, and optional `idNumber` to `/api/accounts/verify` before paying out to reduce failed disbursements.
3. **Create the payout** — `createPayout`: POST `amount`, `currency`, and `beneficiary` (`accountNumber`, `bankCode`, `accountHolder`), plus a `merchantReference`. Returns a `payoutId`.
4. **Confirm** — `getPayout`: GET `/payouts/{payoutId}` and read `status`. A proof-of-payout PDF is generated on success.

## Rules
- Ensure sufficient balance before paying out (retrieve balance / last transaction date first).
- Bulk payouts are uploaded as an XLSX (currency, bankName, payoutMethod, amount, accountNumber, branchCode, reference, accountHolder) and processed asynchronously; track by the returned bulk payout id.
- A `bankVerificationUpdated` webhook notifies of verification results — see `asyncapi/peachpayments-webhooks.yml`.
