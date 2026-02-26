# Week 6 — Linear Transformations ⭐

---

## Definition and Notation

**Definition:** A function T: Rⁿ → Rᵐ is a **linear transformation** if it satisfies:
1. **Additivity:** T(u + v) = T(u) + T(v) for all u, v ∈ Rⁿ
2. **Homogeneity:** T(cu) = cT(u) for all u ∈ Rⁿ, c ∈ ℝ

These two conditions together give the **combined linearity** property:

    T(au + bv) = aT(u) + bT(v)   for all u, v, and scalars a, b

More generally: T(c₁u₁ + c₂u₂ + ... + cₖuₖ) = c₁T(u₁) + c₂T(u₂) + ... + cₖT(uₖ)

**Domain and Codomain:**
- The domain of T: Rⁿ → Rᵐ is Rⁿ (inputs are n-dimensional vectors)
- The codomain is Rᵐ (outputs are m-dimensional vectors)

> **Watch Out (Week 6 Quiz Problem 2):**
> - "T(v) = w makes sense, so w must be in Rⁿ" → **FALSE** — w must be in R^**m** (the codomain)
> - "T(v) = w makes sense, so v must be in Rᵐ" → **FALSE** — v must be in R^**n** (the domain)
> - The matrix of T has **m rows and n columns** → **TRUE** (m = codomain dimension, n = domain dimension)

---

## T(0) = 0 Always

**Theorem:** For any linear transformation T, T(0) = 0.

**Proof sketch:** T(0) = T(0·v) = 0·T(v) = 0 for any v.

> **Exam Pattern:** If T(v) ≠ 0 for some v, T might still be linear (only 0 maps to 0 necessarily).
> But if T(0) ≠ 0, then T is definitely NOT linear.

---

## Computing T of a Linear Combination from Known Outputs

If you know T on specific vectors, you can compute T on any linear combination of those vectors
**without knowing the matrix**.

**Method:** Express the input as a linear combination of the known vectors, then apply linearity.

### Week 6 Quiz Problem 1

T: R⁴ → R² with:
- T([0,1,−9,8]ᵀ) = [1,−5]ᵀ
- T([9,1,0,−2]ᵀ) = [5,−9]ᵀ

Find T([54,11,−45,28]ᵀ).

**Step 1:** Recognize [54,11,−45,28]ᵀ = 5·[0,1,−9,8]ᵀ + 6·[9,1,0,−2]ᵀ
(Check: 5·0 + 6·9 = 54 ✓, 5·1 + 6·1 = 11 ✓, 5·(−9) + 6·0 = −45 ✓, 5·8 + 6·(−2) = 28 ✓)

**Step 2:** Apply linearity:
T([54,11,−45,28]ᵀ) = 5·T([0,1,−9,8]ᵀ) + 6·T([9,1,0,−2]ᵀ)
                    = 5·[1,−5]ᵀ + 6·[5,−9]ᵀ
                    = [5,−25]ᵀ + [30,−54]ᵀ
                    = **[35, −79]ᵀ**   ← answer B

Find T([0,0,0,0]ᵀ):
→ T(0) = 0 → **[0, 0]ᵀ**   ← answer C

---

## The Matrix of a Linear Transformation

**Theorem:** Every linear transformation T: Rⁿ → Rᵐ can be represented as matrix multiplication:
T(x) = Ax for some m×n matrix A.

**How to find A:** The j-th column of A equals T(eⱼ), where eⱼ is the j-th standard basis vector.

    A = [T(e₁) | T(e₂) | ... | T(eₙ)]

> **Exam Pattern (Week 6 Quiz Problem 2):** "If we know T on all standard basis vectors of Rⁿ,
> we can figure out T on any vector" → **TRUE** (each column of the matrix comes from T(eⱼ))

**Why this works:** Any x = x₁e₁ + x₂e₂ + ... + xₙeₙ, so by linearity:
T(x) = x₁T(e₁) + x₂T(e₂) + ... + xₙT(eₙ) = A·x

---

## Kernel and Image

**Definition:** The **kernel** of T (= null space of A) is:
    ker(T) = {v ∈ Rⁿ | T(v) = 0}  = null(A)

**Definition:** The **image** of T (= column space of A) is:
    im(T) = {T(v) | v ∈ Rⁿ} = col(A)

- ker(T) is a subspace of the **domain** (Rⁿ)
- im(T) is a subspace of the **codomain** (Rᵐ)

---

## Derivative as a Linear Transformation

**Theorem:** The derivative d/dx: P₃ → P₂ is a linear transformation.

d/dx(a₀ + a₁x + a₂x² + a₃x³) = a₁ + 2a₂x + 3a₃x²

**Why linear:**
- d/dx(f + g) = f' + g' ✓ (sum rule)
- d/dx(cf) = cf' ✓ (constant multiple rule)

**Second derivative d²/dx²: P₃ → P₁** (Week 6 Quiz Problem 3):
d²/dx²(a₀ + a₁x + a₂x² + a₃x³) = 2a₂ + 6a₃x

The image (range) of d²/dx² is all polynomials of degree ≤ 1, i.e., **P₁**.
Answer: A (P₁, not P₂ or P₀)

**Reasoning:** Taking the second derivative reduces degree by 2.
- Starting space: P₃ (degree ≤ 3)
- After one derivative: P₂ (degree ≤ 2)
- After two derivatives: **P₁** (degree ≤ 1)

---

## Summary: Key Facts about T: Rⁿ → Rᵐ

```
Domain:          R^n       (inputs live here)
Codomain:        R^m       (outputs live here)
Matrix A:        m × n     (m rows = codomain dim, n cols = domain dim)
T(0) = 0:        ALWAYS
ker(T):          subspace of R^n  (= null(A))
im(T):           subspace of R^m  (= col(A))
```

**Linearity combo rule:** T(c₁v₁ + c₂v₂ + ... + cₖvₖ) = c₁T(v₁) + ... + cₖT(vₖ)

This is the most-tested skill: given T on a few vectors, find T on a linear combination.

---

## Worked Practice

**Setup:** T: R³ → R² is linear, with T(e₁) = [1,2]ᵀ, T(e₂) = [0,−1]ᵀ, T(e₃) = [3,4]ᵀ.

**Find the matrix A:**
```
A = [T(e₁) | T(e₂) | T(e₃)] = [ 1   0   3 ]
                                [ 2  -1   4 ]
```

**Compute T([2, −1, 3]ᵀ):**
Method 1 (matrix mult): A·[2,−1,3]ᵀ = [1·2 + 0·(−1) + 3·3, 2·2 + (−1)·(−1) + 4·3]ᵀ = [11, 17]ᵀ
Method 2 (linearity): 2T(e₁) − T(e₂) + 3T(e₃) = 2[1,2]ᵀ − [0,−1]ᵀ + 3[3,4]ᵀ = [11,17]ᵀ ✓
