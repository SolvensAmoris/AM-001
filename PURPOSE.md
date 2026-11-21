# STARKCORE AM-001 | Purpose and scope

## Mission

Provide an independent, read-only evidence layer for first-line additive-manufacturing incident triage.

AM-001 is intended for situations where a customer needs to document what was observed on a workstation or in supplied files before escalating an incident to the original equipment manufacturer (OEM), software publisher, or qualified service provider.

## Problem

An interrupted print or failed preparation workflow may involve several independent layers:

1. Source-file identity and revision.
2. Slicer version and workstation environment.
3. Network and time configuration.
4. Customer-provided application logs.
5. Machine, firmware, sensor, and safety subsystems.

A symptom is not a root-cause diagnosis. AM-001 records bounded observations and preserves uncertainty rather than pretending to know proprietary internals.

## Intended evidence bundle

The target output contains:

- Input-file inventory, byte sizes, and SHA-256 digests.
- Generic, explicitly non-OEM log extraction.
- Collection metadata and timestamps.
- Explicit uncertainty and evidence states.
- Human-readable Markdown and machine-readable JSON reports.
- Local integrity authentication with its limitations disclosed.

## Evidence discipline

- `VERIFIED`: the narrowly stated observation was reproduced from supplied bytes or input.
- `PARTIAL`: some evidence was processed, but gaps, truncation, or malformed content remain.
- `NOT_VERIFIED`: the requested observation could not be established.
- `PENDING`: required input was not supplied or was not found.
- `HYPOTHESIS`: an interpretation, never a substitute for an observation.
- `DEMO_SYNTHETIC`: illustrative data only; never customer evidence.

A log line containing an error message proves, at most, that the supplied log contains that line. It does not prove the cause of the incident.

## Out of scope

AM-001 does not:
- Control machinery or issue printer commands.
- Alter firmware, calibration, motion, powder feed, or safety systems.
- Bypass licensing or collect license tokens.
- Certify manufacturability or print readiness.
- Replace OEM support or qualified industrial service personnel.
- Claim OEM certification, endorsement, or warranty coverage.

Safety-critical faults are documented and escalated, never experimentally bypassed.

## Acceptance principle

> NO EVIDENCE → NO ACCEPTANCE

Claims must remain within the scope of the evidence actually collected. Missing or ambiguous evidence stays `PENDING` or `NOT_VERIFIED`.
