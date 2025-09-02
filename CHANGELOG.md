# Changelog

All notable changes to the Social project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [v0.2.0] - 2025-09-01

### Added
- HTTP server application under `cmd/api` using chi v5 router
- Middleware stack: RequestID, RealIP, Logger, Recoverer, Timeout (60s)
- Health check endpoint: `GET /v1/health` returns `200 OK` with body `OK`
- Environment helpers in `internal/env` for string/int lookup
- Development tooling scaffold: `.air.toml` and `.envrc`

### Changed
- Run instructions updated to `go run ./cmd/api`
- Documentation refreshed: README, Development guide, Project structure

### Fixed
- Clarified environment variable usage for `ADDR` (defaults to `:8080`)

### Removed
- N/A

## [v0.1.0] - 2025-09-01

### Added
- Initial project setup with Go module `social.robertgleason.ca`
- Go 1.25.0 configuration
- Basic project structure with main.go entry point
- Git repository initialization with comprehensive .gitignore
- JetBrains IDE configuration support
- Professional documentation structure (README.md, CHANGELOG.md)

### Changed
- N/A

### Fixed
- N/A

### Removed
- N/A

---

[v0.2.0]: Added core API server, middleware, health endpoint, and env helpers
[v0.1.0]: Initial release
