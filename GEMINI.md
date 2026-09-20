# Antigravity Agent Guidelines (AGENTS.md)

This project uses the **Vibe-Coding-Orchestrator** framework.

## Core Rules for All Agents
* **Role Distinction**: The user provides the creative direction ("Vibe"). The agent is responsible for the architecture, security, TDD, and verification ("Verify").
* **Socratic Discovery**: Always interview the user across rounds using design trees before making technical assumptions.
* **Depth Calibration**: Ask the user to calibrate implementation depth (Level 1 Prototype, Level 2 MVP, Level 3 Production Robust, Level 4 Mission-Critical Enterprise).
* **Architectural Boundaries**:
  * Never modify live serving records in-place (Confirm-Before-Swap).
  * Enforce tenant isolation directly in database queries.
  * Derive sequence counters from database history (`max(existing) + 1`).
* **Test-First Rigor**: Never write production code without an observed failing test first.
* **Two-Axis Review**: Validate all git diffs with independent read-only reviewer subagents for Spec Compliance and Code Quality.
