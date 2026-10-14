# QAM framework interface

A standalone, read-only concept interface for the QAM/MML/MMA structure in Marc Brendecke's **Quantum Sphaera Companion**. Includes a tensor-role audit adapter, explicit assumptions and residuals, and reproducible SHA-512 receipts.

This package is shared as an integration reference for Trent Slade and QEC. It contains only interface code, documentation, examples, tests and an operational rule catalog. The private Companion repository, TeX sources and research history are not included.

## Concept boundary

- **QAM** records typed objects, declared relationships, guards, scope, provenance and residual witnesses.
- **MML** provides fixed `EXPORT` and `SCRUB` requests.
- **MMA** returns `continue`, `guard` or `reject` without changing the context.
- The **tensor-role adapter** checks supported index pairings, explicit same-variance comparisons, same-kind tensor formation, finite Boolean selectors and guarded mixed readouts.

`QClEq` remains a separately declared mathematical relationship. Equal representation fingerprints do not prove equivalence. Successful checks do not prove mathematical admissibility, vanishing residuals or closure. The interface does not parse LaTeX, evaluate numerical tensors or execute arbitrary code.

## Run

Python 3.10+ is sufficient; there are no third-party dependencies. Run from this repository root:

```text
python -B -m unittest discover -s scripts/qsc_audit/tests -v
python -B scripts/qsc_audit/framework_interface.py scripts/qsc_audit/examples/framework_context.json scripts/qsc_audit/examples/framework_tensor_request.json --output build/audit/framework_tensor.report.json
python -B scripts/qsc_audit/framework_interface.py scripts/qsc_audit/examples/framework_context.json scripts/qsc_audit/examples/framework_tensor_request.json --verify build/audit/framework_tensor.report.json
```

Validation: **47 tests**, including positive/negative role checks, scoped guard propagation, unresolved relationships and residuals, SHA-512 identities, report tampering and source-free packaging. The positive example accepts seven local operations while retaining an open residual and unresolved equivalence declaration.

The schemas are `qsc-framework-interface/2` and `qam-role-audit/2`. All hashes use SHA-512 (128 lowercase hexadecimal characters).

## Source binding

In this standalone package, `rule_catalog.json` provides operational rule summaries and links to the public Companion publications. Receipts identify this as `source_binding.mode = "bundled_rule_catalog"` and `source_text_available = false`. The catalog fingerprint does not authenticate unavailable original TeX text. A complete Companion checkout can instead fingerprint its local original source files.

Public publication references: [Companion concept DOI](https://doi.org/10.5281/zenodo.19210728), [Companion v4.7.0](https://doi.org/10.5281/zenodo.20232911).

## Review and possible QEC integration

Start with the [English handoff for Trent / QEC](scripts/qsc_audit/QEC_HANDOFF.md), the [framework concept and API](scripts/qsc_audit/FRAMEWORK_INTERFACE.md), and the [tensor-role checker documentation](scripts/qsc_audit/TENSOR_GRAMMAR.md).

QEC's existing SHA-256 identities and this versioned SHA-512 interface require an explicit adapter or migration design before replacing existing receipt formats. No QEC source was copied into this package. Please coordinate attribution and software licensing with Marc before upstream incorporation or redistribution.
