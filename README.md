# QSP Stage228 — Fail Evidence Persistence

This stage introduces **fail evidence persistence** to the QSP verification pipeline.

Instead of only detecting failures, Stage228 ensures that failures are:

- recorded
- hashed (SHA256)
- stored as tamper-evident evidence
- verifiable later

---

## 🔍 Concept

Flow:

Attack  
↓  
Fail Detection  
↓  
Log Persistence  
↓  
SHA256 Hashing  
↓  
Evidence Fixation  

---

## 🎯 Goal

Stage227:
- Detect failure

Stage228:
- Preserve failure as **tamper-evident forensic evidence**

This enables:

- forensic analysis
- auditability
- reproducible verification
- claim → attack → evidence traceability

---

## 🚀 Quick Start

Run the full pipeline:

```bash
./tools/run_stage228_fail_evidence.sh
✅ Verification

Verify that stored evidence matches original logs:

python3 tools/verify_fail_evidence.py --index out/fail_evidence/index.json

If logs are modified, verification will fail.

📂 Output

Generated artifacts:

out/
├── failures/
│   └── downgrade_fail.log
├── fail_evidence/
│   ├── downgrade_fail.evidence.json
│   └── index.json
🧪 Tests

Run all tests:

pytest -q
🔐 Security Meaning

This stage transforms failure into:

👉 tamper-evident evidence

Properties:

Integrity (SHA256)
Reproducibility
Detectable modification
External verifiability
📈 Evolution

Stage226 — Executable system
Stage227 — Fail detection
Stage228 — Fail evidence persistence ← You are here

⚠️ Scope

This is not a full protocol security proof.

It is a reproducible framework for:

detecting failures
preserving them as evidence
enabling independent verification
📜 License

MIT License
© 2025 Motohiro Suzuki

EOF