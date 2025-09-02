# Development Guide

This document provides setup instructions and guidelines for developing the Social application.

## Local Development Setup

### Prerequisites
- Go 1.25.0 or higher
- Git
- Optional: direnv (for environment variables), Air (for hot reload)

### Environment Setup

1. Clone and navigate
   ```bash
   git clone <repository-url>
   cd social
   ```

2. Verify Go installation
   ```bash
   go version
   # Expect: go version go1.25.0 or higher
   ```

3. Install dependencies
   ```bash
   go mod tidy
   ```

4. Configure environment (optional)
   - Default listen address: `:8080`
   - Override via environment variable:
     ```bash
     export ADDR=":1000"
     ```
   - If using direnv, add to `.envrc` then run `direnv allow`.

5. Run the application
   ```bash
   # From project root
   go run ./cmd/api
   ```

6. Optional: Hot reload with Air
   ```bash
   # Install once
   go install github.com/air-verse/air@latest

   # Start watcher (from project root)
   air
   ```
   Notes:
   - Air builds `./cmd/api` to `./bin/main` using `.air.toml`.
   - Proxy is disabled by default; access the app on `ADDR` (default `:8080`).

## Verifying the Server

- Health check endpoint:
  ```bash
  curl -i http://localhost:8080/v1/health
  ```
  Expected:
  ```
  HTTP/1.1 200 OK
  ...
  OK
  ```

## Project Configuration

- Module path: `social.robertgleason.ca`
- Web framework: chi v5
- Middleware: RequestID, RealIP, Logger, Recoverer, Timeout(60s)
- Env helpers: `internal/env` (string/int lookups with fallbacks)

## Development Workflow

- Code formatting: `gofmt` (enforced by IDE/CI later)
- Logging: Use standard library `log` for now
- Routing: Add routes under `/v1` in `cmd/api/api.go`
- Handlers: Add new handler methods on `application` type in `cmd/api`

## Testing

```bash
# Run all tests
go test ./...

# With coverage
go test -cover ./...
```

## Building

```bash
# Build API
go build -o bin/main ./cmd/api

# Example cross-compilation
GOOS=linux GOARCH=amd64 go build -o bin/main-linux ./cmd/api
GOOS=windows GOARCH=amd64 go build -o bin/main-windows.exe ./cmd/api
```

## Troubleshooting

- Port already in use
  - Change port: `export ADDR=":1000"`
  - Or kill the process holding the port: `lsof -i :8080`
- Env variable not applied
  - Confirm shell exported variable or `direnv reload`
- Air not rebuilding
  - Ensure Air is installed and `.air.toml` exists at project root

## Deployment

- Minimal binary deploy available via `go build` output in `bin/`
- Add a process manager or containerize (Dockerfile planned in roadmap)

---
Last updated: September 1, 2025 - v0.2.0
