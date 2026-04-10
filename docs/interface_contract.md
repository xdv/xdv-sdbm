# Interface Contract
Project: XDV Secure Domain Boundary Manager  
Specification: XDV-015  
Forge: XdvSdbm

## Versioning
- Interface version: `0.1.0`
- Stability tier: stable-alpha
- Capability API version: `1`
- Attestation API version: `1`
- Audit API version: `1`

## Contract Rules
- Exported procedures must preserve deterministic behavior for identical inputs.
- Return-code semantics are part of the public contract and cannot change without a major version bump.
- Capability token field encoding/decoding semantics are stable.
- Revocation and expiration checks must remain replay-stable.
- Cross-domain authorization must never bypass capability validation.

## Core Security APIs
- `issue_capability_token(...)`
- `sign_capability_token(...)`
- `validate_capability_token(...)`
- `revoke_capability(...)`
- `authorize_boundary_transition(...)`
- `authorize_boundary_transition_with_audit(...)`
- `validate_provider_attestation(...)`

## Deterministic Status Semantics
- `0` = `STATUS_OK`
- `1` = `STATUS_DENIED`
- `2` = `STATUS_INVALID_CAPABILITY`
- `3` = `STATUS_REVOKED`
- `4` = `STATUS_EXPIRED`
- `5` = `STATUS_INVALID_SCOPE`
- `6` = `STATUS_INVALID_SIGNATURE`
- `7` = `STATUS_INVALID_DOMAIN`
- `8` = `STATUS_POLICY_DENIED`
- `9` = `STATUS_ATTESTATION_REQUIRED`
- `10` = `STATUS_ATTESTATION_FAILED`

## Compatibility Surface
The following legacy entry points remain for integration stability:
- `create_capability(...)`
- `verify_capability(...)`
- `check_permission(...)`
- `send_cross_domain_message(...)`

## Migration Notes
Origin: `xdv-kernel/sector/xdv_sdbm`

Kernel and runtime consumers should migrate to this package surface and avoid sector-local direct dependencies.