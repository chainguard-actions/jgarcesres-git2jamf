<!-- markdownlint-disable -->

# Hardening Report: jgarcesres--git2jamf/v1.4

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **jgarcesres--git2jamf/v1.4** was hardened automatically. 2 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

The workflow file references actions by mutable tag refs instead of full 40-character commit SHAs, making the workflow vulnerable to supply-chain attacks if the tag is moved. Failing references: `actions/checkout@v3` (line 21) and `actions/setup-python@v1` (line 23). These should be pinned to their full SHA digests, e.g. `actions/checkout@11bd71901bbe5b1630ceea73d27597364c9af683 # v3`.

Locations:

- `.github/workflows/pythonapp.yml:21`
- `.github/workflows/pythonapp.yml:23`

### missing-permissions (severity: medium)

The workflow file has no top-level `permissions:` key and the only job (`build`) also has no job-level `permissions:` key. Without explicit permissions, the workflow inherits the repository's default token permissions (which may be `write-all` for older repositories), granting broader access than necessary. A minimal `permissions:` block (e.g. `contents: read`) should be added.

Locations:

- `.github/workflows/pythonapp.yml:1`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses, missing-permissions

**Notes:**

Fixed .github/workflows/pythonapp.yml: (1) Pinned `actions/checkout@v3` to full SHA `a37ce9120846195fa4ece8f58b268e6043cb2f26` and `actions/setup-python@v1` to full SHA `0f07f7f756721ebd886c2462646a35f78a8bc4de`, preserving the original tags as inline comments. (2) Added a top-level `permissions: contents: read` block to enforce least-privilege access.

