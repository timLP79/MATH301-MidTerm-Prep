# Week 2 — Row Operations and Solving Systems

## Building the Augmented Matrix

**Definition:** The **augmented matrix** [A | b] stores the coefficients and right-hand side
of a linear system. Rows = equations, columns = variables (in order), last column = RHS.

**Rules for construction:**
- Variables must appear in a consistent order across all equations.
- If a variable is missing from an equation, its coefficient is **0**.
- The augmented matrix includes a vertical bar before the RHS column.

### Example (Week 2 Quiz Problem 3)

```
−8x₁       − 7x₃ + 6x₄ = −1
  −x₁ + x₂ − 5x₃ − 7x₄ =  7
  −6x₁ + 2x₂      + 10x₄ = −10
   −x₁ + 5x₂ − 10x₃ + 9x₄ = −4
```

The second equation has x₂, so position (1,2) gets coefficient 1. The third has no x₃,
so position (2,3) = 0. The correct matrix (answer D):

```
[ −8   0  −7   6 | −1 ]
[ −1   1  −5  −7 |  7 ]
[ −6   2   0  10 | −10]
[ −1   5 −10   9 | −4 ]
```

> **Watch Out:** Answers A–C in the quiz shuffled the columns. Always use the variable order
> from the problem.

---

## Valid Elementary Row Operations (EROs)

**Definition:** An **elementary row operation** is one of:
1. **Swap** two rows: Rᵢ ↔ Rⱼ
2. **Scale** a row by a nonzero constant: cRᵢ → Rᵢ  (c ≠ 0)
3. **Replace** a row with itself plus a multiple of another row: cRⱼ + Rᵢ → Rᵢ

> **Watch Out:** Multiplying a row by **0** is NOT a valid ERO — it destroys information and
> the operation is not reversible. (Week 2 Quiz, choice C was invalid.)

> **Watch Out:** "Replacing Row 2 with 4(Row 1) + Row 3" is NOT valid — this replaces R2 with
> a combination that doesn't include R2 itself. Valid replacement must have the form
> c*(some other row) + Rᵢ → Rᵢ.

> **Watch Out:** You cannot perform two row operations simultaneously on the same row
> (e.g., adding R1 to R4 AND adding R4 to R1 at the same time is not valid).

### Valid EROs from Week 2 Quiz (answers ADFG):
- A: Adding Row 5 to Row 4 → valid (1·R5 + R4 → R4)
- D: Dividing Row 5 by 6 → valid (= multiplying by 1/6 ≠ 0)
- F: 3(Row 1) + Row 2 → Row 2 → valid replacement
- G: Switching Row 3 and Row 4 → valid swap

---

## Echelon Form vs. Reduced Row Echelon Form (RREF)

**Definition (Echelon Form):** A matrix is in **echelon form** if:
1. All zero rows are at the bottom.
2. Each row's leading entry (pivot) is strictly to the right of the pivot in the row above.
3. All entries below a pivot are zero.

**Definition (RREF):** A matrix is in **reduced row echelon form** if additionally:
4. Each pivot is 1.
5. All entries **above** a pivot are also zero.

```
Echelon form:           RREF:
[ 1  3 -3 -10 ]        [ 1  0  0 | -3 ]
[ 0  1  9   7 ]        [ 0  1  0 |  3 ]
[ 0  0 -26 -26]        [ 0  0  1 |  2 ]
```

---

## Reading Solutions from RREF

**Step 1:** Identify pivot columns (columns with a leading 1) and free columns.
**Step 2:** Variables in pivot columns = **basic variables** (determined).
**Step 3:** Variables in free columns = **free variables** (choose freely, set = parameter s₁, s₂, ...).

### Case 1: Contradiction row → No Solution

If RREF contains a row of the form [0  0  0 | c] with c ≠ 0:
```
[ 1  7 -3 | -9 ]
[ 0  1 -5 | -4 ]
[ 0  0  0 |  7 ]   ← 0 = 7, contradiction
```
→ **Zero solutions**

### Case 2: No free variables → Unique Solution

Every column except the RHS has a pivot. Read off values directly:
```
[ 1  0  0 | -3 ]     x = -3
[ 0  1  0 |  3 ]  →  y =  3
[ 0  0  1 |  2 ]     z =  2
```
→ **Exactly one solution**

### Case 3: Free variables → Infinitely Many Solutions

(Week 2 WebWork Problem 2)
```
[ 1  -8  3 | -3 ]
[ 0   1 -1 |  1 ]
[ 0   0  0 |  0 ]
```
x₃ is free → set x₃ = t. Then x₂ = 1 + t, x₁ = 5 + 5t.
Solution: x = (5 + 5t, 1 + t, t) for any t ∈ ℝ.

### Recognizing Free Variables from RREF (Week 2 Quiz Problem 4)

```
[ 1  -1   0  -2   0 | 17 ]
[ 0   0   1  15   0 |  9 ]
[ 0   0   0   0   1 | -8 ]
```
Variables: x₁, x₂, x₃, x₄, x₅
Pivot columns: 1 (x₁), 3 (x₃), 5 (x₅) → basic
Free columns: 2 (x₂), 4 (x₄) → free variables → infinitely many solutions

---

## Homogeneous Systems

**Definition:** A system is **homogeneous** if every RHS entry is 0: Ax = 0.

**Key facts:**
- Homogeneous systems are **always consistent** (x = 0 is always a solution).
- If the system has **fewer equations than variables**: infinitely many solutions (guaranteed,
  because RREF cannot have pivots in every column, so free variables must exist).
- If #equations ≥ #variables: either exactly one solution (the trivial x=0) or infinitely many.

> **Exam Pattern (Week 2 Quiz):**
> - 4 equations, 3 variables, homogeneous → 1 or ∞ solutions (correct answer A, not "no solution")
> - 2 equations, 3 variables, homogeneous → guaranteed ∞ solutions (correct answer D)

---

## Gauss-Jordan Elimination Procedure

1. Write the augmented matrix.
2. Use EROs to reach echelon form (forward elimination):
   - Get a leading 1 in the first pivot position.
   - Zero out everything below that pivot.
   - Move to the next row/column.
3. Back-substitute (backward elimination) to reach RREF:
   - Zero out everything above each pivot.
4. Read the solution.

### Example (Week 2 WebWork Problem 8)

```
x + 2y + 3z = 9
-3x - 2y + 4z = 11
-6x + 2y + 3z = 30
```

Augmented matrix → RREF:
```
[ 1  2  3 |  9 ]       [ 1  0  0 | -3 ]
[ -3 -2  4 | 11 ]  →   [ 0  1  0 |  3 ]
[ -6  2  3 | 30 ]       [ 0  0  1 |  2 ]
```
Solution: x = −3, y = 3, z = 2
