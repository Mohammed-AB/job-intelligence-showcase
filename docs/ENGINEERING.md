# Job Intelligence: engineering notes

A job result is only as useful as its source and freshness. Job Intelligence preserves where compensation and eligibility statements came from, including what remains unknown.

## System path

~~~mermaid
flowchart LR
  ConfiguredBoards --> BoundedFetch
  BoundedFetch --> RawSnapshot
  RawSnapshot --> NormalizedPosting
  NormalizedPosting --> EvidenceAndFreshness
  EvidenceAndFreshness --> WebAndMCP
~~~

This diagram describes the demonstrated system boundary, not a production deployment topology.

## Decisions and tradeoffs

### Keep evidence beside normalized fields

Raw snapshots and observations accompany normalized postings. Published pay and inferred or missing units are kept distinct.

### Separate absence from a failed fetch

A provider outage produces an unverifiable observation rather than silently marking a role removed.

### Expose one service through UI and MCP

Search, detail and verification share the same services across the web application and a local MCP interface.

## Review questions

- What evidence demonstrates **keep evidence beside normalized fields**, and what would fail without it?
- What evidence demonstrates **separate absence from a failed fetch**, and what would fail without it?
- What evidence demonstrates **expose one service through ui and mcp**, and what would fail without it?

## Verification boundary

19 database regressions and five browser checks passed in the current verification pass. The fixture collection covers 30 configured boards across three provider formats. The walkthrough shows search, compensation evidence and source freshness.

The showcased search results are fixtures, not current job recommendations. Coverage is limited to configured boards. No applications are submitted and no inbox is read.
