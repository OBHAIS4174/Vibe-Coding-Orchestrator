---
name: vibe-coding-orchestrator
description: The ultimate "Vibe & Verify" engineering orchestrator. Bridges natural language intent ("vibing") with industrial software engineering rigor. Coordinates discovery grilling, domain modeling, architectural invariants, deep module seams, strict TDD, two-axis code review, and zero-regression DevOps verification.
metadata:
  model: inherit
---

# 🚀 Vibe Coding Orchestrator ("Vibe & Verify")

The **Vibe Coding Orchestrator** is an end-to-end multi-agent engineering workflow. It is designed to solve the fatal flaw of modern AI coding: **agents generating shallow, naive, unverified boilerplate that breaks under real-world conditions.**

This orchestrator establishes a clean separation of roles:
* **The Human acts as the Creative Director ("Vibing"):** Provides high-level intent, user stories, product priorities, and UX preferences.
* **The Agent acts as a Full Engineering Department ("Verifying"):** Relentlessly stress-tests the requirements, enforces database integrity and zero-trust security, designs deep module seams, authors strict failing tests before writing code (TDD), dispatches independent code reviewers, and profiles production performance.

---

## 🔄 The Complete "Vibe & Verify" Lifecycle

```
┌──────────────────────────────────────┐
│  Phase 0: Discovery, Grilling & Depth│  Grill the user via design tree; calibrate implementation depth
└──────────────────┬───────────────────┘
                   ▼
┌──────────────────────────────────────┐
│  Phase 1: Architecture & Invariants  │  Lock DB migrations, RBAC threat models, REST/GraphQL seams
└──────────────────┬───────────────────┘
                   ▼
┌──────────────────────────────────────┐
│  Phase 2: Atomic Task Graph          │  Decompose into ordered, decoupled, testable task briefs
└──────────────────┬───────────────────┘
                   ▼
┌──────────────────────────────────────┐
│  Phase 3: Throwaway Prototype        │  (Optional) Fast UI/UX vibe check; trash the prototype once approved
└──────────────────┬───────────────────┘
                   ▼
┌──────────────────────────────────────┐
│  Phase 4: Test-First (TDD) Discipline│  Author failing tests at public interface seams (Red)
└──────────────────┬───────────────────┘
                   ▼
┌──────────────────────────────────────┐
│  Phase 5: Implement & SOLID Refactor │  Implement minimal code (Green); refactor into Deep Modules
└──────────────────┬───────────────────┘
                   ▼
┌──────────────────────────────────────┐
│  Phase 6: Independent Two-Axis Review│  Dispatch read-only subagents to grade Spec & Security (OWASP)
└──────────────────┬───────────────────┘
                   ▼
┌──────────────────────────────────────┐
│  Phase 7: Performance & Multi-Tier QA│  Full regression suites, build validation, N+1 query elimination
└──────────────────┬───────────────────┘
                   ▼
┌──────────────────────────────────────┐
│  Phase 8: Empathy Polish & Release   │  Sanitize technical errors, hide empty UI states, generate walkthrough
└──────────────────────────────────────┘
```

---

## Phase 0: Discovery, Grilling & Depth Calibration

Before proposing architecture or touching code, the agent actively interrogates the user's intent to eliminate ambiguity:

### 1. Relentless Interviewing (The `grilling` Discipline)
* Map the user's request as a **design tree** where each decision branches into dependent choices.
* Identify the **frontier**: questions that can be asked *now* without guessing.
* Ask questions in structured rounds:
  ```text
  ❓ Q1 - <Question Title>: <Detailed context and multiple choices>
  ➡️ Recommended Answer: <Your recommendation>
  ---
  ❓ Q2 - <Question Title>: <Detailed context and multiple choices>
  ➡️ Recommended Answer: <Your recommendation>
  ```
* Never ask the user for facts you can inspect in the codebase or git history; research facts autonomously.

### 2. Live Domain Modeling (`domain-modeling`)
* Actively police vocabulary. If the user says "account", clarify whether they mean `Tenant`, `Organization`, or `User`.
* Immediately record agreed terms in `CONTEXT.md`.
* Flag hard-to-reverse architectural decisions and generate an Architecture Decision Record in `docs/adr/`.

### 3. Implementation Depth Calibration
Agents frequently default to shallow prototypes. Force an explicit calibration using `references/depth-calibration-matrix.md`:
* **Level 1: Vibe Check (Throwaway Prototype)** — UI flow and user experience testing only.
* **Level 2: Standard Feature (MVP)** — Happy path + basic unit tests.
* **Level 3: Production Robust [Default]** — Strict TDD, immutable invariants, sanitized errors.
* **Level 4: Mission-Critical Enterprise** — Zero-downtime DB migrations, strict RBAC, N+1 profiling, full regression verification.

---

## Phase 1: Architectural Invariants & System Security

Before writing implementation files, establish non-negotiable architectural boundaries:

### 1. Core Data Invariants
* **Confirm-Before-Swap**: Never mutate live serving records in-place. Stage → confirm index/storage success → promote to live → retire old state.
* **State Isolation**: Decouple pending drafts from published records (e.g. `hasPendingVersion` independent of `isPublish`).
* **Collision-Proof State**: Sequence counters must derive from database history (`max(existing) + 1`), never optimistic increments.
* **Append-Only History**: Rollbacks and updates create new version snapshots (`source: 'rollback'`); never mutate or delete audit history.

### 2. Data Layer Architecture (`database-architect` & `database-migration`)
* Enforce foreign key constraints, composite indexes for high-frequency queries, and transaction boundaries.
* Plan **zero-downtime migrations**:
  * Expand phase: Add nullable columns or new tables.
  * Contract phase: Backfill data and switch application reads/writes.
  * Cleanup phase: Drop obsolete columns in a subsequent release.

### 3. Threat Modeling & RBAC (`security-auditor`)
* Apply zero-trust at the data layer: enforce tenant boundaries directly in query filters (`{ tenantId, ... }`), never in memory.
* Validate all inputs against strict schemas before processing. Gating permissions by role (agents blocked from admin approvals/deletions).

### 4. API Design Standards (`api-design-principles`)
* Design deep interfaces: idempotency keys for mutations, cursor-based pagination for collections, and standard HTTP/RFC-7807 error envelopes.

---

## Phase 2: Atomic Task Graph Decomposition

Compile the findings into an executable task graph:

1. Produce `implementation_plan.md` using `references/spec-plan-template.md`.
2. Break the feature into strictly ordered, decoupled tasks (Task 1 to Task N).
3. Every task must declare:
   * **Goal & Seam**: What public interface is exposed.
   * **Target Invariants**: Which invariants bind this task.
   * **Explicit Files**: Exact file paths to modify or create.
   * **Verification Command**: Automated test command.

---

## Phase 3: Throwaway Prototyping (Optional)

If the user request is ambiguous, visual, or UI-heavy:
1. Put on the **UX Designer** hat (`ui-ux-designer`, `prototype`).
2. Build a fast, throwaway component using design tokens (`tailwind-design-system`) or interactive mockups.
3. Allow the user to interact with the mockup and calibrate the "vibe".
4. **Crucial Rule**: Once the vibe is approved, **throw the throwaway code away** and proceed to Phase 4 for real, test-first implementation.

---

## Phase 4: Test-First (TDD) Discipline

**Never write production code without an observed, failing test first.**

1. **Locate the Seam (`codebase-design`)**:
   * Position tests at the public interface seam (controller route, public service function).
   * Test across the interface, never against private implementation details.
2. **Author the Test (Red)**:
   * Write tests for the happy path, negative boundaries (unauthorized, cross-tenant), and edge conditions (empty payloads, duplicate keys).
   * Use isolated test fixtures or in-memory databases.
3. **Confirm Failure**:
   * Execute the test runner. Verify the test fails specifically for the expected absence of functionality, not syntax or configuration errors.

---

## Phase 5: Implementer Dispatch & Clean Code Refactoring

1. **Structured Task Brief**:
   * Author `task-N-brief.md` using `references/task-brief-template.md`.
   * Include exact context pointers, global constraints, and verification commands.
2. **Implement Minimum Code (Green)**:
   * Dispatch an implementer subagent via `invoke_subagent`.
   * Write only the code required to satisfy the failing test.
3. **Refactor into Deep Modules (`codebase-design`, `code-refactoring-refactor-clean`)**:
   * Apply SOLID principles.
   * Ensure the module is **Deep**: small, clean interface with a high-leverage implementation.
   * Accept dependencies rather than constructing them internally. Return pure results rather than producing hidden side-effects.

---

## Phase 6: Independent Two-Axis Code Review

**Never self-approve without independent verification.**

1. **Generate the Git Diff**:
   * Produce the clean diff: `git diff <base-commit>..<head-commit> > review-task-N.diff`.
2. **Dispatch Independent Reviewer Subagents (`code-review-ai-ai-review`)**:
   * Dispatch a read-only subagent with `references/reviewer-prompt-template.md`.
   * **Axis 1: Spec & Invariant Compliance**: Did the code violate Confirm-Before-Swap, State Isolation, or RBAC?
   * **Axis 2: Code Quality & Security (`security-auditor`)**: Check for SQL/NoSQL injection, OWASP Top 10 vulnerabilities, resource leaks, and test rigor.
3. **Remediation**:
   * Any `Critical` or `Important` findings must be resolved and re-tested before advancing to the next task.

---

## Phase 7: Performance & Multi-Tier QA

Before declaring the feature complete:

1. **Regression Suites**: Run full backend test suites (`npm test` / `pytest`). Zero failures permitted.
2. **Production Build**: Execute production bundler (`npm run build` / `tsc --noEmit`) to verify zero type errors or broken imports.
3. **Performance & N+1 Audit (`application-performance-performance-optimization`, `database-optimizer`)**:
   * Verify query counts in loops. Enforce batch loading or eager relations to prevent N+1 query cascades.
   * Verify index utilization on new queries.
4. **End-to-End Integration Check**: Test the entire multi-step lifecycle from end to end.

---

## Phase 8: Non-Technical Polish & Empathy Release

Software must delight end users and eliminate developer friction:

1. **Sanitize Internal Errors**:
   * Strip raw stack traces, database codes (`E11000`, `23505`), and low-level denial strings (`"Access denied. Global admin role required"`).
   * Translate into actionable user guidance: *"This item already exists in your workspace."* or *"Permission restricted: contact your workspace administrator."*
2. **Eliminate Cognitive Clutter**:
   * Hide empty fields, empty columns, and empty sections rather than rendering `"N/A"` or blank spaces.
   * Replace raw technical inputs with friendly presets (`All Time`, `Today`, `Last 7 Days`, `Last 30 Days`).
3. **Generate Walkthrough & Commit**:
   * Document all changes, architecture diagrams, and verification proofs in `walkthrough.md`.
   * Commit with clean conventional commits (`feat: ...`, `fix: ...`).

---

## Bundled Sub-Skills & Templates

This orchestrator is powered by the following bundled specialized skills:
* [`grilling`](../grilling/SKILL.md) — Relentless interview & design tree expansion
* [`domain-modeling`](../domain-modeling/SKILL.md) — Active vocabulary policing & ADR generation
* [`spec-driven-agentic-workflow`](../spec-driven-agentic-workflow/SKILL.md) — Spec & invariant framework
* [`database-architect`](../database-architect/SKILL.md) — Relational & NoSQL schema design
* [`database-migration`](../database-migration/SKILL.md) — Zero-downtime migration strategies
* [`database-optimizer`](../database-optimizer/SKILL.md) — Query tuning & index optimization
* [`security-auditor`](../security-auditor/SKILL.md) — Zero-trust, RBAC & OWASP auditing
* [`api-design-principles`](../api-design-principles/SKILL.md) — REST & GraphQL standards
* [`codebase-design`](../codebase-design/SKILL.md) — Deep modules & seam placement
* [`code-refactoring-refactor-clean`](../code-refactoring-refactor-clean/SKILL.md) — SOLID design patterns
* [`code-review-ai-ai-review`](../code-review-ai-ai-review/SKILL.md) — Two-axis independent grading
* [`prototype`](../prototype/SKILL.md) — Throwaway prototyping & feel validation
* [`ui-ux-designer`](../ui-ux-designer/SKILL.md) — Accessible UI & design systems
* [`application-performance-performance-optimization`](../application-performance-performance-optimization/SKILL.md) — End-to-end profiling & N+1 resolution
* [`devops-troubleshooter`](../devops-troubleshooter/SKILL.md) — Distributed diagnostics & verification

### Templates
* [`references/task-brief-template.md`](references/task-brief-template.md) — Standard subagent brief
* [`references/spec-plan-template.md`](references/spec-plan-template.md) — Implementation plan & invariants
* [`references/reviewer-prompt-template.md`](references/reviewer-prompt-template.md) — Two-axis code reviewer prompt
* [`references/depth-calibration-matrix.md`](references/depth-calibration-matrix.md) — Depth calibration rubric
