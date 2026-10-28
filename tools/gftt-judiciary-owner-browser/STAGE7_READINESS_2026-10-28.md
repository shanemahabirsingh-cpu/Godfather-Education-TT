# GFTT Stage 7 — browser handoff readiness (offline-only)

Date: 2026-10-28. Status: simulated portal only; NOT deployed; no Judiciary action.

The owner-authenticated eServices login in Cloud Shell was backed up encrypted to private GCS, but the later access/decryption operation was refused by tool safety checks. This branch does not retrieve, decrypt or repurpose that session.

## Verified implementation
- HTTP agent credential minted only after dummy-owner handoff.
- Owner credential revoked immediately at handoff.
- Agent HTTP requests require a unique, in-memory instance/session-binding capability and an authorized agent bearer.
- Browser retirement destroys both credentials and binding.
- Wrong/stale instance and unsupported action requests fail closed.
- Read-only Cloud Run release checker denies any canary before identity, billing, concurrency, runtime and single-instance gates have evidence.
- 56 unit/integration tests passed twice, including from independently extracted ZIP; all 10 release manifest checksums passed.
- ZIP SHA-256: `99017745531b81608de4fe2c7cb785563e1bd9bea22778fd2c5d1a29122c96a8`.

Canonical source release and full checkpoint are stored in owner Library folder `/GFTT_ARE/`:
- `GFTT_Stage7_Instance_Bound_Offline_Release_2026-10-28.zip`
- `GFTT_STAGE7_INSTANCE_BOUND_BROWSER_DEPLOYMENT_GATE_2026-10-28.md`

## Real cloud validation
Prior Commander V2 read-only example.com canary via existing Cloud Run browser returned HTTP 200 (receipt SHA-256 `aa10ac84359cf15103d94e16c46cb1c35ed0b61f53aa60599c32a40e1617b101`). Anonymity, nonallowlisted host and loopback destination tests were denied (receipt SHA-256 `2043ecc4d98b6e38d1f05fefbe898081b5f5a56d597765a69a4dbe793e04b01d`). Owner Cloud Shell readback showed existing service concurrency 1, timeout 40 seconds, CPU 1 vCPU, 1 GiB memory. Those values are NOT sufficient for separate owner/agent long-running browser handoff without additional architecture and verification.

## Release holds
No real court portal integration, credentials, downloads, uploads, signatures, submissions or filing receipts. No Cloud Run deployment or Google IAM change. No extra Google Cloud spend incurred by this Stage 7 offline test. Cloud Run fees for future work have not been ruled out. Preserve existing WhatsMeow Linux VM and production browser inspector unchanged.

Any later live deployment requires separate approved provider/tool authorization, owner IAP/OIDC, authorized agent identity, billing evidence, fail-closed lifecycle control and an independent non-sensitive canary. CV2026-03295 remains unfiled by this workflow.

Official docs:
- https://docs.cloud.google.com/run/docs/triggering/websockets
- https://docs.cloud.google.com/run/docs/securing/identity-aware-proxy-cloud-run
- https://cloud.google.com/run/pricing
