# Vibe-Coding-Orchestrator

The ultimate **"Vibe & Verify"** development orchestrator. 

This plugin explicitly shifts the paradigm of software development: **The Human provides the Intent and the Vibe. The Agent provides the Rigor, Architecture, and Verification.** 

By invoking this workflow, your AI agent will sequentially wear the hats of a Product Manager, Database Architect, Security Auditor, TDD Implementer, and DevOps Reviewer, ensuring the human's "vibe" becomes bulletproof production code without burdening them with the syntax or boilerplate.

## Supported AI Assistants
This repository provides native plugins and rules for the top AI coding frameworks.

---

### 1. Claude Code
Claude Code supports plugins directly.

**Installation:**
Run this in your terminal:
```bash
claude plugin add https://github.com/OBHAIS4174/Vibe-Coding-Orchestrator/tree/main/claude-code
```

**Usage:**
Type `/vibe-coding-orchestrator` in your Claude Code session.

---

### 2. Antigravity (AGY)
Antigravity supports deep workflows and progressive disclosure.

**Installation:**
Run this in your terminal:
```bash
agy plugin install https://github.com/OBHAIS4174/Vibe-Coding-Orchestrator/tree/main/antigravity
```

**Usage:**
Just mention you want to use the `vibe-coding-orchestrator` skill, or trigger it natively if registered as an always-on rule.

---

### 3. Cursor
Cursor steers AI behavior using `.mdc` rules.

**Installation:**
Copy the `.mdc` file into your project:
1. Create a `.cursor/rules/` directory at the root of your project if it doesn't exist.
2. Copy `cursor/.cursor/rules/vibe-coding-orchestrator.mdc` from this repository into your project's `.cursor/rules/` folder.

**Usage:**
When chatting in Cursor or using Cmd+K, mention `@vibe-coding-orchestrator` to force the AI to follow the Vibe & Verify protocol.

---

## The Workflow Lifecycle

1. **The Vibe (Human):** Human expresses intent. Agent "Grills" to extract the Domain Model.
2. **The Rigor (Agent):** Agent acts as Architect & Security Auditor to define invariants.
3. **The Prototype (Loop):** Agent builds rapid throwaways until the Human approves.
4. **Test-First (TDD):** Agent writes failing tests at deep module seams (Red).
5. **Clean Implementation:** Agent writes SOLID code (Green), applies Refactor patterns.
6. **Multi-Agent Review:** Subagents grade code on Spec Compliance & Security (OWASP).
7. **DevOps Verify:** Builds, N+1 Query checks, and error sanitation. 
