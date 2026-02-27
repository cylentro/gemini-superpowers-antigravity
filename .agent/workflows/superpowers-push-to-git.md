---
description: Build, verify, and push changes to Git with automated README updates.
---

# Push to Git

This workflow ensures that code is verified and documented before being pushed to the repository.

## 1. Safety Check
Determine if any code files were modified or if this is an asset/documentation-only update.

## 2. Asset-Only Path
IF **no code files** were modified (only `.md`, `.txt`, images, etc.):
1) Update `README.md` if necessary to reflect the changes.
// turbo
2) Stage all changes: `git add .`
// turbo
3) Commit changes: `git commit -m "docs: minor updates and assets"`
// turbo
4) Push to remote: `git push origin HEAD`

## 3. Code & Logic Path
IF **code files** were modified (Python, JS, etc.):
1) **Run Verification**:
// turbo
- Run tests and linting: `pytest` (or relevant test runner for the project).
- IF tests fail: **STOP**. Fix errors before proceeding.

2) **Quality Review**:
- Run `/superpowers-review` to double-check for logic errors or security issues.
- Address any "Blocker" or "Major" issues found.

3) **Documentation**:
- Update `README.md` with a brief summary of the technical changes or new features.

4) **Execution**:
// turbo
- Stage all changes: `git add .`
// turbo
- Commit with conventional message: `git commit -m "feat/fix: [brief description of changes]"`
// turbo
- Push to remote: `git push origin HEAD`

## 4. Finalization
// turbo
- Log the push details to `artifacts/superpowers/push_details.md`.
- Provide a summary of the push to the user.
