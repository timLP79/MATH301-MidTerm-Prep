# Week 4 — Linear Independence, Span, and Basis

## Linear Independence and Dependence

**Definition:** A set of vectors {v₁, v₂, ..., vₖ} is **linearly independent** if the only solution
to c₁v₁ + c₂v₂ + ... + cₖvₖ = 0 is the trivial solution c₁ = c₂ = ... = cₖ = 0.

**Definition:** A set is **linearly dependent** if there exists a **nontrivial** solution (not all cᵢ = 0)
to c₁v₁ + c₂v₂ + ... + cₖvₖ = 0.

**Equivalent condition for dependence:** At least one vector in the set can be written as a
linear combination of the others.

> **Important distinction (Week 4 Quiz Problem 1):**
> - "If v₁ is a lin. combo of v₂ and v₃ → set is dependent" — TRUE (choice B)
> - "If v₁ is NOT a lin. combo of v₂ and v₃ → set is independent" — FALSE (choice C is false)
>   Because v₂ could still be a linear combo of v₁ and v₃.
>   Correct answer: ABD (not C).

---

## Quick Tests for Dependence (No Row Reduction Needed)

1. **Zero vector in set** → always dependent (c₁=1 for the zero vector, rest=0)
2. **Two vectors are scalar multiples** → dependent
3. **More vectors than the dimension** of the space → dependent
   (e.g., 4 vectors in R³ are always dependent)

### Week 4 WebWork Examples

**Problem 5:** {u = [4,−1,2]ᵀ, v = [0,0,0]ᵀ, w = [−8,4,−5]ᵀ}
→ v = [0,0,0]ᵀ (zero vector) → **linearly dependent** (answer E)

**Problem 4:** [−16, 11, 6]ᵀ = −3·[−2,1,1]ᵀ + 1·[−2,2,1]ᵀ + (−4)·[5,−3,−2]ᵀ
→ confirms the vector is a linear combination (coefficients: −3, 1, −4)

---

## Subset and Superset Rules

**Theorem:** If {v₁, ..., vₖ} is **linearly independent**, then every **subset** is also linearly independent.

**Theorem:** If {v₁, ..., vₖ} is **linearly dependent**, then every **superset** containing it is also linearly dependent.

### Week 4 WebWork Examples

**Problem 8:** {u₁, u₂, u₃, u₄} is linearly independent. Is {u₁, u₂, u₃} independent?
→ YES — always (answer A). It is a proper subset of an independent set.

**Problem 9:** {u₁, u₂, u₃} is linearly dependent. Is {u₁, u₂, u₃, u₄} independent?
→ NO — always dependent (answer D). Any superset of a dependent set is also dependent.

### Week 4 Quiz Problem 3 (All True)

- Independent → every subset independent → **True**
- Spans R³ → adding a 4th vector still spans R³ → **True**
- v₁ = combo of v₂, v₃, v₄ → does v₄ = combo of v₁, v₂, v₃? → **True** (rearrange equation)
- Basis of R³ → every vector in R³ is a combo of basis vectors → **True**

---

## Span

**Definition:** The **span** of {v₁, ..., vₖ} is the set of ALL linear combinations:

    span{v₁, ..., vₖ} = {c₁v₁ + ... + cₖvₖ | c₁,...,cₖ ∈ ℝ}

**Key fact:** b is in span{v₁, ..., vₖ} **if and only if** the system [v₁ | v₂ | ... | vₖ | b]
is **consistent** (has at least one solution).

### Week 4 WebWork Problem 2

b = [−2, −14, −10]ᵀ, v₁ = [−1,−4,−2]ᵀ, v₂ = [1,1,−1]ᵀ. Is b in span{v₁, v₂}?
Form augmented matrix [v₁ | v₂ | b] and row reduce → consistent with solution (4, 2).
→ b = 4v₁ + 2v₂, so **b is in span{v₁, v₂}**.

---

## Basis

**Definition:** A set {v₁, ..., vₖ} is a **basis** for a subspace H if:
1. The set is **linearly independent**, AND
2. The set **spans** H.

**Theorem:** Every basis for Rⁿ contains exactly **n** vectors.

**Equivalence for n vectors in Rⁿ:** If you have exactly n vectors in Rⁿ, the following are
all equivalent:
- The vectors are linearly independent
- The vectors span Rⁿ
- The vectors form a basis for Rⁿ
(Checking any one is sufficient to conclude all three.)

### Week 4 Quiz Problem 4 — Bases for R²

| Set | Basis? | Why |
|---|---|---|
| {[1,0]ᵀ, [0,1]ᵀ} | YES | Standard basis |
| {[−7,−5]ᵀ, [−21,−15]ᵀ} | NO | Second = 3× first (dependent) |
| {[−4,−2]ᵀ, [4,2]ᵀ} | NO | Second = −1× first (dependent) |
| {[7,1]ᵀ, [−4,−1]ᵀ} | YES | Not scalar multiples, 2 vectors in R² |
| {[8,−6]ᵀ, [16,−13]ᵀ} | YES | RREF has two pivots |

---

## Pivot Column Method: Testing Independence, Span, Basis

**Procedure:** Let B be the matrix whose columns are your vectors.

1. Row reduce B to RREF.
2. Count pivot columns = **rank(B)**.
3. **Independence:** No free variables ↔ all columns are pivot columns.
4. **Span Rⁿ:** Pivots in every row of B ↔ B has m pivot rows (where B is m×k).
5. **Basis:** Both conditions hold (rank = m = k, i.e., square matrix with full rank).

### Example (Week 4 WebWork Problems 6 and 7)

**B (2×4 matrix):**
```
[ 5  5  5  5 ]       RREF: [ 1  0 -1 -2 ]
[ -1 -2 -3 -4]             [ 0  1  2  3 ]
```
Pivot columns: 1 and 2. Rank = 2.
- Spans R²? Yes (pivots in both rows). ✓
- Independent? No (free columns 3 and 4 exist). ✗
- Basis? No (not independent). ✗

**B (3×3 matrix):**
```
[ 2  5  7  ]       RREF: [ 1  0  0 ]
[ 12 9  20 ]             [ 0  1  0 ]
[ -7 -5 -11]             [ 0  0  1 ]
```
RREF = I → rank 3, all columns pivot.
- Independent: YES | Spans R³: YES | Basis: YES

---

## Representing a Vector w.r.t. a Basis

**Definition:** If B = {b₁, ..., bₖ} is a basis for subspace H, and v ∈ H, then the
**representation of v w.r.t. B** is the unique vector [c₁, ..., cₖ] such that:

    v = c₁b₁ + c₂b₂ + ... + cₖbₖ

**How to find it:** Solve the system [b₁ | b₂ | ... | bₖ | v] via row reduction.

### Example (Week 4 WebWork Problem 14)

Basis B = {[1,1,1]ᵀ, [−1,1,3]ᵀ} for the solution set of x − 2y + z = 0.
Find Rep_B(v) for v = [5, −1, −7]ᵀ.

Solve [1  −1 | 5; 1  1 | −1; 1  3 | −7] → c₁ = 2, c₂ = −3.
Check: 2[1,1,1]ᵀ + (−3)[−1,1,3]ᵀ = [2+3, 2−3, 2−9]ᵀ = [5, −1, −7]ᵀ ✓

Rep_B(v) = [2, −3]ᵀ.

### Example (Week 4 WebWork Problem 10 — Polynomial Basis)

Vectors in P₂ represented w.r.t. B = {1, x, x²}: just read off coefficients.
- Rep_B(−15 − 15x − 12x²) = [−15, −15, −12]ᵀ

Then form matrix of these representations and row-reduce to test independence/span.

---

## When Exactly n Vectors in Rⁿ Form a Basis (Week 4 Quiz Problem 5)

Given: {[-4,4,-12]ᵀ, [-3,8,1]ᵀ, [-2,-1,-8]ᵀ} is a basis of R³. Then (without computation):

- **A: Adding a 4th vector → set is linearly dependent** ✓ (4 vectors in R³ always dependent)
- **B: Any vector in R³ is in the span** ✓ (basis spans R³)
- **C: Any vector can be written as a linear combination** ✓ (same as B)
- **D: First vector in span of other two** ✗ (independent set, no redundancy)
- **E: Two vectors span R³** ✗ (need at least 3 vectors to span R³)

> **Exam Pattern:** Given a basis of Rⁿ, you should immediately know: (1) adding any vector
> creates dependence, (2) every vector in Rⁿ is in the span, (3) any vector can be written
> as a linear combination, (4) removing any vector destroys the spanning property.
