# Project Structure

This document outlines the structure and organization of the Social application.

## Directory Structure

```
social/
├── .air.toml                 # Air (hot reload) configuration
├── .envrc                    # Local environment variables (ADDR, etc.)
├── CHANGELOG.md              # Version history and changes
├── README.md                 # Project overview and setup instructions
├── go.mod                    # Go module configuration
├── go.sum                    # Go dependencies lockfile
├── bin/                      # Built binaries (ignored from VCS)
│   └── main                  # Air build target
├── cmd/
│   ├── api/                  # API service entrypoint and HTTP server
│   │   ├── api.go            # Router, middleware, server run loop
│   │   ├── health.go         # Health check handler
│   │   └── main.go           # Bootstraps config and starts the server
│   └── migrate/
│       └── migrations/       # Database migrations (placeholder)
├── docs/                     # Project documentation
│   ├── api.md                # API endpoints and examples
│   ├── development.md        # Dev setup and workflows
│   ├── project-structure.md  # This file
│   └── architecture.md       # Architectural decisions and rationale
├── internal/
│   └── env/
│       └── env.go            # Environment helpers (string/int)
├── scripts/                  # Helper scripts (future)
└── tmp/                      # Temp files used by tooling
```

## Responsibilities

- cmd/api: Contains the API application with routing and handlers.
- internal/env: Helpers for reading environment variables with sane fallbacks.
- docs: Living documentation for developers and contributors.
- bin: Output directory for compiled binaries (e.g., Air builds here).
- scripts: Shell or Go helper scripts (to be added as the project evolves).

## Notes

- The server mounts routes under `/v1` and currently exposes `GET /v1/health`.
- Listening address is configured via `ADDR` environment variable (default `:8080`).
- Air proxy is disabled by default; access the app directly via `ADDR`.

---
Last updated: September 1, 2025 - v0.2.0
