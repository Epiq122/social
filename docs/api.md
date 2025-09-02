# API Documentation

This document describes the currently available API endpoints for the Social application.

Base path: /v1

- Health Check
  - Method: GET
  - Path: /v1/health
  - Description: Liveness/readiness probe; returns 200 OK if the service is accepting requests.
  - Request
    - Headers: none required
    - Body: none
  - Response
    - Status: 200 OK
    - Headers: Content-Type: text/plain; charset=utf-8
    - Body: OK
  - cURL example
    ```bash
    curl -i http://localhost:8080/v1/health
    ```

Notes
- More endpoints will be added under /v1 as features are implemented.
- The service listens on the address defined by the ADDR environment variable (default :8080).

---
Last updated: September 1, 2025 - v0.2.0

