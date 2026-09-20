# Task [N] Brief: [Task Title]

## 1. Context & Objective
- **Feature Area**: [e.g. Flashcard Version Control / Document Replacement]
- **Target Seam**: [e.g. `editUploadedDocument` in `apis/uploaddocument/uploaddocumentController.js`]
- **Objective**: [1-2 sentences describing what capability this task builds and why]

## 2. Invariants & Global Constraints
The following system invariants bind this implementation and must be strictly upheld:
- **Confirm-Before-Swap**: Live serving content must remain completely untouched until reindexing/storage succeeds.
- **State Isolation**: Edits to published content create a pending version row (`approvalStatus: 'pending'`); live `title`, `fileName`, and `status` remain intact.
- **Collision-Proof Counters**: Do not increment optimistically; query database history (`maxExisting + 1`) and update existing pending version on secondary edits.
- **Tenant Isolation**: Strictly scope queries to `req.user.tenantId` for non-global admins.

## 3. Files Under Modification
- **Models**: `[path/to/model]`
- **Controllers/Endpoints**: `[path/to/controller]`
- **Tests**: `[path/to/test]`

## 4. Test-First Deliverables
1. Write failing tests covering:
   - Happy path: [description]
   - Error / boundary path: [e.g. 404 cross-tenant, 403 agent]
   - Regression / invariant path: [e.g. live content remains unchanged while pending]
2. Execute test command:
   ```bash
   npm test tests/[testName].test.js
   ```
3. Implement production code until tests pass (`PASS`).
4. Run full regression suite:
   ```bash
   npm test
   ```

## 5. Output Deliverable
Produce `task-[N]-report.md` detailing:
- Commit hash
- Files modified
- Test results
- Verification against invariants
