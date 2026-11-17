# Deployment Guide

> Maintained by QuorQ AI SDLC. Text between `sdlc:auto` markers is regenerated; anything outside them is yours and is kept.

<!-- sdlc:auto:start how-it-deploys -->
Pushes to `main` run `.github/workflows/deploy.yml`, which builds the API image (if there is a backend) and deploys the SPA to AWS Amplify. Commits touching only `docs/sdlc/**` don't deploy. Deployments can also be started from the platform's Deployment tab.
<!-- sdlc:auto:end how-it-deploys -->

<!-- sdlc:auto:start environments -->
| Name | Service | Runtime | Scaling | Environment |
|---|---|---|---|---|
| Calculator SPA hosting | Amazon S3 + CloudFront | Static React 19 build | CDN edge, scales to public traffic automatically | dev |
| Operational API | AWS App Runner | FastAPI 0.115 on Python (Uvicorn) | Managed autoscaling, min 1 instance | dev |
| PostgreSQL | Amazon RDS for PostgreSQL | PostgreSQL 16 | Single small instance (provisioned, unused) | dev |
<!-- sdlc:auto:end environments -->

<!-- sdlc:auto:start live -->
_Not deployed yet._
<!-- sdlc:auto:end live -->

<!-- sdlc:auto:start topology -->
```mermaid
graph LR
  n_Calculator_SPA_hosting["Calculator SPA hosting<br/>Amazon S3 + CloudFront"]
  n_Operational_API["Operational API<br/>AWS App Runner"]
  n_PostgreSQL["PostgreSQL<br/>Amazon RDS for PostgreSQL"]
  n_Calculator_SPA_hosting -->|"HTTPS"| n_Operational_API
  n_Operational_API -->|"TCP/TLS"| n_PostgreSQL
```
<!-- sdlc:auto:end topology -->
