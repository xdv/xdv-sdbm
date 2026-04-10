# XDV Secure Domain Boundary Manager
Version: 0.1.0
Status: active-split
Language: Dust Programming Language (DPL)

## Specification Alignment
Primary specification: `XDV-015` in `xdv-spec`.

## Purpose
`xdv-sdbm` is the standalone Secure Domain Boundary Manager that enforces deterministic cross-domain security between K/Q/Phi domains. It owns:
- Capability token issuance, signature validation, expiration, and revocation checks
- Boundary authorization enforcement for local and cross-domain transitions
- Provider attestation validation hooks for Q/Phi-bound operations
- Deterministic audit event emission for allow/deny/revocation outcomes

## Implemented Security Contracts (XDV-015)
1. Capability validation/revocation:
- Token field validation (domain/op/scope/subject)
- Deterministic signature verification
- TTL expiration checks
- Revocation by token-id and by issuance cutoff

2. Boundary authorization:
- Policy-gated local vs cross-domain routing
- Scope/operation compatibility checks
- Operation-specific constraints:
  - `OP_TRANSFORM` requires Phi target
  - `OP_MEASURE` requires Q source
- Permission mask enforcement against requested operation

3. Attestation and audit:
- Q/Phi provider attestation verification hook
- Derived attestation digest helper
- Deterministic audit event id generation
- Packed audit result path (`status + event_id`)

## Public Surface
Forge module: `XdvSdbm`

Primary APIs:
- `issue_capability_token(...)`
- `sign_capability_token(...)`
- `validate_capability_token(...)`
- `revoke_capability(...)`
- `authorize_boundary_transition(...)`
- `authorize_boundary_transition_with_audit(...)`
- `validate_provider_attestation(...)`

Compatibility APIs retained:
- `create_capability(...)`
- `verify_capability(...)`
- `check_permission(...)`
- `send_cross_domain_message(...)`

Version exports:
- `xdv_sdbm_interface_version_major/minor/patch`
- `xdv_sdbm_capability_api_version`
- `xdv_sdbm_attestation_api_version`
- `xdv_sdbm_audit_api_version`

## Repository Layout
- `src/` : SDBM implementation, interfaces, and in-tree tests
- `tests/` : external test scaffolding
- `docs/` : architecture and interface contract docs
- `State.toml` : workspace manifest
- `changelog.md` : release notes
- `LICENSE` : copied from `xdv-os/LICENSE`

## Build
`dust check xdv-sdbm/src`

## Test
`dust test xdv-sdbm/tests`

## Integration Notes
- Kernel integration should consume this project via explicit version pinning.
- Interface version triplet remains `0.1.0` for split dependency compatibility.
- Any return-code semantic changes require a major interface-version increment.