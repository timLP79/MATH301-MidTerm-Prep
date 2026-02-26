# Week 5 — Fundamental Subspaces ⭐

This is the hardest topic on the midterm. Every concept here is tested in the quizzes.

---

## The Three Subspaces: Precise Definitions

For an m×n matrix A (m rows, n columns):

**Definition (Column Space):** col(A) = span of the columns of A
- Lives in **R^m** (vectors have m components — same as number of rows)
- col(A) = {Ax | x ∈ Rⁿ} = image of the transformation x ↦ Ax

**Definition (Row Space):** row(A) = span of the rows of A
- Lives in **R^n** (vectors have n components — same as number of columns)
- Equivalently: row(A) = col(Aᵀ)

**Definition (Null Space):** null(A) = {x ∈ Rⁿ | Ax = 0}
- Lives in **R^n** (same as number of columns)
- null(A) is a subspace of Rⁿ

> **Watch Out:** col(A) and null(A) live in DIFFERENT spaces even though both are "in Rⁿ" is wrong.
> - Columns of A have m components → col(A) ⊆ R^m
> - If Ax = 0, then x has n components → null(A) ⊆ Rⁿ

---

## How to Tell Which Subspace a Vector Belongs To

**The key question: How was the vector constructed from A?**

| If the vector was built as... | It belongs to... |
|---|---|
| A linear combination of COLUMNS of A | col(A) |
| A linear combination of ROWS of A | row(A) |
| A solution to Ax = 0 | null(A) |

### Week 5 Quiz Problem 1 — Identifying Subspaces

Matrix A is 4×4. Rows of A are: [4,0,−7,1], [−3,1,5,−9], [−6,−2,0,7], [−1,−8,−1,−4].
Columns of A are: col1=[4,−3,−6,−1]ᵀ, col2=[0,1,−2,−8]ᵀ, col3=[−7,5,0,−1]ᵀ, col4=[1,−9,7,−4]ᵀ.

**Vector 1:** [−14,38,34,−38]ᵀ = 6[−3,1,5,−9]ᵀ − 4[−1,−8,−1,−4]ᵀ
→ This is 6·(Row 2) − 4·(Row 4) → linear combination of **rows** → belongs to **row(A)**

**Vector 2:** [−21,20,−10,−43]ᵀ = 5[0,1,−2,−8]ᵀ + 3[−7,5,0,−1]ᵀ
→ This is 5·(Col 2) + 3·(Col 3) → linear combination of **columns** → belongs to **col(A)**

> **Watch Out:** Both vectors have 4 components, but A is 4×4 so both R^m and R^n equal R⁴.
> The distinction is HOW the vector was constructed, not just its size.

---

## Rank-Nullity Theorem

**Theorem:** For any m×n matrix A:

    rank(A) + nullity(A) = n    (number of COLUMNS)

where:
- rank(A) = dim(col(A)) = dim(row(A)) = number of pivot columns
- nullity(A) = dim(null(A)) = number of free variables = n − rank

> **Watch Out — Most Common Exam Mistake:** The right side is the number of **COLUMNS** (n),
> NOT the number of rows (m). Always count columns!

---

## Dimension Relationships

For an m×n matrix A with rank r:

| Subspace | Dimension | Lives in |
|---|---|---|
| col(A) | r = rank | R^m |
| row(A) | r = rank | R^n |
| null(A) | n − r = nullity | R^n |

**Always true:** dim(col(A)) = dim(row(A)) = rank(A)

### Week 5 Quiz Problem 3 — Using Rank-Nullity

A is a **5×7 matrix** with dim(row(A)) = 2.

- rank = dim(row) = **2**
- dim(col(A)) = rank = **2** (answer A)
- Rank-nullity: rank + nullity = **7** (# columns!) → nullity = 7 − 2 = **5** (answer C)

> **Watch Out:** The answer is NOT 3 (= 5 − 2 from rows). It is 7 − 2 = 5.

### Week 5 Quiz Problem 4 — Using Rank-Nullity

A is a **9×11 matrix** with dim(null(A)) = 7.

- nullity = 7 → rank = 11 − 7 = **4** (answer C for col space)
- dim(row(A)) = rank = **4** (answer A)

### Week 5 WebWork Problem 4 — RREF with Two Zero Rows

A is a **5×7 matrix** with RREF having **two rows of zeros**:
- Non-zero rows = 5 − 2 = 3 → rank = **3**
- dim(row) = dim(col) = **3**
- Rank-nullity: 3 + nullity = 7 → nullity = **4**

---

## How to Compute Each Subspace

### Computing col(A)

1. Row reduce A to RREF.
2. Identify the **pivot columns** (columns with leading 1s) in the RREF.
3. The corresponding columns of the **ORIGINAL matrix A** (NOT the RREF) form a basis for col(A).

> **Watch Out:** Use the ORIGINAL columns, not the RREF columns. RREF columns have the right
> pivot positions but different values.

### Computing row(A)

1. Row reduce A to RREF.
2. The **nonzero rows** of the RREF form a basis for row(A).

> **Note:** You CAN use the RREF rows (unlike col(A), where you must use the original columns).

### Computing null(A)

1. Solve Ax = 0 by row reducing [A | 0].
2. Express each basic variable in terms of the free variables.
3. Write the solution as a parametric vector form: x = s₁d₁ + s₂d₂ + ...
4. The direction vectors {d₁, d₂, ...} form a basis for null(A).

---

## Worked Example: All Three Subspaces (Week 5 WebWork Problem 6)

```
A = [ 1   4  -1   1 ]      RREF(A) = [ 1  0  7   3 ]
    [ 3  14  -1   6 ]                 [ 0  1  -2  -1/2]
    [ 2  12   2   8 ]                 [ 0  0  0   0 ]
```

**Pivot columns in RREF:** columns 1 and 2.

**col(A):** Take columns 1 and 2 of ORIGINAL A:
{[1,3,2]ᵀ, [4,14,12]ᵀ}

**row(A):** Take nonzero rows of RREF:
{[1, 4, −1, 1], [3, 14, −1, 6]}
(or equivalently the first two rows of A, since they are the source rows)

**null(A):** Free variables are x₃ and x₄. Solving:
```
x₁ = −7x₃ − 3x₄ (wait, check RREF above...)
Actually: x₁ + 7x₃ + ... = 0, x₂ − 2x₃ − (3/2)x₄ = 0
```
Null space basis: {[5, −1, 1, 0]ᵀ, [5, −3/2, 0, 1]ᵀ}

---

## Worked Example: RREF Given, All Subspaces (Week 5 WebWork Problem 5)

```
A =  [4  26  5]        RREF(A) = [1 0 0]
     [3   1  0]                  [0 1 0]
     [-5  1  3]                  [0 0 1]
     [3   5 -2]                  [0 0 0]
     [-5  8  4]                  [0 0 0]
```

All 3 columns are pivot columns (rank = 3).

**col(A):** All 3 original columns: {[4,3,−5,3,−5]ᵀ, [26,1,1,5,8]ᵀ, [5,0,3,−2,4]ᵀ}

**row(A):** Nonzero rows of RREF: {⟨1,0,0⟩, ⟨0,1,0⟩, ⟨0,0,1⟩}
(or equivalently rows 1−3 of A: {⟨4,26,5⟩, ⟨3,1,0⟩, ⟨−5,1,3⟩})

**null(A):** No free variables → null(A) = {0} (only the zero vector)

---

## Checking if a Vector is in col(A)

v is in col(A) ↔ the system Ax = v is **consistent** (has a solution).

**Procedure:** Row reduce [A | v]. If no contradiction row, v ∈ col(A).

(Week 5 WebWork Problem 2)

---

## Checking if a Vector is in null(A)

v is in null(A) ↔ Av = 0 (multiply and check).

No row reduction needed! Just compute Av directly.

(Week 5 Quiz Problem 2 — check each candidate by substituting into Ax = 0.)

---

## Summary of Key Numbers

Given an m×n matrix A with rank r:

```
rank(A)     = r = # pivot columns = dim(col(A)) = dim(row(A))
nullity(A)  = n - r                = dim(null(A))
              ^-- ALWAYS subtract from COLUMNS, not rows

dim(col(A)) = r   (col(A) ⊆ R^m)
dim(row(A)) = r   (row(A) ⊆ R^n)
dim(null(A))= n-r (null(A) ⊆ R^n)
```
