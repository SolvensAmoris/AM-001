# STARKCORE AM-001
**Additive Manufacturing Integrity & Diagnostics**  
**Version target:** 0.3.0  
**Repository status:** Project documentation published; implementation pending validation  
**Maintainer:** StarkCore Labs · Mexico

> **NO EVIDENCE → NO ACCEPTANCE**

AM-001 is a proposed, read-only evidence-collection layer for first-line additive-manufacturing incident triage. It is designed to help an operator preserve verifiable facts about input files and customer-supplied logs before an incident is escalated to an equipment manufacturer, software publisher, or qualified service provider.

**AM-001 does not repair, control, certify, or operate industrial printers.**

## Why this project exists

Industrial additive-manufacturing incidents can cross several layers: source-file identity, slicer configuration, workstation environment, network/time settings, application logs, firmware, sensors, and safety systems. A symptom alone does not establish a root cause.

AM-001 aims to produce a compact, inspectable evidence bundle that distinguishes:
- What was directly observed.
- What was mechanically verified.
- What remains an interpretation or hypothesis.
- What is missing and therefore pending.
- What must be escalated to the OEM or qualified service personnel.

Core separation:

`OBSERVATION ≠ INTERPRETATION ≠ ROOT CAUSE`

## Intended capabilities

The v0.3.0 scope is:
- SHA-256 inventory of supplied files.
- Conservative generic extraction from customer-provided text logs.
- Explicit evidence states: `VERIFIED`, `PARTIAL`, `NOT_VERIFIED`, `PENDING`, and `DEMO_SYNTHETIC`.
- Machine-readable JSON and human-readable Markdown reports.
- Local integrity authentication with its limitations disclosed.

The parser is **not** an Eiger, Magics, EOSPRINT, or other OEM-specific parser. It records text structure; it does not infer proprietary semantics or root cause.

## Safety and scope boundaries

AM-001 will not:
- Control printers or issue machine commands.
- Modify firmware, calibration, motion, powder feed, or safety interlocks.
- Collect, recover, or bypass license tokens.
- Diagnose or override laser, interlock, encoder, powder-feed, or other safety-critical systems.
- Claim that an STL/3MF is printable, dimensionally correct, safe, or production-ready.
- Claim OEM certification, endorsement, or warranty coverage.

Safety-critical and machine-level faults must be documented and escalated to the manufacturer or qualified service personnel.

## Cryptographic boundary

The proposed v0.3.0 design uses HMAC-SHA256, a **symmetric message-authentication code**, not an asymmetric digital signature. Verification requires the same secret used for signing. It does not provide public verification or non-repudiation.

A local digest or HMAC does not establish independent trust if an attacker can replace the report, sidecar, and secret together. The next cryptographic milestone is Ed25519 with independently retained public-key material and an external evidence receipt.

Never commit private keys, customer logs, license material, or confidential production files.

## Current publication status

This repository is being initialized with the project purpose, safety boundary, and security policy first. The implementation and automated acceptance suite are **not yet declared release-ready**. They will be published only after the complete test suite passes and verification behavior is reviewed.

No industrial deployment or paid diagnostic engagement should rely on this repository as a validated release until that gate is closed.

## Acceptance principle

`DETECT ≠ VERIFY ≠ AUTHORIZE ≠ EXECUTE`

A hash proves byte identity relative to a known digest. It does not prove authorship, correctness, safety, printability, or OEM approval.

## Contributing and reporting

Before contributing code, read [PURPOSE.md](PURPOSE.md) and [SECURITY.md](SECURITY.md). Do not open public issues containing customer data, credentials, license tokens, proprietary geometry, or confidential production information. Use a private security advisory where available.

## License

Apache License 2.0. See [LICENSE](LICENSE).
