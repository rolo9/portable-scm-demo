# Portable SCM v0.1 Demo Distribution

This is a non-authoritative, one-way curated distribution snapshot. The private source-of-truth repository remains the only development and governance authority. Updates flow only from an explicitly accepted private commit into a newly reviewed distribution; edits to a distributed copy never flow upstream automatically.

## Scope

The portable architecture is:

`Company Source → Company Adapter → 7 Canonical Facts + run-config → Portable Deterministic Analytics → Structured Results → Human-readable Report → optional interpretation / Q&A`

This snapshot contains only the canonical contract, one synthetic example input set, and outputs generated from that example. It contains no executable Core. All example `item_code` values beginning with `SYN-` are wholly synthetic; they are not real, anonymized, or transformed company data.

Use this distribution as a read-only reference. Real data, source mappings, canonicalized company files, execution outputs, and evidence must remain inside the approved company-controlled environment. No credentials belong in this distribution.

## Authority and version

[`DISTRIBUTION.json`](DISTRIBUTION.json) identifies the distribution, contract version, and accepted private Source commit used to produce the sample. If distributed semantics conflict with an accepted private Source, the accepted private Source wins and this snapshot is stale pending a new reviewed distribution.

## Adapter boundary

The Portable / Generic side owns canonical filenames, schemas, grains, validation and normalization, run configuration, deterministic analytical semantics, structured-output meaning, and generic report semantics.

The Company Adapter remains outside this distribution. It owns company source discovery, workbook/sheet/column and file conventions, source quirks, source-to-canonical mapping, proprietary cost retrieval, REPORTED/CALCULATED fact construction, confidential paths and values, and runtime-specific wiring. No Company Adapter is implemented here.

See [`contract/README.md`](contract/README.md) for the complete public contract and [`examples/input`](examples/input) / [`examples/output`](examples/output) for the synthetic example.
