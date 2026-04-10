# Changelog
## Unreleased - XDV-015 Contract Completion
- Replaced placeholder SDBM logic with deterministic capability token model.
- Implemented token issuance, signing, validation, TTL expiration, and revocation checks.
- Added boundary authorization enforcement for local/cross-domain policy constraints.
- Added attestation validation hook for Q/Phi provider pathways.
- Added deterministic audit event emission and packed audit result helpers.
- Expanded test suite with positive/negative coverage for validation, revocation, attestation, and audit paths.
- Expanded stable interface surface with capability/attestation/audit API version exports.

## 0.1.0 - Sector Split Baseline
- Created standalone project from `xdv-kernel/sector/xdv_sdbm`.
- Copied source module and tests into `src/`.
- Added stable interface file: `src/sdbm_interface.ds`.
- Added initial docs and interface contract.
- Added `LICENSE` copied from `xdv-os/LICENSE`.