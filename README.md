# ⚡ Vibe-Coding-Orchestrator

**Industrial-grade "Vibe & Verify" engineering suite for AI coding agents.**

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Claude Code](https://img.shields.io/badge/Claude%20Code-Plugin-blueviolet)](https://docs.anthropic.com)
[![Cursor](https://img.shields.io/badge/Cursor-Rules%20%26%20Plugin-black)](https://cursor.com)
[![Google Antigravity](https://img.shields.io/badge/Antigravity-Skills%20Suite-4285F4)](https://github.com/rmyndharis/antigravity-skills)
[![Agent Skills](https://img.shields.io/badge/Agent%20Skills-Standard-green)](https://agentskills.io)

`Vibe-Coding-Orchestrator` solves the primary failure mode of generative AI in software engineering: **agents creating naive, unverified, surface-level code that breaks under real-world conditions.**

It introduces the **"Vibe & Verify"** paradigm:
* **The Human provides the Vibe:** High-level intent, user stories, domain priorities, and creative direction.
* **The Agent enforces the Rigor:** Relentlessly interviews the user via a design tree, calibrates implementation depth, locks down database migrations, models zero-trust security, enforces strict Test-Driven Development (TDD) at deep module seams, dispatches adversarial reviewer subagents, and runs multi-tier performance profiling.

---

## ⚡ Quickstart

### 1. Agent Skills (Universal)
Install the orchestrator or individual skills using the universal [Agent Skills](https://agentskills.io) CLI (works with Claude Code, Cursor, Codex, Gemini CLI, Antigravity, and 40+ agents):

```bash
# Add the complete Vibe Coding suite
npx skills add OBHAIS4174/Vibe-Coding-Orchestrator

# Or add the master orchestrator specifically
npx skills add OBHAIS4174/Vibe-Coding-Orchestrator --skill vibe-coding-orchestrator
```

---

### 2. Claude Code
This repository serves directly as a native Claude Code marketplace plugin:

```bash
# Add the marketplace
claude plugin marketplace add OBHAIS4174/Vibe-Coding-Orchestrator

# Install the orchestrator plugin
claude plugin install vibe-coding-orchestrator@vibe-coding
```

---

### 3. Google Antigravity (AGY)
Install directly into your global or project-level Antigravity skills repository:

```bash
# Via agy CLI
agy plugin install https://github.com/OBHAIS4174/Vibe-Coding-Orchestrator

# Or clone directly into your project's workspace:
git clone https://github.com/OBHAIS4174/Vibe-Coding-Orchestrator.git .agent/skills/vibe-suite
```

---

### 4. Cursor
Add the rules directly to your project workspace:

```bash
# Create rules directory and copy rule
mkdir -p .cursor/rules
curl -sSL https://raw.githubusercontent.com/OBHAIS4174/Vibe-Coding-Orchestrator/main/.cursor/rules/vibe-coding-orchestrator.mdc -o .cursor/rules/vibe-coding-orchestrator.mdc
```
*Or reference `@vibe-coding-orchestrator` in your Cursor Composer or Chat prompt.*

---

### 5. VS Code & GitHub Copilot
Works natively via the standard `.agents/skills/` cross-client specification:

1. Open your project in **VS Code** with the **GitHub Copilot Chat** extension installed.
2. Select **Agent mode** from the mode dropdown at the bottom of the chat panel.
3. Type `/skills` in the chat input to confirm that `vibe-coding-orchestrator` appears in your skills list.
4. Prompt the agent: *"Build a billing refund feature using vibe-coding-orchestrator"*.

---

## 🔄 The 8-Phase "Vibe & Verify" Lifecycle

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

## 📦 What's Inside: Bundled Skills Catalog

This repository ships 19 deeply integrated, battle-tested engineering skills:

| Skill | Category | Role in the Orchestration Suite |
| :--- | :--- | :--- |
| **`vibe-coding-orchestrator`** | Master Orchestrator | The central pipeline controller managing the 8-phase lifecycle |
| **`spec-driven-agentic-workflow`** | Methodology | Spec-first architecture with immutable invariant guarantees |
| **`grilling`** | Discovery | Relentless Socratic interview mapping requests to a design tree |
| **`domain-modeling`** | Discovery | Active vocabulary sharpening, `CONTEXT.md` sync & ADR authoring |
| **`codebase-design`** | Architecture | Designing deep modules with tiny interfaces & maximum leverage |
| **`database-architect`** | Data Layer | Data modeling, schema normalization, and index strategy |
| **`database-migration`** | Data Layer | Zero-downtime expand/contract migration procedures |
| **`database-optimizer`** | Performance | Query optimization, N+1 query resolution & indexing |
| **`security-auditor`** | Security | Zero-trust modeling, RBAC validation & OWASP audit checks |
| **`security-scanning-security-hardening`** | Security | Multi-layer vulnerability detection and pipeline hardening |
| **`api-design-principles`** | Architecture | RESTful & GraphQL idempotency, pagination, and error contracts |
| **`code-refactoring-refactor-clean`** | Clean Code | Refactoring code for SOLID principles and minimal cyclomatic complexity |
| **`code-review-ai-ai-review`** | Verification | Independent two-axis grading (Spec Compliance + Code Quality) |
| **`prototype`** | Prototyping | Throwaway UI/logic exploration to calibrate feel before coding |
| **`ui-ux-designer`** | Frontend | Accessible, user-centered interface layouts & design systems |
| **`tailwind-design-system`** | Frontend | Scalable design tokens and component styling patterns |
| **`application-performance-performance-optimization`** | Observability | Profiling runtime bottlenecks and memory footprints |
| **`devops-troubleshooter`** | DevOps | Distributed log analysis, tracing, and automated incident diagnosis |
| **`distributed-debugging-debug-trace`** | Diagnostics | OpenTelemetry spans, context propagation, and diagnostic harnesses |

---

## 🛡️ Core Architectural Invariants

Every project executed through this orchestrator upholds five mandatory system boundaries:

1. **Confirm-Before-Swap**: Live serving state is never mutated in-place. Changes are staged, indexed/validated in isolation, and swapped atomically.
2. **State Isolation**: Draft/pending modifications are decoupled from live visibility (e.g. `hasPendingVersion` independent of `isPublish`).
3. **Collision-Proof Sequences**: Sequence generation queries database history (`max(existing) + 1`), preventing optimistic increment crashes.
4. **Append-Only History**: Edits and rollbacks create new immutable version records (`source: 'rollback'`); historical records are never deleted.
5. **Deep Tenant Isolation & RBAC**: Tenant boundaries are enforced directly in data-layer queries (`{ tenantId, ... }`), never filtered in memory.

---

## 🎯 Implementation Depth Calibration

To prevent agents from defaulting to shallow code, the orchestrator explicitly prompts the user to calibrate depth before any spec is approved:

* **Level 1: Vibe Check (Throwaway Prototype)** — Fast UI mockup; code is thrown away before build.
* **Level 2: Standard MVP** — Basic feature set with primary unit tests.
* **Level 3: Production Robust [Default]** — Strict TDD, immutable invariants, sanitized error messages.
* **Level 4: Mission-Critical Enterprise** — Zero-downtime DB migrations, distributed tracing, N+1 query audit, and complete regression pass.

---

## 📄 License

MIT License. Open source and free for individual developers, startups, and enterprise engineering teams.
