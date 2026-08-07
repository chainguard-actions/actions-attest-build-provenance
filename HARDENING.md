<!-- markdownlint-disable -->

# Hardening Report: actions--attest-build-provenance/v4.2.2

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **actions--attest-build-provenance/v4.2.2** was hardened automatically. 0 finding(s) were identified and resolved across 1 iteration(s).

## Iteration Notes

### Iteration 1

**Fixes applied:** script-injection

**Notes:**

Fixed script injection in `.github/workflows/ci.yml` at the "Dump output" step. Moved `${{ steps.attest-provenance.outputs.bundle-path }}` from the `run:` shell string into an `env:` block as `BUNDLE_PATH`, and updated the shell command to use the quoted variable `"$BUNDLE_PATH"` instead of the raw expression.

