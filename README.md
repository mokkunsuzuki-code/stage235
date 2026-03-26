# Stage231: Multi-Signer (Distributed Trust)

## Overview

Stage231 introduces **multi-party signatures** to the QSP verification pipeline.

Instead of relying on a single signer, the same payload is signed by multiple independent parties:

- Owner (project maintainer)
- Third-party (external auditor/operator)
- Researcher (independent reviewer)

This enables **distributed trust** and stronger auditability.

---

## Concept

Traditional model:


Evidence
→ Signature (single)
→ Trust depends on one entity


Stage231:


Evidence
→ Multiple Signatures
→ Independent verification
→ Distributed trust


---

## What is Signed

A canonical JSON payload:

- log_id
- tree_size
- merkle_root
- generated_at_utc

---

## Quick Start

```bash
git clone https://github.com/mokkunsuzuki-code/stage231.git
cd stage231

./tools/run_stage231_multi_signer.sh
pytest -q
Output
out/multi_signer/
├── payload.json
└── signed_bundle.json
Example Result
[OK] valid signature: owner
[OK] valid signature: third_party
[OK] valid signature: researcher
[OK] valid_count: 3
[OK] multi-signer verification passed
Verification Logic

A verifier can:

Check payload hash
Verify each signature independently
Identify signer roles
Count valid signatures
Policy Flexibility

Possible verification policies:

Require ≥1 signature
Require ≥2 signatures
Require all signatures
Security Value

This stage does NOT introduce new cryptography.

It improves:

Trust distribution
Audit transparency
Reviewer independence
Evidence credibility
Architecture Evolution
Stage230:
Single proof authenticity

Stage231:
Multi-party attested authenticity
Limitations
Uses Ed25519 (standard signatures)
Not a threshold signature scheme yet
Signers are simulated (local keys)
Future Work
Threshold signatures (Stage232)
Real external signers
Policy enforcement (M-of-N)
License

MIT License

Copyright (c) 2025 Motohiro Suzuki