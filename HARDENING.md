<!-- markdownlint-disable -->

# Hardening Report: actions--attest-build-provenance/v4.1.0

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **actions--attest-build-provenance/v4.1.0** was hardened automatically. 2 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

The workflow references `actions/attest-build-provenance@v3` using a mutable tag instead of a pinned 40-character commit SHA. This exposes the workflow to supply-chain attacks where the tag could be silently moved to point to malicious code.

Locations:

- `.github/workflows/prober.yml:24`

### script-injection (severity: high)

Rule (a) violation: A `${{ ... }}` expression is interpolated directly inside a `run:` shell command. The step `Dump output` uses `run: jq < ${{ steps.attest-provenance.outputs.bundle-path }}`, which injects the `steps.*.outputs.*` context value directly into the shell command string before the shell ever sees it. If the output value contains shell metacharacters, this can lead to command injection.

Locations:

- `.github/workflows/ci.yml:33`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses, script-injection

**Notes:**

1. prober.yml line 24: Pinned `actions/attest-build-provenance@v3` to full commit SHA `977bb373ede98d70efdf65b84cb5f73e068dcc2a` with `# v3` comment for readability. 2. ci.yml line 33: Fixed script injection in the 'Dump output' step by moving `${{ steps.attest-provenance.outputs.bundle-path }}` into an `env:` block as `BUNDLE_PATH`, then referencing it as `"$BUNDLE_PATH"` in the shell command instead of interpolating the expression directly.

