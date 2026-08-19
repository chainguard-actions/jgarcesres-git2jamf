<!-- markdownlint-disable -->

# Hardening Report: jgarcesres--git2jamf/v1.1

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **jgarcesres--git2jamf/v1.1** was hardened automatically. 2 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### permissions (severity: medium)

missing-permissions: The workflow file .github/workflows/pythonapp.yml has no top-level `permissions:` key, and the single job `build` also has no job-level `permissions:` key. This means the workflow runs with the default (potentially broad) GITHUB_TOKEN permissions.

Locations:

- `.github/workflows/pythonapp.yml:1`

### unpinned-uses (severity: high)

The workflow file .github/workflows/pythonapp.yml references actions using mutable tags instead of full 40-character commit SHAs, making the workflow vulnerable to supply-chain attacks if the tag is moved. Failing references: `actions/checkout@v2` (line 20) and `actions/setup-python@v1` (line 22).

Locations:

- `.github/workflows/pythonapp.yml:20`
- `.github/workflows/pythonapp.yml:22`

## Iteration Notes

### Iteration 1

**Fixes applied:** permissions, unpinned-uses

**Notes:**

Fixed .github/workflows/pythonapp.yml: (1) Added `permissions: {}` at the top level to restrict GITHUB_TOKEN to no permissions by default. (2) Pinned `actions/checkout@v2` to full SHA `0717577d45739eb3c851188b29f50ed6c0b2194e` and `actions/setup-python@v1` to full SHA `0f07f7f756721ebd886c2462646a35f78a8bc4de`, with original tags preserved in comments.

