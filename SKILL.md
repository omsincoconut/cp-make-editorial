---
name: cp-make-editorial
description: "Solve and write the model solution and editorial for competitive-programming problems."
triggers: [user]
---

# Competitive Programming: Model Solution and Editorial

## Activation

Use this skill only when explicitly invoked by the user. Do not activate it automatically.

This skill is responsible for solving a competitive programming problem and producing a correct, efficient C++ model solution and a rigorous, accessible editorial.

## 1. Read the Problem

Locate and read the problem statement in the workspace, typically `statement.txt` or a similarly named file.

Identify the objective, constraints, input/output format, and any special requirements. Follow the statement precisely.

## 2. Solve the Problem

Develop an algorithm that solves the problem within its constraints.

- Aim for the best possible worst-case time and space complexity.
- Prefer simple, elementary approaches when they achieve comparable efficiency.
- Establish correctness rigorously. Do not rely on intuition, testing, or the absence of counterexamples as proof.
- Use code experiments, brute-force solvers, mathematical exploration, and subagents when useful.
- Test implementations against small exhaustive cases, random cases, and carefully chosen edge cases when practical.

You may create temporary files and run experiments in the workspace.

For substantial explorations, prefer delegating independent investigations to subagents when available. Keep only the important findings and reasoning in the main context; leave intermediate exploration details in the subagents' contexts.

Once finished, move exploratory files into `tmp/` and remove compiled executables. Preserve any code, certificates, or other artifacts required by the final proofs, and reference them in the editorial.

## 3. Write the Model Solution

Create `model.cpp` containing the C++ implementation of the main algorithm.

Requirements:

- Follow the input/output protocol in the statement. If none is specified, choose a reasonable protocol.
- Produce a complete, compilable, and correct solution.
- Optimize for worst-case performance under the stated constraints.
- Keep the implementation as simple and readable as possible without sacrificing necessary efficiency.
- Avoid unnecessary abstractions, auxiliary data structures, and implementation complexity.

## 4. Write the Editorial

Create `editorial.md` explaining the model solution.

The editorial must contain:

1. **Algorithm:** Explain the main insights and each step of the algorithm in sufficient detail to reconstruct the implementation.
2. **Correctness proof:** Prove every claim required for correctness, including intermediate lemmas and assumptions.
3. **Complexity analysis:** Derive the time and space complexity and explain why they satisfy the constraints.

### Proof Standards

Every mathematical claim used in the solution must be justified.

- Never describe a claim as "trivial," "obvious," or "standard" instead of proving it.
- Even when using a well-known result or technique, explain and prove the relevant properties rather than merely citing its name.
- Do not omit intermediate reasoning that is necessary to establish correctness.
- Distinguish rigorously proven claims from conjectures, empirical observations, and heuristics.
- Testing is useful for finding bugs but does not constitute a proof.

### Computational Proofs

Computational proofs are permitted only when they take one of these forms:

1. **Complete exhaustion:** A program exhaustively checks a clearly specified finite search space that covers every relevant possibility.
2. **Certificate verification:** A program finds a finite certificate whose validity can be independently verified and whose existence proves the claim.

For either form:

- Include the source code used in the computation.
- Explain precisely what the program checks and why those checks establish the claim.
- For complete exhaustion, justify the search-space bounds and coverage.
- For certificate-based proofs, include the certificate and explain how to verify it.

A failed search for counterexamples is not a proof unless the search is demonstrably exhaustive.

### Writing Style

Make the editorial as simple and accessible as possible without weakening its rigor.

- Prefer elementary explanations over advanced mathematical machinery when both suffice.
- Introduce a definition or variable only when it represents a central idea or is reused enough to improve clarity.
- Avoid excessive notation and unnecessary intermediate lemmas.
- Explain the intuition behind the algorithm, then establish its correctness formally.
- Keep proofs concise, but never omit necessary logical steps.

## 5. Consider a Simpler Alternative

If there is a substantially simpler algorithm that still satisfies the problem's constraints, but is slightly less efficient than the main solution, also create:

- `model_simple.cpp` — the simpler C++ implementation.
- `editorial_simple.md` — its explanation, correctness proof, and complexity analysis.

The simpler alternative must be a fully valid solution, not merely a heuristic or an approach that works on small inputs.

The main solution should still aim for the best achievable efficiency. Do not sacrifice a significant performance improvement merely to make the main implementation shorter.

Simplify both solutions and editorials as much as possible while retaining correctness, efficiency, and proof quality.

## 6. Independent Editorial Review

Spawn an independent subagent to critically examine the editorial before finalizing it.

The subagent's task is to attack the proposed solution and its proof, rather than merely confirm them. In particular, it should look for:

- Incorrect or unjustified claims.
- Missing cases, hidden assumptions, and logical gaps.
- Counterexamples to the algorithm or intermediate lemmas.
- Mistakes in worst-case complexity analysis.
- Discrepancies between the editorial and the C++ implementation.
- Opportunities for meaningful simplification.

The review should be independent: the subagent must be free to challenge the proposed reasoning rather than assume its correctness.

Resolve every valid objection. Revise the algorithm, implementation, or editorial as necessary.

## 7. Exploratory and Optimization Problems

Some problems may be exploratory or may request a construction that is "as good as possible."

### If a Complete Solution Cannot Be Found

Make the strongest progress possible rather than abandoning the task.

- Present any correct partial algorithms, bounds, constructions, or special-case solutions.
- Prove all results that are claimed as established.
- Clearly identify what remains unresolved.
- Do not misrepresent a partial solution as a complete one.

### If a Stronger Result Is Possible

If a result stronger than the statement requires emerges naturally, include it in the editorial with a proof.

However, do not devote substantial resources to pursuing stronger results when there is no clear path to obtaining them.

### Optimization and Construction Problems

For problems asking for the best possible construction, prioritize the following outcomes, in order:

1. A globally optimal construction together with a proof of optimality.
2. A construction with a tight or nearly tight proven bound.
3. The strongest construction obtainable, accompanied by the best available bounds.

If proving global optimality is infeasible, focus more effort on improving the construction than on marginally tightening theoretical bounds.

Unless the statement specifies otherwise, assess solution quality primarily by **worst-case performance**, not average-case or experimentally observed performance.

## 8. Final Deliverables

Required files:

| File | Purpose |
|---|---|
| `model.cpp` | Main C++ model solution |
| `editorial.md` | Detailed algorithm, rigorous correctness proof, and complexity analysis |

Additional files when applicable:

| File | Purpose |
|---|---|
| `model_simple.cpp` | Simpler alternative solution |
| `editorial_simple.md` | Editorial for the simpler alternative |
| Proof source files | Programs supporting computational proofs |
| Certificate files | Certificates required by computational proofs |
| `tmp/` | Archived exploratory work and temporary files |

Before finishing, verify that:

- The implementation compiles and follows the input/output protocol.
- The algorithm satisfies the stated constraints in the worst case.
- The editorial accurately describes the submitted implementation.
- Every correctness claim has a complete justification.
- Any computational proof includes reproducible evidence.
- The independent editorial review has been performed and valid issues resolved.
- The final solutions and editorials have been simplified without sacrificing quality.
- Temporary files have been organized and compiled executables removed.

The final objective is **the most efficient correct solution that can be expressed and proved as simply as possible**, with a rigorous, self-contained editorial.