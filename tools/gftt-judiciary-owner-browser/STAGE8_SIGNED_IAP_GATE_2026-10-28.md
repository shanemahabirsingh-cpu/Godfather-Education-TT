# GFTT Stage 8 — signed IAP identity release gate (OFFLINE ONLY)

Verified: 2026-10-28. This is a checkpoint for the controlled Chromium owner→agent handoff fixture; no production deployment and no court portal actions.

## Actual implementation
- Cryptographically verifies ES256 JWT assertions for the signed `X-Goog-IAP-JWT-Assertion` header using trusted public keys provided by the fixture.
- Enforces exact IAP issuer, audience, key ID, expiration and distinct signed owner/agent subjects.
- Checks every protected owner/agent HTTP request before dispatching browser actions.
- Maintains previous one-way handoff, bearer, CSRF/Origin, serial browser actions, expiry, per-instance binding and no-upload fixture restrictions.
- Fail-closed Stage 8 canary release gate requires provider-evidenced real IAP setup, real owner/agent principals, invoker authorization, no-extra-cost checks and Cloud Run runtime guarantees.

## Independent verification
- 88 automated tests passed in source directory and again after fresh ZIP extraction using real local Chromium and **only dummy test keys**.
- 13 SHA-256 file manifest checks passed.
- ZIP SHA-256: `b1eead7b2d5c0f21f3a752edc1e29f23f572e9e405ffe50739c323ac98a688cd`.
- Current production Cloud Run settings (concurrency 1, timeout 40 seconds) and missing IAP/budget evidence yield **15 release blockers** and no ready-for-canary claim.

## Authoritative owner Library artifacts

The source code and complete tests (not exposed as a public browser service):
- `/GFTT_ARE/GFTT_Stage8_IAP_Signed_Identity_Offline_2026-10-28.zip`
- `/GFTT_ARE/GFTT_STAGE8_IAP_SIGNED_IDENTITY_GATE_2026-10-28.md`

## Holds
- No live Cloud Run IAP configuration was changed or confirmed.
- The fixture still binds to localhost and is **not** directly deployable to Cloud Run.
- No real Judiciary session was downloaded, decrypted, imported, or remotely controlled. The earlier tool refusal is respected.
- No GFTT Linux WhatsMeow, Cloud Run inspector or billing configuration was changed.
- Filing **CV2026-03295 remains unfiled by this workflow**.

Cloud documentation:
https://docs.cloud.google.com/iap/docs/signed-headers-howto
https://docs.cloud.google.com/run/docs/securing/identity-aware-proxy-cloud-run
