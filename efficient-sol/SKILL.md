---
name: efficient-sol
description: Use when running Codex Sol with Extra High reasoning on codebase-heavy, ambiguous, or token-heavy work and the user wants Sol to orchestrate research, implementation, and validation while delegating bounded work to subagents chosen according to task complexity.
---

# Efficient Sol

Use Codex Sol with Extra High reasoning as the primary orchestrator, architect,
integrator, and final judge. Delegate bounded work when doing so saves time or
context without weakening ownership of the result.

## Route Work by Complexity

Keep the primary task on Sol Extra High. For each independent slice, assess its
ambiguity, breadth, risk, and required judgment before selecting an available
subagent model:

- Route low-complexity work such as repository inventories, targeted searches,
  log reduction, mechanical edits, and routine test runs to fast models.
- Route medium-complexity work such as bounded implementation, reproduction,
  focused debugging, and test authoring to balanced models.
- Route high-complexity work such as cross-cutting design, security-sensitive
  changes, conflicting evidence, and ambiguous debugging to stronger models or
  keep it with Sol Extra High.

Choose by capability rather than by a hard-coded model list. Use model and
reasoning controls when the runtime exposes them. If it does not, delegate the
well-scoped slice and let the Codex runtime select the worker model. Escalate a
slice when the worker reports uncertainty, uncovers wider scope, or cannot
produce evidence strong enough for the decision.

Do not delegate merely to use every available agent. Keep tiny tasks, tightly
coupled edits, shared-file integration, and judgment-sensitive validation with
Sol when coordination would cost more than it saves.

## Orchestrate the Task

1. Identify the decision layer that requires Sol's judgment.
2. Split only independent work into bounded research, implementation, or
   validation slices.
3. Select a worker tier for each slice from its complexity and risk.
4. Run independent slices in parallel when tooling and concurrency limits allow.
5. Reopen important cited files, inspect the final diff, and rerun critical
   verification before accepting delegated work.
6. Resolve conflicting reports, integrate the result, assess residual risk, and
   give the user one coherent answer.

Avoid parallel edits to the same files. Assign explicit file ownership or make
overlapping agents research-only until Sol chooses an implementation path.

## Write Self-Contained Handoffs

Give each worker only the context needed to complete its slice:

- Provide the repository path and exact objective.
- State files, packages, and surfaces in scope and out of scope.
- Specify whether the worker may edit files or must remain read-only.
- Request concise evidence: file paths, line references, commands, diffs,
  failures, screenshots, and uncertainties as applicable.
- Name verification commands or user flows and define success when knowable.
- Set stop conditions for mismatched code, repeated command failure, scope
  expansion, destructive actions, missing authority, or unresolved ambiguity.

Require workers to report instead of improvising past a stop condition.

## Verify Delegated Work

Treat worker reports as leads, not facts. Before making a high-impact decision,
changing external state, publishing work, or declaring completion:

- Inspect the decisive source files and cited evidence yourself.
- Review the combined diff for task fit and unintended changes.
- Run verification proportional to the risk of the change.
- Distinguish product failures from flaky or environmental failures.
- Surface remaining uncertainty instead of smoothing it over.

Let subagents gather and compress signal. Keep final truth judgment,
integration, risk assessment, and user-facing synthesis with Sol Extra High.
