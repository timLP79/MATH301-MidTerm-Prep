# Week 1 — Linear Systems

## What Makes an Equation Linear?

**Definition:** An equation in variables x₁, x₂, ..., xₙ is **linear** if every variable appears
only to the first power, is not multiplied by another variable, and is not inside any function
(square root, trig, etc.). The general form is:

    a₁x₁ + a₂x₂ + ... + aₙxₙ = b

where a₁,...,aₙ and b are constants (can be zero).

### Quiz Examples — Linear or Not?

| Equation | Linear? | Reason |
|---|---|---|
| 3x + 6y − 4z = 9 | **YES** | each variable appears once, degree 1 |
| 2x² + 4x − 7 = y | **NO** | x² — variable raised to power 2 |
| 7(x₁ + 6x₂) = 9(x₃ − x₂) | **YES** | distributes to 7x₁ + 42x₂ − 9x₃ + 9x₂ = 0 |
| (3x₁ − x₂)(5x₃ − x₄) = 9 | **NO** | product of variables (x₁x₃ appears) |

> **Watch Out:** Parentheses alone do not make an equation nonlinear — only if multiplication
> *between variables* results after distributing.

---

## Three Possible Solution Outcomes

1. **No solution** (inconsistent) — the equations contradict each other
2. **Exactly one solution** (unique) — all variables pinned down
3. **Infinitely many solutions** — at least one free variable

There is no such thing as "exactly two solutions" for a linear system.

---

## Critical Insight: Equation/Variable Count Does NOT Determine Solutions

**Exam Pattern:** The Week 1 quiz tested this concept on every problem. Memorize the correct
claims.

| Situation | What you can conclude |
|---|---|
| #equations = #variables | Could be 0, 1, or ∞ solutions — **nothing guaranteed** |
| #equations < #variables | Either **no solution** OR **infinitely many** (never unique) |
| #equations > #variables | Could be 0, 1, or ∞ solutions — **nothing guaranteed** |

> **Watch Out:** "Same number of equations as variables" does NOT mean a unique solution exists.
> The correct answer is always "could be 0, 1, or ∞."

> **Watch Out:** "Fewer equations than variables" means you CAN rule out a unique solution — but
> you cannot rule out no solution (e.g., two parallel planes have no intersection).

### Worked Example (from Week 1 Quiz)

```
−7x + 8y − 6z = 1
  x       + z = 1
```
2 equations, 3 variables → could have 0 or ∞ solutions.
The quiz says this system has ∞ solutions. Checking candidate (x=1, y=1, z=0):
- Eq 1: −7(1) + 8(1) − 6(0) = 1 ✓
- Eq 2: 1 + 0 = 1 ✓  → (1, 1, 0) is a solution.

Checking (x=1, y=7/4, z=1):
- Eq 2: 1 + 1 = 2 ≠ 1 ✗  → NOT a solution.

---

## How to Verify a Candidate Solution

1. Substitute the candidate values into **every** equation.
2. Check that both sides are equal for **all** equations.
3. If any single equation fails, the candidate is not a solution.

### Worked Example (Week 1 WebWork Problem 3)

System: 8x₁ + 3x₂ − 3x₃ = 21 and 3x₁ + 9x₂ − 4x₃ = −48.

Checking (6, −6, 3):
- 8(6) + 3(−6) − 3(3) = 48 − 18 − 9 = 21 ✓
- 3(6) + 9(−6) − 4(3) = 18 − 54 − 12 = −48 ✓  → **solution**

Checking (1, −4, −3):
- 8(1) + 3(−4) − 3(−3) = 8 − 12 + 9 = 5 ≠ 21 ✗  → **not a solution**
