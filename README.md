# Portable SCM Demo Distribution

This tree is a non-authoritative, one-way distribution snapshot of Portable
SCM contract version 0.1. The private development repository remains the sole
source of truth. Changes to this distribution do not flow upstream and must
not be treated as authoritative product changes.

The portable boundary is:

`Company Source -> Company Adapter -> 7 Canonical Facts + run-config -> Portable Deterministic Analytics -> Structured Results -> Human-readable Report -> optional LLM Interpretation / Q&A`

All example inputs and outputs in this tree are synthetic. Do not place real
or company-specific data, mappings, paths, credentials, or connector settings
in this repository.

## Contents

- `contract/README.md` defines the seven canonical datasets, `run-config`,
  validation and missing-data semantics, output meanings, and the boundary
  between portable and company-specific responsibilities.
- `examples/input/` contains one synthetic canonical input set.
- `examples/output/` contains deterministic results generated from those exact
  input bytes by the accepted private implementation recorded in
  `DISTRIBUTION.json` and the sample manifests.

The CSV outputs are the machine-readable sources of truth. `report.md` is only
a deterministic human-readable projection; it introduces no new calculation,
classification, policy, or causality.

## Use boundary

This distribution is designed as a read-only contract and mapping reference.
Any actual execution, real source data, company mappings, canonicalized company
files, outputs, and local evidence must remain inside an independently
authorized company-controlled environment. Technical readiness in the sample
manifest is not authorization to begin a pilot.

Repository access, if separately authorized later, should be least-privilege
read-only access to this distribution alone. Never store a token or credential
in this tree.
