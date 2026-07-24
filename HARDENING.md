<!-- markdownlint-disable -->

# Hardening Report: actions--attest-build-provenance/v4.1.1

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **actions--attest-build-provenance/v4.1.1** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### script-injection (severity: high)

Sub-rule (a): A ${{ }} expression is directly interpolated inside a `run:` shell command. The step `run: jq < ${{ steps.attest-provenance.outputs.bundle-path }}` embeds a step output directly into the shell command string. Before the shell executes the command, GitHub Actions substitutes the expression value verbatim into the script, allowing an attacker who can influence the step output to inject arbitrary shell commands. The offending line is: `run: jq < ${{ steps.attest-provenance.outputs.bundle-path }}`. Fix: move the value into an env var and reference it as a quoted shell variable, e.g. `env: BUNDLE_PATH: ${{ steps.attest-provenance.outputs.bundle-path }}` then `run: jq < "$BUNDLE_PATH"`.

Locations:

- `.github/workflows/ci.yml:34`

## Iteration Notes

### Iteration 1

**Fixes applied:** script-injection

**Notes:**

Fixed script injection in hardened/action/.github/workflows/ci.yml line 34. Moved `${{ steps.attest-provenance.outputs.bundle-path }}` out of the `run:` shell command and into an `env:` block as `BUNDLE_PATH`. Updated the run command from `jq < ${{ steps.attest-provenance.outputs.bundle-path }}` to `jq < "$BUNDLE_PATH"` to prevent attacker-controlled step output values from being interpreted as shell commands.

