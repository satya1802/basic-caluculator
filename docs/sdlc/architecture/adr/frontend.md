<!-- sdlc:auto:start adr -->
# ADR-0001: Use React 19 for Frontend

Status: Accepted  
Date: 2026-11-17

## Context and Problem Statement

Which Frontend technology does the project use? Decided in architecture v1.

## Considered Options

- React 19
- Vue 3
- Svelte

## Decision Outcome

Chosen option: React 19, because React 19 is the approved frontend and hosts the entire product; the calculator UI is assembled from Magic UI components, which are React components that drop straight into a React app and preview through the Magic UI MCP integration (US-011). All arithmetic and input handling run in these components in the browser.

## Consequences

A full SPA framework is heavier than vanilla JS for so small an app, but React is mandated and gives direct Magic UI compatibility and a familiar component model for the responsive layout.
<!-- sdlc:auto:end adr -->