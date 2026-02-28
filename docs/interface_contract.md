# Interface Contract
Project: XDV Secure Domain Boundary Manager
Specification: XDV-015
Forge: XdvSdbm
## Versioning
- Interface version: 0.1.0
- Stability tier: stable-alpha
## Contract Rules
- Exported procedures must preserve deterministic behavior for identical inputs.
- Return code semantics are part of the public contract and cannot change without a major version bump.
- Domain tags, capability masks, and status constants are externally visible contract data.
- New constants/procedures must be additive unless major-version upgrade is declared.
## Current Public Files
- src/sdbm.ds
- src/sdbm_interface.ds
## Migration Notes
This project was split from xdv-kernel/sector/xdv_sdbm.
Kernel integration paths should progressively switch from sector-local imports to versioned dependency usage.
