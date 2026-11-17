<!-- sdlc:auto:start adr -->
# ADR-0003: Use PostgreSQL 16 for Database

Status: Accepted  
Date: 2026-11-17

## Context and Problem Statement

Which Database technology does the project use? Decided in architecture v1.

## Considered Options

- PostgreSQL 16
- SQLite
- DynamoDB

## Decision Outcome

Chosen option: PostgreSQL 16, because PostgreSQL 16 is the approved database, provisioned empty to fill the data layer. The product stores no user data, history or accounts (NFR-003, AC-028), so no schema holds user-facing data.

## Consequences

Running a database that stores nothing is pure overhead at this scope; it is kept only to honour the approved stack and to be ready if persistence is ever introduced.
<!-- sdlc:auto:end adr -->