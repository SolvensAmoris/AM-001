# Security policy

## Data classification

Do not commit or submit customer logs containing passwords, API keys, license tokens, personal information, proprietary geometry, machine credentials, or confidential production data. Sanitize logs before sharing them for support.

## Key handling

The proposed v0.3.0 HMAC secret is a local symmetric key. Keep it outside version control, restrict filesystem permissions, and do not email, upload, or share it.

If the key is lost, prior HMAC tags cannot be verified. If it is exposed, treat prior authentication as compromised and rotate the key for future reports.

## Cryptographic scope

HMAC-SHA256 is not Ed25519 and is not a publicly verifiable digital signature. It authenticates data only for parties that possess the same secret. It does not provide public verification or non-repudiation.

A report, JSON sidecar, and key stored together on one compromised workstation do not constitute independent custody. Independent retention and public-key verification are future requirements, not current guarantees.

## Safety boundary

Do not use AM-001 to manipulate machine controls, firmware, laser systems, interlocks, motion systems, powder-feed systems, or other safety-critical functions. Escalate such faults to the OEM or qualified service personnel.

## Reporting vulnerabilities

Use a private GitHub Security Advisory where available. Do not publish exploit details, customer logs, credentials, or production data in public issues.
