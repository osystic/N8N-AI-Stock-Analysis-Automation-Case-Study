# Technical Overview

## Components

- Webhook trigger for inbound analysis requests.
- Validation and normalization code nodes.
- External market/profile HTTP requests.
- Chart-context HTTP request.
- OpenAI-compatible language-model nodes.
- AI agent / chain stages.
- Data extraction and formatting code.
- Symbol-scoped memory.
- Webhook response node.

## Data flow

Input symbol and interval
  → validation
  → normalized market identifier
  → external market/profile data
  → chart context
  → AI analysis
  → technical value extraction
  → formatted response

## Operational boundary

The workflow is stored inactive in the canonical repository. Operators import it into n8n, bind runtime credentials, verify endpoint behavior and rate limits, perform an end-to-end test, and only then activate it.

## Security boundary

No provider token, API key, password or n8n credential export is part of the public case study. The private canonical repository also excludes credential bindings from the checked-in workflow.
