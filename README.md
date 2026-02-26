# MATH 301 — Introduction to Linear Algebra

**BSU Spring 2026 | Section 001 | Tim Palacios (timpalacios)**

This repository contains course materials and midterm study notes for MATH 301 at Boise State
University. Source materials are the weekly quiz and WebWork PDFs from Weeks 1–7.

---

## Exam Dates

| Exam | Date | Time |
|---|---|---|
| **Midterm Written** | Tuesday, March 3, 2026 | 12:00–1:15 pm |
| **Midterm WeBWorK** | Thursday, March 5, 2026 | 12:00–1:15 pm |
| Final Exam (both portions) | Tuesday, May 5, 2026 | 12:00–2:00 pm |

**Allowed on both midterm portions:** One 8.5"×11" sheet of notes (two-sided) + scratch paper.
**WeBWorK portion also allows:** Python for calculations.
**Not allowed:** Calculators, any electronic devices (other than exam computer for WeBWorK).

---

## Repository Contents

### Course Materials (PDFs)

| File | Description |
|---|---|
| `Week 01 Quiz.pdf` | Linear equations, solution counts |
| `Week 01 WebWork.pdf` | Solving systems, verifying solutions |
| `Week 02 Quiz.pdf` | Augmented matrices, EROs, RREF |
| `Week 02 WebWork.pdf` | Row reduction, Gauss-Jordan elimination |
| `Week 03 Quiz.pdf` | Vectors, linear combinations, subspaces |
| `Week 03 WebWork.pdf` | Vector arithmetic, subspace tests |
| `Week 04 Quiz.pdf` | Independence, span, basis |
| `Week 04 WebWork.pdf` | Pivot method, representations w.r.t. basis |
| `Week 05 Quiz.pdf` | Fundamental subspaces, rank-nullity |
| `Week 05 WebWork.pdf` | col(A), row(A), null(A) computations |
| `Week 06 Quiz.pdf` | Linear transformations |
| `Week 07 Quiz.pdf` | ERO matrices, invertibility |
| `Exam info from Professor.pdf` | Official exam rules, dates, Respondus browser info |

### Study Notes (`study-notes/`)

Generated from the course materials above. See [`study-notes/`](study-notes/) for all files.

| File | Topic | Week |
|---|---|---|
| [`00-cheat-sheet.md`](study-notes/00-cheat-sheet.md) | **Print-ready exam sheet** (9pt, front+back) | All |
| [`01-linear-systems.md`](study-notes/01-linear-systems.md) | Linear equations; solution count rules | 1 |
| [`02-row-operations.md`](study-notes/02-row-operations.md) | Augmented matrices; valid EROs; RREF | 2 |
| [`03-vectors-subspaces.md`](study-notes/03-vectors-subspaces.md) | Vectors; linear combos; 3-condition subspace test | 3 |
| [`04-independence-span-basis.md`](study-notes/04-independence-span-basis.md) | Independence; span; basis; pivot method | 4 |
| [`05-fundamental-subspaces.md`](study-notes/05-fundamental-subspaces.md) | col(A), row(A), null(A); rank-nullity | 5 ⭐ |
| [`06-linear-transformations.md`](study-notes/06-linear-transformations.md) | T: Rⁿ→Rᵐ; linearity; kernel; image | 6 ⭐ |
| [`07-invertibility-ero-matrices.md`](study-notes/07-invertibility-ero-matrices.md) | ERO matrices; invertible transformations | 7 ⭐ |

⭐ = highest priority for midterm (Weeks 5–7 are hardest)

---

## Recommended Study Order

1. `05-fundamental-subspaces.md` — rank-nullity trap tested on every quiz
2. `06-linear-transformations.md` — computing T of a linear combo is the key skill
3. `07-invertibility-ero-matrices.md` — ERO matrix entry placement; invertibility logic
4. `04-independence-span-basis.md` — foundation for everything in weeks 5–7
5. `03-vectors-subspaces.md` — subspace 3-condition test
6. `01-linear-systems.md` + `02-row-operations.md` — earlier material, quick review
7. `00-cheat-sheet.md` — read the night before; **print and bring to the exam**

---

## Printing the Cheat Sheet

`study-notes/00-cheat-sheet.md` is designed to fit on **one sheet of paper** (front and back):

- Font: **9pt**
- Margins: **0.5 inches** all sides
- Layout: double-sided
- Render with any markdown viewer (VS Code preview, Typora, browser + markdown extension)

This sheet is allowed on both the Written and WeBWorK portions of the midterm.
