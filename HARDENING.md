<!-- markdownlint-disable -->

# Hardening Report: jgarcesres--git2jamf/v1.2

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **jgarcesres--git2jamf/v1.2** was hardened automatically. 2 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

The workflow file uses mutable tag-based action references instead of pinned SHA digests. `actions/checkout@v2` and `actions/setup-python@v1` are both tag references that can be silently changed by the upstream repository, enabling supply-chain attacks.

Locations:

- `.github/workflows/pythonapp.yml:18`
- `.github/workflows/pythonapp.yml:20`

### missing-permissions (severity: medium)

The workflow file `.github/workflows/pythonapp.yml` has no top-level `permissions:` key and the `build` job also has no job-level `permissions:` key. Without explicit permissions, the workflow runs with the default (potentially broad) GITHUB_TOKEN permissions, which may include write access to repository contents.

Locations:

- `.github/workflows/pythonapp.yml:1`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses, missing-permissions

**Notes:**

1. Pinned `actions/checkout@v2` to SHA `0717577d45739eb3c851188b29f50ed6c0b2194e` and `actions/setup-python@v1` to SHA `0f07f7f756721ebd886c2462646a35f78a8bc4de`, preserving the original tags as inline comments.
2. Added `permissions: {}` at the top level of the workflow, granting no GITHUB_TOKEN permissions since the workflow only performs read-only operations (checkout, install deps, lint).

