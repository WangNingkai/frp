---
name: config-schema-update
description: Workflow command scaffold for config-schema-update in frp.
allowed_tools: ["Bash", "Read", "Write", "Grep", "Glob"]
---

# /config-schema-update

Use this workflow when working on **config-schema-update** in `frp`.

## Goal

Update or extend the configuration schema, often for new features or options.

## Common Files

- `pkg/config/client.go`
- `pkg/config/server.go`
- `pkg/config/proxy.go`
- `pkg/config/visitor.go`
- `pkg/config/client_test.go`
- `pkg/config/server_test.go`

## Suggested Sequence

1. Understand the current state and failure mode before editing.
2. Make the smallest coherent change that satisfies the workflow goal.
3. Run the most relevant verification for touched files.
4. Summarize what changed and what still needs review.

## Typical Commit Signals

- Edit pkg/config/client.go, pkg/config/server.go, pkg/config/proxy.go, or related config files
- Update corresponding *_test.go files
- Update conf/frpc_full.ini, conf/frps_full.ini, or other config examples
- Update documentation if needed
- Update code that consumes config (client/service.go, server/service.go, etc.)

## Notes

- Treat this as a scaffold, not a hard-coded script.
- Update the command if the workflow evolves materially.