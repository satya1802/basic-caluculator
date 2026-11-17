<!-- sdlc:auto:start adr -->
# ADR-0004: Use AWS for Cloud

Status: Accepted  
Date: 2026-11-17

## Context and Problem Statement

Which Cloud technology does the project use? Decided in architecture v1.

## Considered Options

- AWS
- Google Cloud
- Azure

## Decision Outcome

Chosen option: AWS, because AWS is the approved cloud and serves the free, public, lightweight app with no special configuration: CloudFront fronts the static SPA for global low-latency reach and App Runner hosts the thin API, meeting NFR-005 (reachable by the public at scale).

## Consequences

A static-only deploy would be even simpler, but keeping App Runner and RDS aligns the deployment with the approved backend and database layers.
<!-- sdlc:auto:end adr -->