---
name: vibe-coding-orchestrator
description: >-
  Use this skill whenever building or refactoring features, designing full-stack systems, or when the user wants to "vibe code" with enterprise-grade quality. Coordinates the complete 8-phase Vibe & Verify engineering lifecycle: Socratic discovery grilling, depth calibration, architectural invariants, strict test-first (TDD) discipline, deep module boundaries, independent two-axis code review, and zero-regression verification. Activate this skill even if the user does not explicitly mention "TDD" or "orchestrator", but requests end-to-end feature development, robust implementation, or architectural oversight. Do not activate for trivial one-off questions or typo fixes.
metadata:
  model: inherit
---

# 🚀 Vibe Coding Orchestrator ("Vibe & Verify")

The **Vibe Coding Orchestrator** is an end-to-end multi-agent engineering workflow. It is designed to solve the primary failure mode of AI coding: **agents generating shallow, naive, unverified boilerplate that fails under real-world conditions.**

### Role Division
* **The Human acts as Creative Director ("Vibing"):** Provides high-level intent, user stories, domain priorities, and UX preferences.
* **The Agent acts as a Full Engineering Department ("Verifying"):** Relentlessly interviews the user via a design tree, calibrates implementation depth, locks down database migrations, models zero-trust security, enforces strict Test-Driven Development (TDD) at deep module seams, dispatches adversarial reviewer subagents, and runs multi-tier performance profiling.

---

## 📋 Master Execution Checklist

When this workflow triggers, instantiate this checklist in your conversation to track progress and prevent skipping steps:

```markdown
- [ ] Phase 0: Discovery Grilling & Depth Calibration
- [ ] Phase 1: Architectural Invariants & Security Boundaries
- [ ] Phase 2: Atomic Task Graph Compilation (`implementation_plan.md`)
- [ ] Phase 3: (Optional) Throwaway Prototype & UX Vibe Approval
- [ ] Phase 4: Test-First (TDD) Seam Verification (Red: confirmed failure)
- [ ] Phase 5: Implement Minimal Code (Green) & SOLID Deep Module Refactoring
- [ ] Phase 6: Independent Two-Axis Code Review (Spec & Security grading)
- [ ] Phase 7: Multi-Tier Verification & Performance / N+1 Profiling
- [ ] Phase 8: Non-Technical Polish, Error Sanitization & Release Walkthrough
```

---

## ⚠️ Gotchas & Critical Failure Modes to Avoid

These non-obvious traps violate the workflow contract:

1. **Never skip Phase 0 depth calibration.** Agents default to high-level mocks unless forced to ask: *"How deep should this implementation be?"*
2. **Never write production code before observing a test fail.** Writing the test and code simultaneously or assuming a test passes is a direct violation of Phase 4. You must execute the test runner and verify the failure reason.
3. **Never mutate live database records in-place.** Always apply Confirm-Before-Swap: Stage → verify reindex/storage → swap live atomically.
4. **Never leak internal error codes to users.** Raw database errors (`E11000`, `23505`) and stack traces must be sanitized into friendly, actionable guidance.
5. **Never self-approve code changes.** Phase 6 requires an independent, read-only subagent evaluating the git diff against invariants and OWASP standards.
6. **Non-interactive shells only.** Subagents cannot respond to interactive TTY prompts. Scripts and tests must accept all flags upfront and never hang waiting on stdin.

---

## 🔄 The 8-Phase Engineering Lifecycle

### Phase 0: Discovery, Grilling & Depth Calibration
1. **Socratic Grilling (`skills/grilling`)**:
   * Map the request as a **design tree** where every decision branches into dependent choices.
   * Ask the frontier in structured rounds:
     ```text
     ❓ Q1 - <Question Title>: <Detailed context and multiple choices>
     ➡️ Recommended Answer: <Your recommendation>
     ```
   * Never ask the user for facts you can inspect in the codebase or git history.
2. **Live Domain Modeling (`skills/domain-modeling`)**:
   * Police vocabulary. Clarify ambiguous terms immediately and update `CONTEXT.md`.
   * For hard-to-reverse trade-offs, record an Architecture Decision Record in `docs/adr/`.
3. **Depth Calibration**:
   * *When to load:* Read [`references/depth-calibration-matrix.md`](references/depth-calibration-matrix.md) to present the 4-level rubric:
     * **Level 1: Vibe Check (Throwaway Prototype)** — UI flow and UX validation only.
     * **Level 2: Standard MVP** — Basic feature set with primary unit tests.
     * **Level 3: Production Robust [Default Recommended]** — Strict TDD, immutable invariants, sanitized errors.
     * **Level 4: Mission-Critical Enterprise** — Zero-downtime DB migrations, distributed tracing, N+1 profiling.

---

### Phase 1: Architectural Invariants & Security Boundaries
Before writing implementation files, establish non-negotiable architectural constraints:
1. **Core Data Invariants (`skills/spec-driven-agentic-workflow`)**:
   * *Confirm-Before-Swap*: Live serving state is never mutated in-place.
   * *State Isolation*: Decouple pending drafts from published records (`hasPendingVersion` decoupled from `isPublish`).
   * *Collision-Proof Sequences*: Derive counters from database history (`max(existing) + 1`), never optimistic increments.
   * *Append-Only History*: Edits and rollbacks create new version rows (`source: 'rollback'`).
2. **Database & Migrations (`skills/database-architect`, `skills/database-migration`)**:
   * Plan zero-downtime migrations (Expand → Contract → Cleanup). Validate index strategies.
3. **Zero-Trust Security (`skills/security-auditor`)**:
   * Enforce tenant isolation directly in query filters (`{ tenantId, ... }`), never in memory. Validate RBAC boundaries.
4. **API Contracts (`skills/api-design-principles`)**:
   * Enforce idempotency keys on mutations and standardized RFC 7807 error envelopes.

---

### Phase 2: Atomic Task Graph Compilation
* *When to load:* Read [`references/spec-plan-template.md`](references/spec-plan-template.md) to compile `implementation_plan.md`.
* Decompose the feature into ordered, decoupled tasks (Task 1 to Task N).
* Each task declares: Goal & Seam, Target Invariants, Explicit Files, and Automated Test Command.

---

### Phase 3: Throwaway Prototyping (Optional)
* *When to trigger:* Activate only if the user request is ambiguous, visual, or UI-heavy.
* Use `skills/prototype` and `skills/ui-ux-designer` to build a fast, throwaway component.
* Let the user interact with it to calibrate the "vibe".
* **The Golden Rule:** Once the vibe is approved, **throw the throwaway code away** and proceed to Phase 4 for real, test-first development.

---

### Phase 4: Test-First (TDD) Discipline
**Never write production code without an observed, failing test first.**
1. **Locate the Seam (`skills/codebase-design`)**: Position tests at the public interface seam, not private helpers.
2. **Author the Test (Red)**: Cover happy path, negative boundaries (unauthorized, cross-tenant), and edge cases.
3. **Validation Gate**: Run the test runner. Confirm failure for the *expected* reason before writing production code.

---

### Phase 5: Implement Minimal Code & SOLID Refactoring
1. **Task Brief Dispatch**:
   * *When to load:* Read [`references/task-brief-template.md`](references/task-brief-template.md) to dispatch implementer subagents with explicit context and constraints.
2. **Make Tests Pass (Green)**: Write only the minimal code required to satisfy the failing test.
3. **Refactor into Deep Modules (`skills/code-refactoring-refactor-clean`, `skills/codebase-design`)**:
   * Enforce small interfaces hiding high-leverage logic. Apply SOLID principles. Accept dependencies; avoid hidden side effects.

---

### Phase 6: Independent Two-Axis Code Review
**Never self-approve without independent verification.**
1. Generate the git diff: `git diff <base-commit>..<head-commit> > review-task-N.diff`.
2. *When to load:* Read [`references/reviewer-prompt-template.md`](references/reviewer-prompt-template.md) and dispatch a read-only subagent.
   * **Axis 1: Spec Compliance**: Did the implementer uphold every mandatory invariant?
   * **Axis 2: Code Quality & Security (`skills/security-auditor`)**: Check for OWASP Top 10 vulnerabilities, N+1 queries, and test rigor.
3. **Validation Gate**: All `Critical` or `Important` findings must be resolved before proceeding.

---

### Phase 7: Multi-Tier Verification & Performance Profiling
1. **Full Test Suites**: Run `npm test` or `pytest`. Zero failures tolerated.
2. **Production Build**: Execute bundler (`npm run build` or `tsc --noEmit`) to verify zero type or import errors.
3. **Performance Audit (`skills/application-performance-performance-optimization`, `skills/database-optimizer`)**:
   * Audit query counts in loops; enforce batching or eager loading to eliminate N+1 cascades.
4. **DevOps Diagnostics (`skills/devops-troubleshooter`)**: Verify error logging and distributed tracing instrumentation.

---

### Phase 8: Non-Technical Polish & Empathy Release
1. **Sanitize Internal Errors**: Convert technical database codes (`E11000`, `23505`) and stack traces into friendly, actionable messages (e.g. *"This item already exists in your workspace"*).
2. **Eliminate Cognitive Clutter**: Automatically hide empty tables and fields rather than rendering `"N/A"` or blank boxes. Replace raw date pickers with 1-click presets.
3. **Walkthrough**: Record architecture diagrams and verification proofs in `walkthrough.md`. Commit with clean conventional commits (`feat: ...`, `fix: ...`).

---

## 📚 Bundled Reference Artifacts
* [`references/depth-calibration-matrix.md`](references/depth-calibration-matrix.md) — 4-level depth calibration rubric (Load in Phase 0)
* [`references/spec-plan-template.md`](references/spec-plan-template.md) — Spec & task graph template (Load in Phase 2)
* [`references/task-brief-template.md`](references/task-brief-template.md) — Subagent task brief template (Load in Phase 5)
* [`references/reviewer-prompt-template.md`](references/reviewer-prompt-template.md) — Two-axis code review prompt (Load in Phase 6)
