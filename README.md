# Enterprise RAG Knowledge

Reusable enterprise knowledge and workflow execution economics.

## Live tools

- **[Context Amplification & Agent Cost Calculator](https://sheikhn.github.io/enterprise-rag-knowldge/calculators/context-amplification.html)** — interactive comparison of a repeated high-context LLM agent session against a reuse-first RAG/MCP workflow approach.
- **[Project homepage](https://sheikhn.github.io/enterprise-rag-knowldge/)**

> GitHub Pages must be enabled for branch **main**, folder **/(root)** before the links become live.

## Repository structure

```text
index.html
calculators/
  context-amplification.html
docs/
  architecture.md
README.md
```

## Calculator methodology

- Agent inference cost/request: **calls × (average input tokens × blended input rate + average output tokens × output rate)**.
- Blended input rate accounts for the selected share of cache-discounted input tokens.
- Reuse-first comparison: gateway cost for all requests + deterministic execution for known-workflow cache misses + optional LLM summarization for known-workflow requests + agent cost for novel requests + fixed monthly platform cost.
- Cache hit rate applies to **known requests**, not to all requests.
- The tool assumes authorization, cache freshness, and workflow suitability checks succeed. Those checks must be enforced in an actual system.
- Browser-only static HTML; no tracking, no dependencies, and no enterprise information is transmitted to a backend. Share URLs contain entered scenario parameters.
- Prices are user-controlled **illustrative assumptions**, not verified live vendor rates.

## GitHub Pages

In **Settings → Pages**, set **Build and deployment → Deploy from a branch → main → /(root)**. Save the settings.

## Scope

Educational cost-modeling demonstration, not a production estimator. Real provider billing can vary with cached token thresholds, cache write fees, context size, rate tiers, tool costs, retries, and orchestration latency.
