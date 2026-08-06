<!-- markdownlint-disable -->

# Hardening Report: screendriver--ifttt-action/v1.0.0

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **screendriver--ifttt-action/v1.0.0** was hardened automatically. 2 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

The workflow file .github/workflows/ci.yml references GitHub Actions using mutable branch/tag refs instead of full 40-character commit SHAs. This exposes the workflow to supply-chain attacks if the referenced action is compromised or the tag/branch is moved. Failing references: `uses: actions/checkout@master` (branch ref) and `uses: actions/setup-node@v1` (tag ref). These should be pinned to their full SHA digests, e.g. `actions/checkout@<40-char-sha> # master` and `actions/setup-node@<40-char-sha> # v1`.

Locations:

- `.github/workflows/ci.yml:8`
- `.github/workflows/ci.yml:10`

### missing-permissions (severity: medium)

The workflow file .github/workflows/ci.yml has no top-level `permissions:` key and the single job `build` also has no `permissions:` key. Without explicit permissions, the workflow runs with the default (potentially broad) GITHUB_TOKEN permissions. A minimal permissions block (e.g. `permissions: read-all` or specific scopes like `contents: read`) should be added at the top level or on the job.

Locations:

- `.github/workflows/ci.yml:1`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses, missing-permissions

**Notes:**

Fixed .github/workflows/ci.yml: (1) Pinned actions/checkout@master to full SHA 61b9e3751b92087fd0b06925ba6dd6314e06f089 # master; (2) Pinned actions/setup-node@v1 to full SHA f1f314fca9dfce2769ece7d933488f076716723e # v1; (3) Added top-level `permissions: contents: read` block to restrict GITHUB_TOKEN to the minimum required scope.

