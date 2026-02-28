# XDV Secure Domain Boundary Manager
Version: 0.1.0
Status: active-split
Language: Dust Programming Language (DPL)
## Specification Alignment
Primary specification: XDV-015 in xdv-spec.
## Purpose
Standalone Secure Domain Boundary Manager project for capability validation, policy enforcement, and security boundary controls.
This repository was split from xdv-kernel/sector/xdv_sdbm into a standalone project so interfaces can evolve independently under stable versioning.
## Split Provenance
- Source sector: xdv-kernel/sector/xdv_sdbm
- Imported Dust modules: src/sdbm.ds and src/sdbm_tests.ds
- Import model: source-copy split (non-destructive to existing kernel sector)
## Stable Interface Contract
This project defines a stable external interface boundary in:
- src/sdbm_interface.ds
- docs/interface_contract.md
Compatibility model:
- Semantic interface versioning (major/minor/patch)
- Additive changes are minor releases
- Breaking signature/semantic changes are major releases
- Deprecated APIs remain one minor cycle before removal
## Repository Layout
- src/ : implementation and interface surfaces
- tests/ : standalone tests and integration placeholders
- docs/ : architecture and interface docs
- State.toml : workspace manifest
- changelog.md : release notes
- LICENSE : copied from xdv-os/LICENSE
## Public Surface
- Forge module: XdvSdbm
- Primary implementation: src/sdbm.ds
- Stable interface profile: src/sdbm_interface.ds
## Dependencies
Planned dependencies:
- xdv-dal, xdv-kernel, xdv-runtime, xdv-lib
- Dust toolchain and runtime packages required by integration profile
## Build
dust check xdv-sdbm/src
## Test
dust test xdv-sdbm/tests
## Integration Notes
- Kernel integration should consume this project via explicit version pinning.
- xdv-os integration should use release tags from this repo, not kernel-internal paths.
- API changes must update docs/interface_contract.md and changelog.md in the same change set.
