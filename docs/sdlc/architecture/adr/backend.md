<!-- sdlc:auto:start adr -->
# ADR-0002: Use FastAPI 0.115 for Backend

Status: Accepted  
Date: 2026-11-17

## Context and Problem Statement

Which Backend technology does the project use? Decided in architecture v1.

## Considered Options

- FastAPI 0.115
- Flask
- Express

## Decision Outcome

Chosen option: FastAPI 0.115, because FastAPI 0.115 is the approved backend, kept as a thin shell serving a health check and reserving room for future operational endpoints. There is no calculator business logic server-side because calculations run entirely in the browser (NFR-002).

## Consequences

The service carries no feature load today, so it adds deploy surface for little immediate use; it is retained to satisfy the approved layer and to make future server-side needs cheap to add.
<!-- sdlc:auto:end adr -->