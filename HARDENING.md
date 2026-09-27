<!-- markdownlint-disable -->

# Hardening Report: actions--attest-build-provenance/predicate@0.1.0

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **actions--attest-build-provenance/predicate@0.1.0** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

action.yml references two actions using the mutable branch ref `@main` instead of a pinned 40-character commit SHA. This exposes the action to supply-chain attacks where a compromised upstream repository could inject malicious code. Failing references:
- `uses: actions/attest-build-provenance/predicate@main` (line 41)
- `uses: actions/attest@main` (line 43)

These should be pinned to full SHA digests, e.g. `uses: actions/attest@<40-char-sha> # main`.

Locations:

- `action.yml:41`
- `action.yml:43`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Pinned both mutable @main references in hardened/action/action.yml to full commit SHAs:
- `actions/attest-build-provenance/predicate@main` → `@9d57eef8c06cd9d6b433effeeb7a6a77b3ff94ad # main`
- `actions/attest@main` → `@a0eb68d51f3a5d373e107cfa9c8455ba800479cd # main`

