# Project Structure

This document outlines the structure and organization of the Social application.

## Directory Structure

```
social/
├── main.go              # Application entry point
├── go.mod               # Go module configuration
├── .gitignore           # Git ignore rules
├── README.md            # Project overview and setup instructions
├── CHANGELOG.md         # Version history and changes
└── docs/                # Project documentation
    ├── project-structure.md  # This file
    ├── development.md        # Development setup and guidelines
    └── api.md               # API documentation (coming soon)
```

## File Responsibilities

### Root Level Files

- **main.go**: The main entry point for the Go application. Currently empty, ready for initial application setup.
- **go.mod**: Defines the Go module as `social.robertgleason.ca` with Go 1.25.0 requirement.
- **.gitignore**: Comprehensive ignore rules for JetBrains IDEs and common Go build artifacts.

### Documentation (`/docs`)

- **project-structure.md**: This file - explains the project organization.
- **development.md**: Development setup, coding standards, and contribution guidelines.
- **api.md**: Will contain API endpoint documentation as the project develops.

## Module Information

- **Module Name**: `social.robertgleason.ca`
- **Go Version**: 1.25.0
- **Type**: Social networking application

## Development Notes

The project is currently in initial setup phase. The main.go file is ready for the first implementation of core application structure, routing, and basic server setup.

---
*Last updated: September 1, 2025 - v0.1.0*
