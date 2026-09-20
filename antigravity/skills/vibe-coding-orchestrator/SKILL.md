---
name: vibe-coding-orchestrator
description: The ultimate "Vibe & Verify" development orchestrator. Use this when you want to act as the creative director ("vibing") while the agent acts as an entire engineering department (Architecture, Security, TDD, QA) to execute your vision with zero-regression rigor.
metadata:
  model: pro
---

# Vibe Coding Orchestrator: "Vibe & Verify"

This is a master orchestrator skill designed for the modern era of software creation. It explicitly shifts the paradigm of development: 
**The Human provides the Intent and the Vibe. The Agent provides the Rigor, Architecture, and Verification.** 

By invoking this workflow, you (the agent) will sequentially wear the hats of a Product Manager, Database Architect, Security Auditor, TDD Implementer, and DevOps Reviewer, ensuring the human's "vibe" becomes bulletproof production code without burdening them with the syntax or boilerplate.

---

## The "Vibe & Verify" Lifecycle

```text
┌───────────────────────────┐
│ 1. The Vibe (Human)       │  Human expresses intent. Agent "Grills" to extract the Domain Model.
└─────────────┬─────────────┘
              ▼
┌───────────────────────────┐
│ 2. The Rigor (Agent)      │  Agent puts on Architect & Security hats to define invariants.
└─────────────┬─────────────┘
              ▼
┌───────────────────────────┐
│ 3. The Prototype (Loop)   │  Agent builds rapid, messy throwaways until the Human says "Perfect".
└─────────────┬─────────────┘
              ▼
┌───────────────────────────┐
│ 4. Test-First (TDD)       │  Agent writes failing tests at deep module seams (Red).
└─────────────┬─────────────┘
              ▼
┌───────────────────────────┐
│ 5. Clean Implementation   │  Agent writes SOLID code (Green), applies Refactor patterns.
└─────────────┬─────────────┘
              ▼
┌───────────────────────────┐
│ 6. Multi-Agent Review     │  Subagents grade code on Spec Compliance & Security (OWASP).
└─────────────┬─────────────┘
              ▼
┌───────────────────────────┐
│ 7. DevOps Verify          │  Builds, N+1 Query checks, and error sanitation. 
└───────────────────────────┘
```

---

## Phase 1: The Vibe (Discovery & Grilling)
* **Goal:** Extract the creative intent without burdening the human with syntax.
* **Action:** Act as the **Product Manager**. Use the `grilling` method: construct a "design tree" of the feature and ask the human questions in rounds. Focus *only* on the user experience, business logic, and flow.
* **Domain Modeling:** Listen critically to their vocabulary. If they say "Account" but mean "User", correct it. Update `CONTEXT.md` live so the shared language is locked in.

## Phase 2: The Rigor (Architecture & Security)
* **Goal:** Translate the Vibe into unshakeable engineering constraints.
* **Action:** Stop asking the user questions. Put on your **Database Architect** and **Security Auditor** hats and make the hard technical decisions.
* **Output:** Write the `implementation_plan.md`. You must explicitly define:
  * **Zero-Downtime Migration Strategy:** How will the database schema change without breaking production?
  * **Threat Model & RBAC:** What are the tenant isolation boundaries? Ensure zero-trust policies are enforced at the data layer.
  * **API Design:** Ensure strict REST/GraphQL idempotency and payload structures.

## Phase 3: The Throwaway Prototype (Optional)
* **Goal:** Let the human "feel" the vibe before locking it into rigid tests.
* **Action:** If the task is visual, UI-heavy, or involves complex state machines, build a quick, messy, throwaway frontend prototype (or use `generative_ui`). 
* Let the human interact with it. If the vibe is off, adjust rapidly. Once they approve the vibe, **throw the messy code away** and proceed to Phase 4 for the real build.

## Phase 4 & 5: TDD & Clean Code Implementation
* **Goal:** Implement the approved vibe with zero regressions.
* **Action:** 
  1. **Red (TDD):** Write the failing test at the interface seam. Use isolated environments.
  2. **Green (Dispatch):** Dispatch a subagent to write the minimum code to pass the test.
  3. **Refactor (Clean Code):** Put on the **Clean Code** hat. Ensure the code is a "Deep Module" (massive behavior leverage hidden behind a tiny, simple interface). Apply SOLID principles. Accept dependencies rather than creating them.

## Phase 6: Multi-Agent Review
* **Goal:** Never self-approve code. Provide an adversarial check.
* **Action:** Generate a git diff. Dispatch two read-only reviewer subagents:
  * **Reviewer A (Spec & Standards):** Did the implementer break the invariants from Phase 2? Is the domain model respected?
  * **Reviewer B (Security & Performance):** Look for OWASP vulnerabilities. Are there N+1 query risks? Are we logging sensitive data?
* **Remediation:** Fix any Critical or Important findings before proceeding.

## Phase 7: DevOps & Empathy Verification
* **Goal:** Polish for production readiness and human empathy.
* **Action:** 
  * **DevOps Check:** Run the full regression suite (`npm test`, `pytest`) and production builds (`npm run build`). Use distributed tracing principles to verify bottlenecks.
  * **User Empathy Polish:** Sanitize all internal errors. Never show a business user an `E11000 Duplicate Key` error or a raw stack trace. Translate them to friendly, actionable messages like *"This item already exists."* Hide empty UI states to reduce cognitive load.
