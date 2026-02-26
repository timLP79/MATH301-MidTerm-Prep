# Week 3 — Vectors and Subspaces

## Vector Arithmetic

**Definition:** A **vector** in Rⁿ is a column of n real numbers. Vectors are usually written as
column vectors.

**Addition:** Add component-wise: (u + v)ᵢ = uᵢ + vᵢ

**Scalar multiplication:** Multiply each component: (cv)ᵢ = cvᵢ

### Geometric Interpretation (in R² and R³)

To add vectors u and v geometrically: place the base of v at the tip of u; draw the arrow from
the base of u to the tip of v. (Week 3 Quiz answer B)

### Computation Example (Week 3 Quiz Problem 2)

    v = [9, 10, 4, 5]ᵀ   and   w = [9, −8, 8, 5]ᵀ

    −8v + 5w = −8[9,10,4,5]ᵀ + 5[9,−8,8,5]ᵀ
             = [−72,−80,−32,−40]ᵀ + [45,−40,40,25]ᵀ
             = [−27, −120, 8, −15]ᵀ   ← answer B

---

## Linear Combinations

**Definition:** A **linear combination** of vectors v₁, v₂, ..., vₖ is any vector of the form:

    c₁v₁ + c₂v₂ + ... + cₖvₖ

where c₁, ..., cₖ are scalars (real numbers).

---

## The Three-Way Equivalence

These three representations describe exactly the same mathematical object:

```
Linear System          Vector Equation              Augmented Matrix
a₁₁x₁ + a₁₂x₂ = b₁   x₁[a₁₁] + x₂[a₁₂] = [b₁]   [a₁₁ a₁₂ | b₁]
a₂₁x₁ + a₂₂x₂ = b₂      [a₂₁]      [a₂₂]   [b₂]   [a₂₁ a₂₂ | b₂]
```

In the vector equation form, the columns of A are the coefficient vectors.

### Converting: Vector Equation → Linear System (Week 3 WebWork Problem 4)

```
x₁[3, −7]ᵀ + x₂[−9, 4]ᵀ = [1, 5]ᵀ
```
converts to:
```
3x₁ − 9x₂ = 1
−7x₁ + 4x₂ = 5
```

### Converting: Linear System → Vector Equation (Week 3 Quiz Problem 4)

Each variable's coefficients form a column vector. The system
```
−5x₁ + 10x₃ − 8x₄ = 6
−9x₁ + x₂ + 3x₃ − 8x₄ = −8
...
```
becomes x₁[−5,−9,−10,−1]ᵀ + x₂[0,1,8,−10]ᵀ + x₃[10,3,0,9]ᵀ + x₄[−8,−8,−5,7]ᵀ = [6,−8,7,−5]ᵀ

> **Watch Out (Week 3 Quiz Problem 4):** The columns of the vector equation match the columns
> of the coefficient matrix — NOT the rows. The x₂ coefficient in equation 1 is 0 (the variable
> is missing), so the first component of the x₂ column vector is 0.

---

## Parametric Solution Form

When a system has infinitely many solutions, the general solution is written as:

    x = p + s₁d₁ + s₂d₂ + ...

where:
- **p** is any particular solution (often read from the RREF)
- **d₁, d₂, ...** are direction vectors (one per free variable)
- **s₁, s₂, ...** are the free parameters

### Example (Week 3 Quiz Problem 3)

```
x₁ = 15 + 16s + 14t
x₂ = t             ← free variable t
x₃ = −5 − 19s
x₄ = s             ← free variable s
x₅ = −27
```

Vector form:
```
[x₁]   [15]       [16]       [14]
[x₂]   [0 ]       [0 ]       [1 ]
[x₃] = [-5] + s * [-19] + t * [0 ]
[x₄]   [0 ]       [1 ]       [0 ]
[x₅]   [-27]      [0 ]       [0 ]
```

Note that the free-variable direction vectors have a 1 in the row corresponding to that
free variable and 0 in the other free-variable row.

---

## Zero Vector in Abstract Spaces

**Definition:** The **zero vector** in a vector space is the unique element 0 such that
v + 0 = v for every vector v.

- In Rⁿ: the zero vector is [0, 0, ..., 0]ᵀ
- In P₄ (polynomials of degree ≤ 4): the zero vector is the **zero polynomial** 0
  (the constant function that outputs 0 for every input)

> **Watch Out (Week 3 Quiz Problem 5):** The zero polynomial in P₄ is written as 0, not x⁴,
> and not the column vector [0,0,0,0]ᵀ (that would be in R⁴). The elements of P₄ are
> polynomials, so the zero element is a polynomial.

---

## Subspaces

**Definition:** A subset H of a vector space V is a **subspace** of V if it satisfies all three:
1. **Contains zero:** The zero vector of V is in H.
2. **Closed under addition:** If u ∈ H and v ∈ H, then u + v ∈ H.
3. **Closed under scalar multiplication:** If v ∈ H and c is any scalar, then cv ∈ H.

If ANY condition fails, H is not a subspace.

> **Note:** Conditions 2 and 3 can be combined: H is closed under linear combinations.

### Testing Subspaces — Worked Examples

**Example 1 (Week 3 WebWork Problem 7, V₁):**
V₁ = all vectors in R⁴ of the form [a, 3a+b, a+2b, 4a−6b]ᵀ

Test condition 1: Set a=0, b=0 → [0,0,0,0]ᵀ ∈ V₁. ✓
Test condition 2: Take two such vectors, add → still in form [a,3a+b,...]. ✓
Test condition 3: Multiply by scalar c → [ca, 3(ca)+cb,...] = same form. ✓
→ **V₁ is a subspace of R⁴.**

**Example 2 (Week 3 WebWork Problem 7, V₂):**
V₂ = vectors [a,b]ᵀ in R² with a ≤ b.

Test condition 1: [0,0]ᵀ, 0 ≤ 0. ✓
Test condition 2: [1,2]ᵀ and [3,4]ᵀ → sum is [4,6]ᵀ, 4 ≤ 6. ✓
Test condition 3: Take [1,2]ᵀ with c = −1 → [−1,−2]ᵀ, but −1 ≤ −2 is FALSE. ✗
→ **V₂ is NOT a subspace.** (Fails closure under scalar multiplication with negative scalars.)

> **Watch Out — Classic Failure:** A set defined by an inequality (a ≤ b, b₁ ≤ b₂, etc.)
> always fails closure under negative scalar multiplication.

**Subspaces of R³ (Week 3 WebWork Problem 8):**
- {b₁=0}: passes all 3 → subspace ✓
- {b₂=2b₃}: passes all 3 → subspace ✓
- {b₁≤b₂}: fails negative scalar → NOT a subspace ✗
- {b₁=1}: does not contain zero → NOT a subspace ✗ (zero vector has b₁=0≠1)
- {b₃=b₁+b₂}: linear constraint, passes all 3 → subspace ✓
- {b₁=b₂}: linear constraint, passes all 3 → subspace ✓

> **Pattern:** Any set defined by a **homogeneous linear constraint** (like b₃=b₁+b₂) is a
> subspace. Sets defined by inequalities or non-homogeneous equations (b₁=1) are not.

### Polynomial Subspaces (Week 3 WebWork Problem 9)

- Odd polynomials in P₃ (ax³ + bx): subspace — closed under addition and scalar mult, zero is 0. ✓
- f(1) ≥ 0 in P₃: NOT a subspace — fails scalar mult (multiply f by −1, then f(1) ≤ 0). ✗
- f(2) = 0 in P₃: subspace — homogeneous linear condition on the coefficients. ✓
