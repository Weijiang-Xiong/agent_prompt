## General Agreements for AI Agents

The code will be reviewed by a human expert and multiple AI agents.

Prioritize correctness, readability, and minimal, well-scoped changes.

Do not add optional existence checks, fallback branches, or defensive guards

## Core Rules

- Follow the user's requested scope closely.
- Challenge incorrect assumptions when they materially affect correctness.
- Make the smallest correct change.
- Prefer editing existing code over introducing new abstractions.
- Do not refactor unless it is required for correctness or explicitly requested.
- Do not create new files unless required to complete the task.
- Do not delete files unless explicitly required by the user.
- Do not delete comments unless explicitly required by the user.

## Development Philosophy

**Simplicity**: Implement minimal solution with correct logic.

**Readability**: Keep code easy to understand and maintain.

**Performance**: Optimize when it does not reduce readability.

**Correctness**: Prefer fixing the root cause over adding fallbacks, broad catches, or defensive checks that hide broken logic.

## Preparation Before Editing

1. Analyze the implicit assumptions in the user request.
2. Identify uncertain information that will materially change the implementation.
3. Carefully inspect the current implementation, the direct callers and downstream consumers of related codes.
4. Watch for common failure modes, especially:
   - silent fallbacks
   - broad exception handling
   - guard clauses that hide incorrect core logic
   - rejecting valid edge cases instead of handling them
   - repeated null or type checks that suggest weak invariants

## Editing Guidelines

For non-trivial tasks, use this loop:

1. edit
2. self-review
3. revise

Code edit scope:

* Do not refactor unless requested.
* Prefer editing existing code over adding new classes, helpers, or wrappers.
* If a guard clause, error handling or type checking has to be added, write the reason in comment.
* If a function is very short and used only once, write inline to avoid unnecessary abstraction

In code review, look for:

* Silent fallbacks or broad catches that hide failures
* Guard clauses that mask broken core logic
* Valid edge cases rejected instead of handled
* Repeated null/type checks that signal weak invariants

If found, **fix the root cause**. Adding a guard or fallback is not a fix. Report unresolved issues.

## Report

If any modification is made, report:

* any code files changed, created or deleted, with a brief reason
* saved visualization and result files and their content
* validation run (or why not run)
* self-review results including:
  - The core invariants your code maintains;
  - The edge cases it handles
  - Any real remaining limitation.

## Documentation Notes

When creating markdown files:

* format with clear sections and subsections
* use tables, bullet points and code blocks for clarity
* include references to related files and documentation
