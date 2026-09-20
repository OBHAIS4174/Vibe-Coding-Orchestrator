# Implementation Depth Calibration Matrix

When asking the user *"How deep should this implementation be?"*, present this exact calibration rubric to eliminate high-level / naive agent implementations:

| Depth Level | Target Use Case | Testing Rigor | Error Handling & Boundaries | Architecture & Persistence |
| :--- | :--- | :--- | :--- | :--- |
| **Level 1: Vibe Check (Throwaway Prototype)** | Validating UI/UX flow, mental model, or customer pitch | None / manual sanity check only | Minimal, happy path only | In-memory mocks, hardcoded state, temporary components |
| **Level 2: Standard Feature (MVP)** | Non-critical internal tools, exploratory features | Unit tests covering happy path + 1-2 edge cases | Standard HTTP error responses, simple try/catch | Direct DB schema migrations, basic relations, standard ORM calls |
| **Level 3: Production Robust (Default Recommended)** | User-facing production features, data-modifying flows | Strict TDD (Red-Green-Refactor) at public interface seams, negative authorization tests | Sanitized business-friendly messages, zero raw stack traces, error boundaries | Confirm-Before-Swap, collision-proof sequences (`max + 1`), append-only history, tenant isolation |
| **Level 4: Mission-Critical Enterprise** | High-throughput, financial, authentication, multi-tenant | 100% seam coverage, chaos/failure simulation tests, regression suites | Granular RFC 7807 problem details, circuit breakers, idempotency keys | Zero-downtime DB migrations, dual-read/dual-write verification, distributed tracing, N+1 query elimination |

### Prompting the User During Phase 0:
```text
🎯 Implementation Depth Calibration:
Before building the specification, please specify the required depth:
1. Level 1 - Throwaway Prototype (Fast vibe check, throwaway code)
2. Level 2 - MVP (Functional, basic unit tests)
3. Level 3 - Production Robust [Recommended] (Strict TDD, immutable invariants, sanitized errors)
4. Level 4 - Mission-Critical Enterprise (Zero-downtime migrations, strict RBAC, N+1 profiling, full verification)
```
