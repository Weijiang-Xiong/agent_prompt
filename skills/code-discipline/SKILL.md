---
name: code-discipline
description: Must be used for every task that writes, modifies, debugs, reviews, or refactors code. Enforces simple, surgical, non-defensive implementation and verifiable completion.
---

## Code Discipline for Agents

The code will be reviewed by a human expert and multiple AI agents.

Prioritize correctness, readability, and minimal, well-scoped changes.

## 1. Think Before Coding

**Don't assume. Don't hide confusion. Surface tradeoffs.**

Before implementing:

- Inspect the existing codebase carefully.
- State your assumptions explicitly. If uncertain, ask.
- If multiple interpretations exist, present them - don't pick silently.
- If a simpler approach exists, say so. Push back when warranted.
- If something is unclear, stop. Name what's confusing. Ask.

## 2. Simplicity First

**Minimum code that solves the problem. Nothing speculative.**

- No features beyond what was asked.
- No abstractions for single-use code.
- No "flexibility" or "configurability" that wasn't requested.
- No error handling for impossible scenarios.
- If you write 200 lines and it could be 50, rewrite it.

Ask yourself: "Would a senior engineer say this is overcomplicated?" If yes, simplify.

## 3. Surgical Changes

**Touch only what you must. Clean up only your own mess.**

When editing existing code:

- Don't "improve" adjacent code, comments, or formatting.
- Don't refactor things that aren't broken.
- Match existing style, even if you'd do it differently.
- If you notice unrelated dead code, mention it - don't delete it.
- Every changed line should trace directly to the user's request.

When your changes create orphans:

- Remove imports/variables/functions that YOUR changes made unused.
- Don't remove pre-existing dead code unless asked.

Be extra careful with deletions:

- Do not delete files unless explicitly required by the user.
- Do not delete comments unless explicitly required by the user.

When writing new codes, add comments or doc-strings for:

- design choices and trade-offs discussed with the user
- math and non-trivial logic

## 4. Critical Self-Review

Critically review the edits before finalizing. Look for:

- Silent fallbacks or broad catches that hide failures
- Guard clauses that mask broken core logic
- Valid edge cases rejected instead of handled
- Repeated null/type checks that signal weak invariants

Fix the root cause and report unresolved issues.

## 5. Goal-Driven Execution

**Define success criteria. Loop until verified.**

For simple tasks, keep the workflow efficient, never over-complicate them.

For multi-step tasks, turn tasks into verifiable steps, state a brief plan:

```
1. [Step] → verify: [check]
2. [Step] → verify: [check]
3. [Step] → verify: [check]
```

Strong success criteria let you loop independently. Weak criteria ("make it work") require constant clarification.

## 6. Change Report

If any modification is made, make a simple report in the chat:

- Any code files changed, created or deleted, with a brief reason
- Saved visualization and result files and their content
- Validation run (or why not run)
- Self-review results

For complex tasks, write a more detailed markdown report for these topics, and additionally include:

- Overall Task objective and design choices
- Usage example for new files