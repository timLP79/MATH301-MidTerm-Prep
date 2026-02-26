<!--
PRINT INSTRUCTIONS: Set font to 9pt, margins to 0.5in all sides, two-sided.
This fits on front and back of one 8.5x11 sheet — allowed on both portions of the midterm.
Midterm Written: Tue 3/3 12:00-1:15pm | WeBWorK: Thu 3/5 12:00-1:15pm
-->

# MATH 301 Midterm Cheat Sheet

---

## LINEAR EQUATIONS

**Linear:** each variable appears only to the first power, not multiplied by another variable.
- YES: `3x+6y-4z=9`, `7(x1+6x2)=9(x3-x2)` (distributes to linear)
- NO: `2x^2+4x-7=y` (squared), `(3x1-x2)(5x3-x4)=9` (product of variables)

**Solution counts** — equation vs variable count tells you almost NOTHING:
- Same #eq as #var: could be 0, 1, or ∞ (NOT guaranteed 1)
- Fewer eq than var: either 0 or ∞ (no unique solution possible)
- More eq than var: could be 0, 1, or ∞ (NOT guaranteed no solution)
- Homogeneous (RHS=0): always ≥1 solution; fewer eq than var → guaranteed ∞

---

## AUGMENTED MATRICES & EROs

**Build [A|b]:** coefficients in variable order; missing variable → 0 entry.

**Valid EROs:** (1) swap rows, (2) multiply row by c≠0, (3) cRj + Ri → Ri
- INVALID: multiply by 0; replace Ri with combo not involving Ri; two ops simultaneously

**RREF reading:**
- Row `[0 0 ... 0 | c]` with c≠0 → NO solution
- All columns pivot, no `0=0` rows → UNIQUE solution
- Free column(s) + no contradiction → INFINITELY MANY (set free vars = s1, s2, ...)

---

## VECTORS & SUBSPACES

**3-condition subspace test** (all three must hold):
1. Contains zero vector
2. Closed under addition
3. Closed under scalar multiplication (including NEGATIVE scalars!)

**Classic failures:**
- Inequality constraint (a≤b): fails condition 3 (multiply by -1)
- Non-homogeneous constraint (b1=1): fails condition 1 (zero vector has b1=0)
- Homogeneous linear constraint (b3=b1+b2, b1=0, f(2)=0): always a subspace

**Zero vector in abstract spaces:** in P4, zero = the polynomial 0 (not a column vector)

**Parametric form:** x = p + s1*d1 + s2*d2 (particular + free params × direction vectors)
Direction vectors have 1 in the free-variable row, 0 in all other free-variable rows.

---

## INDEPENDENCE, SPAN, BASIS

**Dependent iff** nontrivial combo = 0; one vector is combo of others.

**Quick dependence tests (no row reduction):**
- Zero vector in set → dependent
- Two vectors scalar multiples → dependent
- More vectors than dimension of space → dependent (>n vectors in Rn: always dependent)

**Subset/superset rules:**
- Subset of independent = independent
- Superset of dependent = dependent

**Span:** b ∈ span{v1,...,vk} iff [v1|...|vk|b] is consistent.

**Basis = independent + spans.** Exactly n vectors in any basis for Rn.

**For n vectors in Rn:** independent ↔ spans ↔ basis (any one implies all three)

**Pivot column method:** row reduce B
- Rank = # pivots = dim(span of columns)
- No free columns → independent | Pivots in every row → spans Rm

**Representation:** Rep_B(v): solve [b1|b2|...|v] → coordinates w.r.t. basis B.

---

## FUNDAMENTAL SUBSPACES (for m×n matrix A)

| Subspace | Definition | Lives in | How to compute |
|---|---|---|---|
| col(A) | span of columns | R^m | Pivot cols of ORIGINAL A |
| row(A) | span of rows | R^n | Nonzero rows of RREF |
| null(A) | solutions to Ax=0 | R^n | Solve Ax=0, take direction vectors |

**Which space does a vector belong to?**
- Built as combo of COLUMNS of A → col(A)
- Built as combo of ROWS of A → row(A)
- Satisfies Ax=0 → null(A)

**Rank-nullity:** rank + nullity = **#COLUMNS** (not rows!)
- rank = dim(col) = dim(row)
- nullity = #cols - rank = dim(null)

**Worked examples:**
- 5×7 matrix, dim(row)=2: dim(col)=2, nullity=7-2=**5** (NOT 3)
- 9×11 matrix, nullity=7: rank=11-7=**4**, dim(row)=**4**
- 5×7 matrix, 2 zero rows in RREF: rank=3, nullity=7-3=**4**

---

## LINEAR TRANSFORMATIONS T: Rn → Rm

**Matrix:** m×n (m rows = codomain dim, n cols = domain dim)
**Linearity:** T(au+bv) = aT(u)+bT(v) → T of combo = combo of T's outputs
**T(0)=0 always.** If T(0)≠0, function is not linear.
**Domain:** Rn (inputs) | **Codomain:** Rm (outputs)
**Standard matrix:** A = [T(e1)|T(e2)|...|T(en)] (j-th column = T(j-th std basis vector)

**Computing T of a linear combination:**
If v = c1*u1 + c2*u2, then T(v) = c1*T(u1) + c2*T(u2) — no matrix needed.

**Exam example:** T([0,1,-9,8])=[1,-5], T([9,1,0,-2])=[5,-9]
[54,11,-45,28] = 5[0,1,-9,8]+6[9,1,0,-2] → T = 5[1,-5]+6[5,-9] = **[35,-79]**

**Kernel** = null(A) (subspace of domain) | **Image** = col(A) (subspace of codomain)

**Derivative as linear transformation:**
- d/dx: P3→P2 (reduces degree by 1)
- d²/dx²: P3→**P1** (reduces degree by 2; image is P1, not P2)

---

## TRANSFORMATION ARITHMETIC & ERO MATRICES

**Arithmetic:** (aS+bT)(v) = aS(v)+bT(v)
Exam: (-4S+3T)([0,1,-4,9]) = -4[3,1]+3[-6,4] = [-12,-4]+[-18,12] = **[-30,8]**

**ERO matrices** (left-multiply to perform ERO):

| ERO | Matrix form | Key entry |
|---|---|---|
| Ri ↔ Rj | Identity with rows i,j swapped | — |
| cRi → Ri | Identity with (i,i) = c | On diagonal |
| cRj+Ri → Ri | Identity with (i,j) = c | Row=destination, Col=source |

**ERO matrix examples:**
- `[0 0 1; 0 1 0; 1 0 0]` → R1↔R3 (rows 1 and 3 of I are swapped)
- `[1 0 0; 0 1 4; 0 0 1]` → 4R3+R2→R2 (4 in position (2,3): row 2 = dest, col 3 = source)
- TRAP: c in (i,j) means "cRj+Ri→Ri" — row of c is modified row, col of c is source row

**Invertible transformation T (all equivalent):**
- RREF(A) = I | rank(A) = n | null(A) = {0} | det(A) ≠ 0

**Invertibility rules:**
- T(v) = w  ↔  T⁻¹(w) = v (bidirectional)
- T(T⁻¹(v)) = v and T⁻¹(T(v)) = v (always)
- If T⁻¹(w)=v, then T(v)=w ← most useful inference direction
