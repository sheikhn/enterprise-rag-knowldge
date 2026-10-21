# Architecture: Reuse Before Reason

## Problem

General-purpose agent harnesses may repeatedly rediscover known enterprise workflows through multi-call large-context reasoning. They offer flexibility for unfamiliar tasks, but familiar operational tasks can be more cost-effective as approved reusable workflows.

## Logical flow

```text
User / Agent / Application
         |
Intent + Identity + Policy Gateway
         |
Validated Knowledge / Capability Registry (RAG discovery)
         |
   Authorized Result Cache ---- valid hit --> Verified Result
         |
       Miss
         |
Versioned Workflow Engine --> MCP / Enterprise APIs
         |
Validation, provenance, cache publication
         |
Verified Result --> Optional compact LLM summarization
```

Unfamiliar tasks branch to an adaptive reasoning agent, which may propose a new plan. Promotion of proposed workflows should require enterprise approval and lifecycle validation.

## Security and correctness requirements

1. Authenticate and authorize on every request, including cache hits.
2. Include tenant, authorization scope, resolved time windows, environment, workflow versions and source versions in cache identity.
3. Use TTL **and** event/version invalidation. Historical and live requests need different freshness contracts.
4. Enforce read-only or write authorization, idempotency and approval on execution.
5. Validate workflow tool contracts and structured outputs, and record execution provenance.
6. Never execute code copied from retrieved documentation without sandboxing and review.
7. Monitor misrouting, stale cache responses, p95 latency and cost per correct authorized result.

## Evaluation

Compare agent-only, deterministic-first without cache, and deterministic-first with cache across matched workloads. Measure cost per successful request, agent calls, tokens, cache hit rate, routing accuracy, freshness, latency and capability lifecycle cost.
