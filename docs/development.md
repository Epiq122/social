# Development Guide

This document provides setup instructions and guidelines for developing the Social application.

## Local Development Setup

### Prerequisites
- Go 1.25.0 or higher
- Git
- A code editor (JetBrains GoLand/IntelliJ IDEA recommended - already configured)

### Environment Setup

1. **Clone and Navigate**
   ```bash
   git clone <repository-url>
   cd social
   ```

2. **Verify Go Installation**
   ```bash
   go version
   # Should output: go version go1.25.0 or higher
   ```

3. **Initialize Dependencies**
   ```bash
   go mod tidy
   ```

4. **Run the Application**
   ```bash
   go run main.go
   ```

## Project Configuration

### Go Module
- **Module Path**: `social.robertgleason.ca`
- **Go Version**: 1.25.0
- **Dependencies**: None currently (will be added as features develop)

### IDE Configuration
The project includes JetBrains IDE configuration in the `.idea/` folder, providing:
- Code formatting standards
- Go-specific settings
- Debug configurations (to be added)

## Development Workflow

### Branch Strategy
*To be defined based on team preferences*

### Code Standards
- Follow standard Go conventions (`gofmt`, `golint`)
- Use meaningful variable and function names
- Include comprehensive comments for public APIs
- Write unit tests for all core functionality

### Testing
```bash
# Run tests
go test ./...

# Run tests with coverage
go test -cover ./...
```

### Building
```bash
# Build for current platform
go build -o social main.go

# Cross-platform builds (examples)
GOOS=linux GOARCH=amd64 go build -o social-linux main.go
GOOS=windows GOARCH=amd64 go build -o social-windows.exe main.go
```

## Next Development Steps

1. Implement basic HTTP server in `main.go`
2. Set up routing structure
3. Define core data models
4. Implement authentication system
5. Add database layer
6. Create API endpoints

## Deployment

*Deployment instructions will be added as the application develops.*

---
*Last updated: September 1, 2025 - v0.1.0*
