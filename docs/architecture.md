# Architecture
XDV Secure Domain Boundary Manager (`xdv-sdbm`) is structured in deterministic layers:

1. Token and boundary core (`src/sdbm.ds`)
- Capability token issuance and deterministic packing
- Token decode, signature verification, TTL, and revocation checks
- Boundary policy enforcement for local/cross-domain transitions

2. Attestation and audit channels (`src/sdbm.ds`)
- Provider attestation checks for Q/Phi pathways
- Attestation digest derivation helper
- Deterministic audit event id generation and packed status/event result

3. Stable interface surface (`src/sdbm_interface.ds`)
- Interface version triplet
- Capability/attestation/audit API surface versions
- Compatibility wrappers for generic version callers

## Enforcement Flow
1. Issue token with operation/scope/policy constraints.
2. Sign token deterministically.
3. Validate token fields, signature, expiry, and revocation status.
4. Enforce boundary operation/scope/policy semantics.
5. Validate attestation when required by policy and target domain.
6. Emit deterministic audit event and return packed audit result.

## Determinism Guarantees
- No nondeterministic clock or RNG dependencies are required by the API.
- Token and audit identifiers are derived from explicit inputs.
- Authorization pass/fail is replay-stable for identical inputs.