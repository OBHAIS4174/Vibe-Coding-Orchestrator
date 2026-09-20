---
name: spec-driven-agentic-workflow
description: End-to-end spec-driven development workflow with test-first (TDD) rigor, atomic task planning, subagent implementer dispatch, independent two-axis code review, and multi-tier verification. Use when planning and executing complex features, refactors, or multi-step engineering tasks requiring strict invariants, TDD, and agent delegation.
---

# Spec-Driven Agentic Workflow

An industrial-strength engineering workflow combining deep architectural specification, test-first (TDD) rigor, atomic task graph decomposition, subagent delegation, independent two-axis review, and empathetic non-technical polish.

---

## 1. The Core Lifecycle Loop

```
┌───────────────────────────┐
│ 0. Discovery & Depth      │  Interrogate the user request and align on implementation depth
└─────────────┬─────────────┘
              ▼
┌───────────────────────────┐
│ 1. Spec & Invariants      │  Define domain invariants, state machines, and boundaries
└─────────────┬─────────────┘
              ▼
┌───────────────────────────┐
│ 2. Atomic Task Graph      │  Decompose into ordered, bounded, decoupled tasks
└─────────────┬─────────────┘
              ▼
┌───────────────────────────┐
│ 3. Task Brief Creation    │  Context pointers, explicit files, constraints, deliverables
└─────────────┬─────────────┘
              ▼
┌───────────────────────────┐
│ 4. Test-First (TDD)       │  Author failing tests at seams before production code (Red)
└─────────────┬─────────────┘
              ▼
┌───────────────────────────┐
│ 5. Implementer Dispatch   │  Implement minimal robust code to pass tests (Green)
└─────────────┬─────────────┘
              ▼
┌───────────────────────────┐
│ 6. Independent Review     │  Dispatch read-only subagent to grade Spec & Standards
└─────────────┬─────────────┘
              ▼
┌───────────────────────────┐
│ 7. Multi-Tier Verify      │  Full regression suites, build checks, and end-to-end pass
└─────────────┬─────────────┘
              ▼
┌───────────────────────────┐
│ 8. Polish & Walkthrough   │  Sanitize errors for non-technical users, clean commit
└───────────────────────────┘
```

---

## Phase 0: Request Discovery & Depth Calibration

Before writing any specification, you must thoroughly interrogate the user's initial request to remove ambiguity and calibrate expectations:

1. **Ask Detailed Questions**: 
   - Proactively ask clarifying questions about every aspect of the feature or request. Do not make assumptions about the user's intent.
   - Investigate edge cases, user roles, data sources, UI/UX behavior, and integration points.
2. **Align on Implementation Depth**:
   - Explicitly ask the user: *"How deep should this implementation be?"*
   - AI agents are known to default to high-level or naive implementations. Force a conversation about whether this requires a production-ready, highly robust implementation, or a quick-and-dirty prototype. 
   - Establish the level of testing, error handling, and architectural rigor required.

---

## Phase 1: Architectural Specification & System Invariants

Before modifying any source code, establish immutable system boundaries and invariants:

1. **Identify Critical Invariants**:
   - *Confirm-Before-Swap*: Never mutate live serving records in-place. Stage → confirm index/storage success → promote to live → retire old state.
   - *State Isolation*: Decouple pending edits from live content (e.g. `hasPendingVersion` independent of `isPublish`/`status`).
   - *Collision-Proof State*: Always derive counters/sequences from database history (`max(existing) + 1`), never optimistic increments. Reuse existing pending snapshots on secondary edits.
   - *Append-Only History*: Rollbacks and edits always create *new* version rows (`source: 'rollback'`); never mutate or delete historical records.
   - *Citation & Audit Pinning*: Pinned references (e.g. LLM citations) must link to immutable revision IDs, never mutable head records.
   - *Multi-Tenant Isolation & Least Privilege RBAC*: Tenant boundaries strictly enforced at the data layer; permissions gated by role (e.g., agents cannot approve or delete).

2. **Produce the Task Graph (`implementation_plan.md`)**:
   - Break the project into numbered, atomic tasks (Task 1 to Task N).
   - Each task must state:
     - **Goal & Rationale**: What capability is unlocked and why.
     - **Files to Modify / Create**: Explicit file paths.
     - **Target Invariants**: Which system invariants bind this task.
     - **Verification Plan**: Exact test command or script.

---

## Phase 2: Test-First (TDD) Discipline

**Never write production code without a failing test first.**

1. **Identify the Public Seam**:
   - Place tests at public interfaces (API routes, controller entry points, service functions), never coupled to internal private implementation details.
2. **Author the Test First (Red)**:
   - Use isolated test environments (e.g. `mongodb-memory-server`, isolated mock vectors, supertest).
   - Write tests covering:
     - The happy path.
     - Negative/unauthorized boundaries (e.g., cross-tenant 404, agent 403).
     - Edge cases (duplicate version collisions, empty payloads, reindex failures).
3. **Run the Test Suite to Confirm Failure**:
   - Ensure the test fails for the *expected* reason (e.g. function not implemented or returning wrong status), not due to syntax or test harness misconfiguration.
4. **Implement Minimum Production Code (Green)**:
   - Write only the code required to make the failing test pass cleanly.
5. **Run Local & Regression Test Suites**:
   - Run both the targeted test file and the full project regression suite.
   - **Requirement**: 100% pass rate before marking the task complete.

---

## Phase 3: Subagent Implementer Dispatch

When delegating complex tasks to subagents:

1. **Write a Structured Task Brief** (`.superpowers/sdd/task-N-brief.md` or artifact):
   - Provide **Context Pointers** to relevant specs, models, and controllers.
   - Explicitly list **Global Constraints** and invariants that bind the task.
   - Specify the exact deliverables and test commands.
2. **Dispatch the Implementer Subagent**:
   - Use `invoke_subagent` with a concise prompt pointing to the task brief.
   - The subagent focuses entirely on implementation and local test passing.
3. **Capture Output & Artifacts**:
   - The subagent writes a task completion report (`task-N-report.md`) detailing changes made, files touched, and test outputs.

---

## Phase 4: Independent Two-Axis Code Review

**Never self-approve without independent verification.**

1. **Generate the Git Diff**:
   - Generate a clean diff file for the task:
     `git diff <base-commit>..<head-commit> > review-task-N.diff`
2. **Dispatch an Independent Read-Only Reviewer Subagent**:
   - Invoke a fresh subagent with the role `"Task N Reviewer"`.
   - The reviewer evaluates the diff along **two independent axes**:
     - **Axis 1: Spec & Invariant Compliance**: Did the implementer uphold every mandatory invariant (e.g. Confirm-before-swap, state isolation, RBAC)?
     - **Axis 2: Code Quality & Standards**: Are error handlers robust? Are tests non-vacuous and testing true seams? Are comments clean?
3. **Structured Review Rubric**:
   - **Spec Compliance**: `✅ Compliant` or `❌ Issues Found`
   - **Critical (Must Fix)**: Breaking invariant violations or regressions.
   - **Important (Should Fix)**: Missing edge cases, weak assertions.
   - **Minor**: Code cleanliness or documentation nits.
   - **Assessment**: `Approved` or `Needs Fixes`.
4. **Remediation**:
   - Address any Critical or Important findings immediately before proceeding.

---

## Phase 5: Multi-Tier Full System Verification

Before finalizing the feature or releasing to production:

1. **Backend Tests**: Run full test suites (`npm test` / `pytest`). Zero failures tolerated.
2. **Frontend Production Build**: Run `npm run build` (or Vite/Webpack build) to catch TypeScript, JSX, or bundling regressions.
3. **Integration Scenarios**: Verify multi-step lifecycles (e.g. edit draft → pending version created → live remains unchanged → approve → vector reindex → live swapped).
4. **Zero Console & Lint Errors**: Ensure clean browser console and zero unhandled rejections.

---

## Phase 6: Non-Technical Polish & User Empathy

Software must be designed with deep empathy for the end user:

1. **Sanitize Internal Errors**:
   - Never expose raw stack traces, database codes (`E11000`), or internal authorization denials (`"Access denied. Global admin role required"`) to business/tenant users.
   - Rewrite them into friendly, professional, actionable text (e.g., *"Permission restricted: administrator permissions required"*).
2. **Eliminate UI Empty States & Technical Clutter**:
   - If a field, column, or modal section is empty (`null`, `undefined`, or `"N/A"`), **hide it completely** rather than rendering blank rows or empty boxes.
   - Hide technical infrastructure columns (IP addresses, raw endpoints, internal MongoDB IDs) from non-admin views.
   - Merge related fields into intuitive feeds (e.g. combine *Action* + *Item Name* into a clean *Activity & Item* feed).
3. **Simplify Controls for Business Users**:
   - Replace complex raw inputs (e.g. technical `datetime-local` pickers) with 1-click friendly presets (`All Time`, `Today`, `Last 7 Days`, `Last 30 Days`).
   - Group technical database operations into plain-English categories (*Approvals & Restores*, *Edits & Updates*, *Uploads*, *Sign-ins*).
4. **Living Documentation & Atomic Commits**:
   - Maintain a comprehensive `walkthrough.md` artifact detailing all changes, verification results, and architecture diagrams.
   - Stage and commit with clean, conventional commit messages (`feat: ...`, `fix: ...`).

---

## References & Templates

- [`references/task-brief-template.md`](references/task-brief-template.md): Template for authoring implementer task briefs.
- [`references/reviewer-prompt-template.md`](references/reviewer-prompt-template.md): Template for dispatching two-axis reviewer subagents.
- [`references/spec-plan-template.md`](references/spec-plan-template.md): Template for authoring implementation plans and invariant declarations.
