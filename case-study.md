# Case Study

## Challenge

The engagement required a workflow that could accept a stock-analysis request from a web interface, gather relevant external market context, run AI-assisted analysis and return a response in a format suitable for frontend display.

The main engineering challenge was not simply calling an LLM. The workflow had to coordinate input validation, symbol handling, multiple external APIs, chart context, several analysis stages and deterministic response formatting while keeping credentials outside the exported source artifact.

## Solution

OSYSTIC structured the system around a webhook-driven n8n workflow.

The workflow:

1. receives a symbol and analysis interval;
2. validates and normalizes the request;
3. maps symbols to exchange-aware identifiers where needed;
4. retrieves market statistics and company/profile context;
5. obtains chart context from an external chart service;
6. runs AI-assisted technical and fundamental analysis;
7. extracts practical analysis values such as trend and support/resistance context;
8. formats the result for the calling application;
9. returns the response through the webhook response path.

## Engineering decisions

### n8n as the orchestration layer

n8n provided a visual and operationally flexible way to connect webhooks, API calls, code steps, AI nodes and response handling without turning the integration layer into a monolithic custom service.

### Separate AI stages

The implementation uses multiple AI stages instead of one oversized prompt. This keeps responsibilities clearer between raw analysis, summarization and presentation-oriented output.

### Runtime credential binding

Credentials belong in the n8n credential store and deployment environment. The canonical repository intentionally removes credential bindings and keeps the stored workflow inactive by default until operators configure the runtime.

### Portable deployment

The canonical private repository includes a pinned n8n runtime and Docker-oriented setup so deployment is reproducible without committing environment secrets.

## Repository hardening

During governance review, OSYSTIC identified that the legacy repository had previously contained operational environment values and an inline bearer credential.

Rather than carry contaminated history into the maintained canonical repository, the project was rebuilt as a clean private canonical snapshot. The public case study was created with an entirely independent history and contains no workflow source or credential material.

The affected historical provider credential must be rotated before production reuse.

## Outcome

The result is a reusable orchestration pattern for AI-assisted market-analysis workflows with clear boundaries between:

- request handling;
- external data acquisition;
- AI reasoning;
- presentation formatting;
- runtime credentials;
- public portfolio material.

The retained system is an analysis automation, not an automated brokerage execution engine and not a profitability claim.
