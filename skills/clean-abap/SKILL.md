---
name: clean-abap
description: Apply Clean ABAP guidance when creating, refactoring, reviewing, or explaining ABAP artifacts such as classes, interfaces, reports, function modules, and unit tests.
license: CC BY 3.0
---

# Clean ABAP

Use this skill whenever the task involves ABAP artifacts, especially global classes, local classes, interfaces, reports, includes, function modules, methods, internal tables, exception handling, or ABAP Unit tests.

## When to Use

- Writing new ABAP code.
- Refactoring legacy ABAP code.
- Reviewing ABAP code for readability, maintainability, or consistency.
- Naming classes, methods, parameters, variables, constants, or test code in ABAP.
- Deciding between old and modern ABAP syntax.
- Improving ABAP error handling, formatting, and unit tests.

## Working Principles

1. Preserve behavior first.
Only change external behavior when the user explicitly asks for it.

2. Prefer the cleanest solution that fits the codebase and release level.
Use modern, object-oriented, expressive ABAP when the target system supports it.

3. Do not mix conflicting styles without reason.
If a legacy object consistently uses an old style and a full cleanup is not part of the task, avoid partial rewrites that make the object internally inconsistent.

4. Optimize for readability before cleverness.
Prefer code that is easy to scan, explain, test, and safely change.

5. Do not optimize prematurely.
Treat performance concerns as real only when supported by measurements, known hot paths, or explicit project constraints.

## Core Guidance

### Names

- Use descriptive names that communicate intent.
- Prefer problem-domain or solution-domain terms that other developers will recognize.
- Use `snake_case` consistently.
- Avoid unnecessary abbreviations. If abbreviations are required, use the same one everywhere.
- Use nouns for classes, interfaces, and objects.
- Use verbs or verb phrases for methods and functions.
- Avoid noise words such as `data`, `info`, or `object` unless they add real meaning.
- Do not use Hungarian notation or encoding prefixes like `iv_`, `ev_`, `rv_`, `lt_`, or `ls_` unless the existing codebase explicitly standardizes on them and the task requires staying consistent.
- Do not obscure ABAP built-in functions with method names like `lines`, `line_exists`, `condense`, or `strlen`.

### Language And Structure

- Prefer object orientation over procedural programming where feasible.
- Prefer functional, expression-oriented ABAP over verbose procedural statements when it improves clarity.
- Avoid obsolete language constructs when modern equivalents are available on the supported release.
- Use design patterns only where they clearly improve the design.
- Prefer composition over inheritance unless inheritance is truly the right model.
- Make classes `FINAL` unless they are explicitly designed for inheritance.
- Keep members `PRIVATE` by default.

### Methods

- Methods should do one thing only.
- Keep methods small and focused.
- Keep all statements within a method at one level of abstraction.
- Prefer instance methods over static methods unless static semantics are clearly appropriate.
- Public instance methods should usually be exposed through interfaces.
- Aim for a small number of importing parameters.
- Split methods instead of adding unrelated optional parameters.
- Avoid boolean input parameters when they create two behaviors. Split the method instead.
- Return one logical result.
- Prefer `RETURNING` over `EXPORTING` for single-result methods.
- Avoid mixing `RETURNING`, `EXPORTING`, and `CHANGING` unless there is a strong reason.
- Use `CHANGING` sparingly.
- Prefer `RESULT` as the `RETURNING` parameter name unless a more specific name is genuinely clearer.
- Fail fast on invalid input.
- Separate happy-path logic from error-handling logic when possible.

### Variables, Tables, Strings, And Conditions

- Prefer inline declarations close to first use.
- Do not let variables leak beyond the block where they are conceptually needed.
- Avoid chaining up-front declarations unless the declarations form a meaningful group.
- Choose table types intentionally: `STANDARD`, `SORTED`, or `HASHED` based on usage.
- Avoid `DEFAULT KEY`; prefer explicit keys or `EMPTY KEY`.
- Prefer `INSERT INTO TABLE` over `APPEND TO` unless array semantics are intentional.
- Prefer `LINE_EXISTS`, table expressions, and direct reads over verbose `READ TABLE ... sy-subrc` patterns when clarity improves.
- Use string templates `|...|` to assemble text.
- Use `ABAP_BOOL`, `ABAP_TRUE`, `ABAP_FALSE`, and `XSDBOOL` consistently for boolean logic.
- Prefer positive conditions.
- Prefer `IS NOT` forms over `NOT ... IS` when readability improves.
- Extract complex conditions into helper variables or helper methods.

### Error Handling

- Prefer exceptions over return codes.
- Use class-based exceptions.
- Throw one meaningful exception supertype per operation where possible.
- Wrap foreign exceptions instead of leaking external exception types through your own abstraction.
- Use `CX_STATIC_CHECK` for expected and recoverable failures.
- Use `CX_NO_CHECK` only for usually unrecoverable situations.
- Dump only for truly unrecoverable programming or runtime failures.
- Prefer `RAISE EXCEPTION NEW` when available.

### Comments And Formatting

- Express intent in code before adding comments.
- Use comments to explain why, not what.
- Delete dead code instead of commenting it out.
- Avoid manual versioning comments.
- Use `TODO`, `FIXME`, or `XXX` sparingly and include an identifiable owner.
- Be consistent with the existing formatting style of the object or team.
- Optimize formatting for reading, not typing speed.
- Keep one statement per line.
- Keep nesting shallow.

### Testing

- Write code so dependencies can be replaced in tests.
- Test public behavior, not private internals.
- Keep tests readable and purpose-driven.
- Prefer local test classes where appropriate.
- Use meaningful names for the code under test and for test methods.
- Follow `given-when-then` structure when it helps readability.
- Keep assertions focused and specific.

## ABAP Review Checklist

When reviewing or generating ABAP code, check these questions explicitly:

- Are names descriptive and consistent?
- Is the code using modern syntax that the target release supports?
- Is there unnecessary nesting or branching?
- Does each method have one clear responsibility?
- Are parameters minimal and meaningful?
- Is exception handling explicit and consistent?
- Are internal tables typed and accessed intentionally?
- Are comments useful instead of compensating for weak code?
- Is the code testable and are the tests focused on behavior?

## Legacy Code Rules

- Improve code incrementally instead of forcing full rewrites.
- Follow the boy scout rule: leave the code a little cleaner than you found it.
- Build small clean islands when broad refactoring is risky.
- If a large object is consistently legacy-style, avoid half-modernizing one corner unless the task is specifically a refactor.
- When modernizing, prioritize readability, safety, and testability over breadth of change.

## Output Expectations

When applying this skill, the agent should:

- Explain ABAP-specific tradeoffs briefly and concretely.
- Prefer code examples that reflect Clean ABAP style.
- Call out release-level assumptions when syntax depends on a newer ABAP platform.
- Mention when it intentionally preserves legacy consistency instead of applying a cleaner alternative.

## Source

This skill is derived from the Clean ABAP guidance maintained in this repository's `CleanABAP.md` source document.