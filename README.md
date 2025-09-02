# Social

A modern social networking application built with Go, designed for scalable and efficient social interactions.

## Version
**Current Version:** v0.2.0

## Features
- Core HTTP server with structured routing
- Health check endpoint: `GET /v1/health`
- Request middleware: request ID, real IP, logging, recoverer, timeouts
- Environment-driven configuration (ADDR with default `:8080`)
- Development tooling scaffold (Air config present, `.envrc` for local env)

## Installation

### Prerequisites
- Go 1.25.0 or higher
- Git
- Optional: Air (live reload) and direnv for environment management

### Setup
1. Clone the repository:
   ```bash
   git clone <repository-url>
   cd social
   ```

2. Install dependencies:
   ```bash
   go mod tidy
   ```

3. Configure environment (optional):
   - By default the server listens on `:8080`.
   - To override, set `ADDR`, e.g.:
     ```bash
     export ADDR=":1000"   # bash/zsh
     ```
   - If you use direnv, add/update `.envrc` accordingly then run `direnv allow`.

4. Run the application:
   ```bash
   # Run without hot reload
   go run ./cmd/api
   ```

5. Run with hot reload (optional):
   ```bash
   # Install Air if needed
   go install github.com/air-verse/air@latest

   # From project root
   air
   ```
   Notes:
   - Air builds `./cmd/api` into `./bin/main` as configured in `.air.toml`.
   - By default, the app listens on `ADDR` (default `:8080`).

## Usage
- Health check:
  ```bash
  curl -i http://localhost:8080/v1/health
  ```
  Expected response:
  ```
  HTTP/1.1 200 OK
  ...
  OK
  ```

## Tech Stack
- Backend: Go 1.25.0
- Web: chi v5 (router and middleware)
- Module: `social.robertgleason.ca`
- Dev: Air (hot reload), direnv (env), JetBrains IDE support

## Roadmap
- [x] Core application structure and routing
- [x] Health endpoint and base middleware
- [ ] User authentication and authorization
- [ ] Social features (posts, comments, likes)
- [ ] Real-time messaging
- [ ] API documentation expansion
- [ ] Database integration
- [ ] Frontend interface
- [ ] Deployment configuration

## License
License to be determined. If you plan to contribute or use this code, please check back for a LICENSE file or reach out to the maintainers.

---
Last updated: September 1, 2025
