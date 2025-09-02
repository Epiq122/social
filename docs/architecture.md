# Architecture and Decisions

This document records key architectural choices for the Social application and the rationale behind them.

## Goals
- Simple, maintainable API service as a foundation for future features.
- Clear separation of concerns and predictable project layout.
- Developer-friendly local setup with minimal friction.

## Service Layout
- Entry point: `cmd/api` (Go convention to place binaries under `cmd/<name>`)
- Internal packages: `internal/*` for code not intended for public reuse (e.g., `internal/env`)
- Documentation: `docs/*` as the living source of truth for contributors

## Routing and Middleware
- Router: `github.com/go-chi/chi/v5`
  - Lightweight and idiomatic for Go HTTP services
  - Composable middleware and straightforward route nesting
- Middleware stack (in `cmd/api/api.go`):
  - `RequestID`: correlate requests across logs
  - `RealIP`: capture client IP behind proxies
  - `Logger`: basic request logging for visibility
  - `Recoverer`: protect against panics and return 500 safely
  - `Timeout(60s)`: bound request lifecycle
- API versioning: all endpoints are mounted under `/v1` to allow non-breaking future changes.

## Configuration
- Environment-first configuration via `internal/env` helpers
  - `ADDR` controls listen address; defaults to `:8080`
  - Helpers provide sane fallbacks and basic parsing
- Local development helpers:
  - `.envrc` for direnv users (optional)
  - `.air.toml` to speed up feedback with hot reload; proxy disabled by default

## Health and Observability
- `GET /v1/health`: simple liveness/readiness indicator returning `200 OK` with body `OK`
- Logging: standard library `log` for now; can be replaced with structured logging later

## Error Handling
- Centralized through middleware `Recoverer` and explicit error returns from handlers
- HTTP server configured with read/write/idle timeouts to mitigate slowloris and similar issues

## Future Considerations
- Authentication and authorization layer (JWT/OAuth2)
- Domain modeling and persistence (SQL with migrations)
- Structured logging and tracing (OpenTelemetry)
- Rate limiting and request validation
- API pagination, filtering, and consistent error envelopes

---
Last updated: September 1, 2025 - v0.2.0

