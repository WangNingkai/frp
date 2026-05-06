---
name: release-version-bump
description: Workflow command scaffold for release-version-bump in frp.
allowed_tools: ["Bash", "Read", "Write", "Grep", "Glob"]
---

# /release-version-bump

Use this workflow when working on **release-version-bump** in `frp`.

## Goal

Bump the project version for a new release, including changelog, documentation, and code updates.

## Common Files

- `pkg/util/version/version.go`
- `README.md`
- `README_zh.md`
- `Release.md`
- `Makefile`
- `go.mod`

## Suggested Sequence

1. Understand the current state and failure mode before editing.
2. Make the smallest coherent change that satisfies the workflow goal.
3. Run the most relevant verification for touched files.
4. Summarize what changed and what still needs review.

## Typical Commit Signals

- Update version in version.go (or pkg/util/version/version.go)
- Update README.md and/or README_zh.md
- Update Release.md
- Update or touch Makefile, go.mod, go.sum as needed
- Update configuration files (conf/frpc_full.ini, conf/frps_full.ini, etc.)

## Notes

- Treat this as a scaffold, not a hard-coded script.
- Update the command if the workflow evolves materially.