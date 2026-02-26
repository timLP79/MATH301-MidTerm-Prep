# Week 7 — Invertibility and ERO Matrices ⭐

---

## Arithmetic of Linear Transformations

If S: Rⁿ → Rᵐ and T: Rⁿ → Rᵐ are linear transformations, and a, b are scalars, then:

    (aS + bT)(v) = aS(v) + bT(v)

The combined transformation aS + bT is itself a linear transformation.

### Week 7 Quiz Problem 1

S: R⁴ → R² and T: R⁴ → R² are linear with:
- S([0,1,−4,9]ᵀ) = [3,1]ᵀ
- T([0,1,−4,9]ᵀ) = [−6,4]ᵀ

Find (−4S + 3T)([0,1,−4,9]ᵀ):

    = −4·S([0,1,−4,9]ᵀ) + 3·T([0,1,−4,9]ᵀ)
    = −4·[3,1]ᵀ + 3·[−6,4]ᵀ
    = [−12,−4]ᵀ + [−18,12]ᵀ
    = [−30, 8]ᵀ   ← answer D

> **Watch Out:** Both S and T act on the SAME input vector. You do not need to decompose the
> input — just apply the arithmetic of transformations formula directly.

---

## ERO Matrices: Construction Rules

Every elementary row operation can be represented as left multiplication by an **ERO matrix**.
ERO matrices are derived from the identity matrix by performing the same ERO on the identity.

### Type 1 — Row Swap (Rᵢ ↔ Rⱼ)

**Construction:** Take the identity matrix and swap rows i and j.

**Example:** R₁ ↔ R₃ on a 3×3 system:
```
Original I:   ERO matrix E:
[ 1  0  0 ]   [ 0  0  1 ]
[ 0  1  0 ]   [ 0  1  0 ]
[ 0  0  1 ]   [ 1  0  0 ]
```
Left-multiplying any 3×n matrix by E swaps its rows 1 and 3.

**Week 7 Quiz Problem 2 (first part):**
```
[ 0  0  1 ]
[ 0  1  0 ]   → This is I with rows 1 and 3 swapped → performs R₁ ↔ R₃   Answer: C
[ 1  0  0 ]
```

### Type 2 — Row Replacement (cRⱼ + Rᵢ → Rᵢ)

**Construction:** Take the identity matrix and put c in position **(i, j)** — row i, column j.
(i is the row being modified; j is the source row being scaled)

**Example:** 4R₃ + R₂ → R₂ on a 3×3 system (c=4, i=2, j=3):
```
Original I:   ERO matrix E:
[ 1  0  0 ]   [ 1  0  0 ]
[ 0  1  0 ]   [ 0  1  4 ]   ← 4 goes in position (2,3)
[ 0  0  1 ]   [ 0  0  1 ]
```

**Week 7 Quiz Problem 2 (second part):**
```
[ 1  0  0 ]
[ 0  1  4 ]   → 4 is in position (2,3) → performs 4R₃ + R₂ → R₂   Answer: C
[ 0  0  1 ]
```

> **Watch Out:** The c goes in position (i, j), NOT (j, i). The MODIFIED row index is i (the ROW),
> and the SOURCE row index is j (the COLUMN). Getting this backwards is the most common error.

> **Watch Out:** The operation name is "cRⱼ + Rᵢ → Rᵢ" — the source row is Rⱼ, the destination
> is Rᵢ. The 4 in position (row 2, col 3) means: 4 × (row 3) gets added to row 2.

### Type 3 — Row Scaling (cRᵢ → Rᵢ)

**Construction:** Take the identity matrix and replace the (i,i) entry with c.

**Example:** 3R₂ → R₂:
```
[ 1  0  0 ]
[ 0  3  0 ]   ← 3 in position (2,2)
[ 0  0  1 ]
```

---

## Invertible Linear Transformations

**Definition:** A linear transformation T: Rⁿ → Rⁿ is **invertible** if there exists a linear
transformation T⁻¹: Rⁿ → Rⁿ such that:

    T(T⁻¹(v)) = v    for all v ∈ Rⁿ
    T⁻¹(T(v)) = v    for all v ∈ Rⁿ

**Key inference rule:** If T(v) = w, then T⁻¹(w) = v (and conversely).

### Week 7 Quiz Problem 3

T: R² → R² invertible with T([5,1]ᵀ) = [3,−3]ᵀ and T⁻¹([−5,−7]ᵀ) = [−2,4]ᵀ.

Which statements must be true?

**A:** T⁻¹([3,−3]ᵀ) = [5,1]ᵀ
→ We know T([5,1]ᵀ) = [3,−3]ᵀ. Apply T⁻¹ to both sides: T⁻¹(T([5,1]ᵀ)) = T⁻¹([3,−3]ᵀ)
→ [5,1]ᵀ = T⁻¹([3,−3]ᵀ). **TRUE** ✓

**B:** T(T⁻¹([−5,−7]ᵀ)) = [−5,−7]ᵀ
→ This is just the definition T(T⁻¹(v)) = v. **TRUE** ✓

**C:** T⁻¹([−2,4]ᵀ) = [−5,−7]ᵀ
→ We know T⁻¹([−5,−7]ᵀ) = [−2,4]ᵀ. This says the INPUT to T⁻¹ is [−2,4]ᵀ.
→ Does T⁻¹([−2,4]ᵀ) = [−5,−7]ᵀ? This would require T([−5,−7]ᵀ) = [−2,4]ᵀ — not given. **FALSE** ✗

**D:** T(T⁻¹([−5,−7]ᵀ)) = [3,−3]ᵀ
→ T(T⁻¹(v)) = v, not [3,−3]ᵀ. **FALSE** ✗

**E:** T([−2,4]ᵀ) = [−5,−7]ᵀ
→ We know T⁻¹([−5,−7]ᵀ) = [−2,4]ᵀ. Apply T to both sides: T(T⁻¹([−5,−7]ᵀ)) = T([−2,4]ᵀ)
→ [−5,−7]ᵀ = T([−2,4]ᵀ). **TRUE** ✓

Correct answers: **ABE**

> **Key rule:** T⁻¹(w) = v ↔ T(v) = w. These are exactly equivalent for invertible T.
> C is the trap: it reverses the direction incorrectly.

---

## Invertibility Equivalences

For a linear transformation T: Rⁿ → Rⁿ with matrix A (n×n), the following are all equivalent:

1. T is invertible
2. A is invertible (det(A) ≠ 0)
3. RREF(A) = Iₙ (the n×n identity matrix)
4. rank(A) = n (full rank)
5. null(A) = {0} (trivial null space)
6. The columns of A form a basis for Rⁿ
7. The system Ax = b has a unique solution for every b ∈ Rⁿ

> **Note:** If rank(A) < n, then T is NOT invertible, RREF(A) ≠ I, null(A) has nonzero vectors,
> and some systems Ax = b have no solution while others have infinitely many.

---

## Quick Reference: ERO Matrices

| ERO | ERO Matrix Form | Position of Off-Diagonal Entry |
|---|---|---|
| Rᵢ ↔ Rⱼ | I with rows i,j swapped | N/A (row swap) |
| cRᵢ → Rᵢ | I with (i,i) entry = c | On diagonal |
| cRⱼ + Rᵢ → Rᵢ | I with (i,j) entry = c | Position **(i,j)**: row=destination, col=source |

> **Memory trick for row replacement:** The c in position (i,j) means "add c times row j to row i."
> Row of the c = row being changed. Column of the c = row being added.
