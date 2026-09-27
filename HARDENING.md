<!-- markdownlint-disable -->

# Hardening Report: actions--attest-build-provenance/predicate@1.1.5

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **actions--attest-build-provenance/predicate@1.1.5** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

The `uses:` reference `actions/attest@v2.2.1` in action.yml is pinned to a version tag rather than a full 40-character commit SHA. This means the action could be silently updated or replaced by a supply-chain attacker without changing the reference. It should be pinned to a specific commit SHA (e.g., `actions/attest@<40-char-sha> # v2.2.1`).

Locations:

- `action.yml:72`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Pinned actions/attest@v2.2.1 to its full commit SHA: actions/attest@a63cfcc7d1aab266ee064c58250cfc2c7d07bc31 # v2.2.1 in hardened/action/action.yml at line 72.

