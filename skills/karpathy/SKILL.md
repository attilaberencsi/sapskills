---
name: karpathy
description: Apply to all programming languages when creating, refactoring, reviewing, or explaining source code artifacts. Behavioral guidelines for coding agents to reduce common implementation mistakes by surfacing assumptions, preferring simple solutions, keeping edits tightly scoped, and validating against explicit success criteria. 
license: MIT
---

# Karpathy

Use this skill when writing, reviewing, debugging, or refactoring code and you want stronger execution discipline: fewer silent assumptions, less overengineering, tighter diffs, and clearer validation.

This skill is adapted from the MIT-licensed `karpathy-guidelines` skill in `multica-ai/andrej-karpathy-skills`, itself based on Andrej Karpathy's observations about common LLM coding failure modes.

## When to Use

- Implementing a feature with ambiguous requirements.
- Fixing bugs where the root cause is not yet proven.
- Refactoring code that is easy to overcomplicate.
- Reviewing a change for unnecessary scope or weak validation.
- Directing an agent that needs stronger guardrails around reasoning and execution.

## 1. Think Before Coding

Do not guess silently.

- State assumptions before relying on them.
- If the task can be interpreted more than one way, surface the alternatives instead of choosing one invisibly.
- If something is unclear enough to change the implementation, stop and ask.
- If a requested direction looks riskier or more complex than necessary, say so and explain the tradeoff.
- Before editing, identify the controlling code path, one falsifiable local hypothesis, and the cheapest check that could prove it wrong.

## 2. Simplicity First

Solve the problem with the minimum necessary code.

- Do not add features that were not requested.
- Do not add abstractions for one-off usage.
- Do not add configurability, indirection, or future-proofing without a concrete need.
- Avoid speculative error handling for scenarios that are impossible or unsupported.
- If a simpler design achieves the same outcome, prefer it.
- If a solution becomes long or layered, ask whether most of it is actually necessary.

## 3. Surgical Changes

Keep the diff tightly aligned with the request.

- Touch only the files and lines needed for the task.
- Do not opportunistically refactor nearby code, comments, or formatting.
- Match the surrounding style unless the task explicitly includes cleanup.
- Remove only the dead code or imports created by your own change.
- If you notice unrelated issues, mention them separately instead of mixing them into the patch.
- Every changed line should be explainable as a direct consequence of the requested outcome.

## 4. Goal-Driven Execution

Turn tasks into verifiable outcomes.

- Define what success looks like before making broad edits.
- For bug fixes, prefer a failing reproduction or focused check before and after the fix.
- For refactors, preserve behavior and verify it with the narrowest practical test or check.
- For multi-step work, keep a short plan where each step has an explicit validation method.
- After the first substantive edit, run the cheapest focused validation before expanding scope.
- Continue until the requested outcome is verified or a concrete blocker is identified.

## Review Prompts

When using this skill, explicitly ask:

- What am I assuming, and how can I verify it cheaply?
- Is this the simplest implementation that satisfies the request?
- Did I change anything outside the necessary slice?
- What exact check proves the task is done?

## Tradeoff

These rules bias toward caution and precision over raw speed. For trivial, obvious edits, apply them with proportionate rigor rather than ceremony.

## Source

Adapted from the MIT-licensed `karpathy-guidelines` skill in `multica-ai/andrej-karpathy-skills`.