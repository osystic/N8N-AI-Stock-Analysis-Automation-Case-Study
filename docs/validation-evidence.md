# Validation Evidence

The private canonical repository includes automated repository validation that checks:

- the workflow JSON parses successfully;
- the stored workflow is inactive by default;
- the expected webhook trigger exists;
- a webhook response node exists;
- AI model nodes are present;
- credential bindings are not committed;
- inline Authorization headers are not committed;
- common token/key patterns are not present in the workflow artifact.

The canonical workflow validated with 20 nodes and 19 connection groups during the repository hardening pass.

This evidence is structural and security-oriented. It does not certify market accuracy, investment quality, latency, live brokerage execution or financial returns.
