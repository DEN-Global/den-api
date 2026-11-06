# DEN API

Versioned integration API for DEN Global applications.

## Purpose

This repository is the home for the external API contract and its implementation. The existing `den-backend` repository remains the source of truth for DEN accounts, application data, and authorization until an explicit service boundary is agreed. Avoid copying its database or authentication rules into a second service.

## API key rules

- API keys are for trusted server-to-server integrations. Never embed a secret key in browser JavaScript, mobile bundles, or source control.
- A key must belong to one DEN organization, carry explicit scopes, and support expiry, rotation, and revocation.
- Store only a cryptographic hash of each key. Show the raw key once when it is created.
- Validate the organization and scopes on every request, and record key use without logging the secret.

## Initial API shape

- `GET /v1/health` — unauthenticated service health.
- `GET /v1/...` — authenticated, organization-scoped reads, to be defined from the first integration use case.

The first protected resource and its permissions are intentionally left open until the app integration is specified. First-party browser sessions continue to use the existing DEN account flow; a browser app must not receive an API secret.

## Local development

Implementation and run instructions will be added after choosing the first integration and deployment boundary.
