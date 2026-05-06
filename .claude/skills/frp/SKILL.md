```markdown
# frp Development Patterns

> Auto-generated skill from repository analysis

## Overview

This skill teaches you the key development patterns, coding conventions, and workflows used in the `frp` project—a fast reverse proxy written in Go. You'll learn how to contribute effectively by following established practices for code organization, configuration management, feature development, testing, and release management.

## Coding Conventions

- **Language:** Go
- **Framework:** Native Go (no external frameworks detected)
- **File Naming:** Uses `snake_case` for file names.
  - Example: `client_service.go`, `proxy_manager.go`
- **Import Style:** Relative imports are preferred.
  - Example:
    ```go
    import (
        "github.com/fatedier/frp/pkg/config"
        "github.com/fatedier/frp/server/proxy"
    )
    ```
- **Export Style:** Named exports for functions, types, and variables.
  - Example:
    ```go
    // Exported function
    func StartService() { ... }

    // Exported type
    type ProxyManager struct { ... }
    ```
- **Commit Messages:** Freeform, average length ~41 characters. No strict prefixing.

## Workflows

### Release Version Bump
**Trigger:** When preparing a new release or patch version.  
**Command:** `/release-bump`

1. Update the version in `pkg/util/version/version.go`.
2. Update `README.md` and/or `README_zh.md` with new version info.
3. Update `Release.md` with release notes.
4. Update or touch `Makefile`, `go.mod`, and `go.sum` as needed.
5. Update configuration files such as `conf/frpc_full.ini` and `conf/frps_full.ini`.
6. Update or touch test files and assets if required.
7. Update or touch web UI assets in `assets/frpc/static/*`, `assets/frps/static/*`, `web/frpc/*`, and `web/frps/*`.
8. Update or touch `client/service.go` and `server/service.go` as needed.

### Config Schema Update
**Trigger:** When adding or changing configuration options for client/server/proxy.  
**Command:** `/config-schema-update`

1. Edit configuration files: `pkg/config/client.go`, `pkg/config/server.go`, `pkg/config/proxy.go`, or related.
2. Update corresponding test files: `*_test.go`.
3. Update example configuration files: `conf/frpc_full.ini`, `conf/frps_full.ini`.
4. Update documentation if necessary.
5. Update code that consumes configuration (e.g., `client/service.go`, `server/service.go`).
6. Update or touch `test/e2e` and `tests/ci` files as needed.

### Proxy Feature Development
**Trigger:** When implementing a new proxy type or updating proxy logic.  
**Command:** `/proxy-feature`

1. Edit or add files in `server/proxy/` (e.g., `http.go`, `udp.go`, `tcpmux.go`, etc.).
2. Edit or add files in `client/proxy/` (e.g., `proxy.go`, `general_tcp.go`, etc.).
3. Update `pkg/config/proxy.go` and/or `pkg/config/visitor.go`.
4. Update or add command files in `cmd/frpc/sub/*.go`.
5. Update tests in `test/e2e/basic/*`, `test/e2e/features/*`, `test/e2e/plugin/*`.
6. Update or touch documentation if needed.

### Test Suite Update
**Trigger:** When adding new features, fixing bugs, or improving test coverage.  
**Command:** `/update-tests`

1. Edit or add files in `test/e2e/*` (basic, features, plugin, etc.).
2. Edit or add files in `tests/ci/*`.
3. Edit or add files in `tests/mock/*` or `test/e2e/mock/*`.
4. Update or touch related config or code files as needed.

### Web UI Assets Update
**Trigger:** When making changes to the web dashboard or updating frontend dependencies.  
**Command:** `/web-ui-update`

1. Edit or add files in `web/frpc/*` or `web/frps/*`.
2. Rebuild assets and update `assets/frpc/static/*` or `assets/frps/static/*`.
3. Update or touch `README.md` or documentation as needed.

### CI/CD Workflow Update
**Trigger:** When changing build, lint, or release automation.  
**Command:** `/ci-cd-update`

1. Edit or add files in `.github/workflows/*`, `.circleci/config.yml`, `.travis.yml`, `.golangci.yml`.
2. Update `Makefile` or `package.sh` if needed.

## Testing Patterns

- **Test Framework:** Not explicitly specified; uses Go's standard testing tools.
- **Test File Pattern:** Test files are named with the `_test.go` suffix.
  - Example: `client_test.go`, `proxy_test.go`
- **Test Structure:** Standard Go test functions.
  - Example:
    ```go
    func TestProxyStart(t *testing.T) {
        // test logic here
    }
    ```
- **Test Locations:** Tests are found in `test/e2e/`, `tests/ci/`, `tests/mock/`, and as unit tests alongside implementation files.

## Commands

| Command             | Purpose                                                   |
|---------------------|-----------------------------------------------------------|
| /release-bump       | Prepare and execute a new release version bump            |
| /config-schema-update | Update or extend the configuration schema                |
| /proxy-feature      | Add or update a proxy type or related feature             |
| /update-tests       | Update or add to the automated test suites                |
| /web-ui-update      | Update or rebuild the web UI assets                       |
| /ci-cd-update       | Update or add CI/CD workflow files                        |
```