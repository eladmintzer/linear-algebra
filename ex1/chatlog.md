# Exercise 1 — AI Chat Log

This course encourages collaborating with an AI assistant. This file reconstructs the
prompts I (the student) gave and the assistant's key responses while building the
solution. It is a faithful summary rather than a byte-for-byte transcript; the raw
transcript can be pasted in for full fidelity if needed.

The work happened in two phases:

- **Phase A (earlier session):** brainstorming the approach, writing the spec
  (`docs/superpowers/specs/2026-06-01-ex1-linear-algebra-design.md`) and the
  implementation plan (`docs/superpowers/plans/2026-06-01-ex1-linear-algebra.md`),
  then doing Tasks 1–4: repo + GitHub setup, Python venv, the notebook skeleton, and
  Part 2 (the linear system). A handoff note was saved to
  `docs/superpowers/PROGRESS.md`.
- **Phase B (this session):** resuming from `PROGRESS.md`, finishing Parts 1, 3, 4,
  cleaning up the repo (dropping an HTML report, scrubbing history), responding to an
  (incorrect) grader review, and producing a static PDF for submission. Logged below.

---

## Phase B — resume session

### 1. Resume + email preference
**Me:** Read `docs/superpowers/PROGRESS.md` and continue Exercise 1 from where it left
off. Also: use my email `eladm1993@gmail.com` for everything, including git.

**Assistant:** Located the project, read the progress note (Tasks 1–4 done; Part 2
complete and approved). Saved the email preference and set the repo's local git author to
`eladm1993@gmail.com`.

### 2. Rewrite git history
**Me:** Force rewrite history.

**Assistant:** Ran `git filter-branch` to rewrite author **and** committer on all
commits to `eladmintzer <eladm1993@gmail.com>`, then force-pushed. Verified no commit in
history used the old email.

### 3. Re-explain Parts 2 and 3 algebraically
**Me:** Instead of going to Part 4, go back to Parts 2 and 3 and explain the algebraic
reasoning so I understand the logic.

**Assistant:** Walked through **Part 2** (matrix form `Ax = b`, why `det(A) = 4 ≠ 0`
guarantees a unique solution, and elimination giving `x = (1, 2, 3)`) and **Part 3**
(the two linearity conditions — additivity and homogeneity — proved entry-by-entry from
`(Ax)_i = Σ_j A_ij x_j`).

### 4. Explicit inverse
**Me:** For Part 2, also compute `A⁻¹` explicitly — I want to learn.

**Assistant:** Showed the cofactor/adjugate formula `A⁻¹ = adj(A)/det(A)`, computed it
by hand and in code, confirmed it matched `np.linalg.inv`, that `A A⁻¹ = I`, and that
`x = A⁻¹ b = (1, 2, 3)`. Explained why `np.linalg.solve` is still preferred (cost and
numerical stability).

### 5. Add to the notebook
**Me:** Put this in the notebook, and the other solution too.

**Assistant:** Added the explicit-inverse derivation (markdown + code + a "why we still
prefer solve" note) to Part 2, and built out **Part 3** (linearity proof, numeric demo,
and a parallelogram figure showing `A(u+v) = Au + Av`). Fixed an axis-limit bug so the
resultant arrow was visible. Re-ran the notebook; everything passed.

### 6. Step-by-step for Part 4
**Me:** Build Part 4, then: explain step by step how you got those numbers.

**Assistant:** Built **Part 4** — the derivative matrix `D` (superdiagonal 1, 2, 3, 4),
all five required items with assertions, and a figure of `q` vs `q' = Dp`. Then explained
each result arithmetically: `Dp` = row sums, `pᵀD` = column sums, `D²` = second-derivative
matrix, `pᵀDp = 10 = q'(1)`, and the general `n(n-1)/2` from summing `1 + … + (n-1)`.

### 7. How does word2vec work?
**Me:** Explain how word2vec actually works.

**Assistant:** Explained the distributional hypothesis; the skip-gram prediction game;
the softmax over **dot products** `P(o|c) ∝ exp(u_o · v_c)`; learning the vectors by
gradient descent; negative sampling as the speed trick; why this makes **cosine
distance** meaningful and why "king − man + woman ≈ queen" works; and how GloVe (the
model actually used) is count-based but yields the same kind of vectors.

### 8. Part 1 — word embeddings
**Me:** Continue to Part 1.

**Assistant:** Built **Part 1** — loaded GloVe `glove-wiki-gigaword-100` (dim 100),
computed the pairwise cosine-distance matrix for `[king, queen, dog, cat, coffee]`, a
heatmap, and a PCA-via-SVD 2-D scatter (no sklearn dependency). Results: closest =
`dog–cat` (0.120), also close `king–queen` (0.249), furthest = `queen–coffee` (0.834).

### 9. HTML report
**Me:** Carry on to the HTML report.

**Assistant:** Generated `ex1/report.html` from the executed notebook and injected a
styled header (links to the notebook locally and on GitHub) plus the visible footer.
Captured the export + injection in a reusable script `ex1/build_report.py` so the report
regenerates in one command.

### 10. Final run and push
**Me:** Jump to the final run and push.

**Assistant:** Did a clean end-to-end notebook run (all asserts pass), regenerated the
report, committed, and pushed to GitHub `main`. Confirmed the whole history is authored
by `eladm1993@gmail.com`.

### 11. This chat log
**Me:** Add Task 9 (the chat log) and push everything.

**Assistant:** Wrote this file and pushed.

### 12. Previewing the HTML from GitHub
**Me:** How do I preview the HTML from GitHub?

**Assistant:** Explained GitHub doesn't render `.html` files; the easiest preview is the
notebook itself (GitHub renders `.ipynb` natively), plus options like downloading the
file, raw.githack (public repos only), or GitHub Pages. The repo was then made public and
Pages was enabled, serving the report — but see the next steps, where this was reversed.

### 13. Drop the HTML, scrub the old email, rewrite history
**Me:** Never mind — drop the HTML. Also rewrite the chat log so the old email doesn't
appear there, and update history.

**Assistant:** Removed `ex1/report.html` and `ex1/build_report.py`, disabled GitHub Pages,
and edited `chatlog.md` to drop the old-email mention. Then ran `git filter-branch` to
purge those files **and** the old email string from every commit in history, garbage-
collected the backups, and force-pushed. Verified `git grep` across all of `origin/main`
returned zero matches for the old address and the HTML files.

### 14. Confirm the builder is gone
**Me:** Also remove `build_report.py`, it's useless.

**Assistant:** Confirmed it was already removed in the previous step — gone from the
working tree and from every commit on the remote.

### 15. Grader feedback claiming Parts 3 & 4 were missing
**Me:** [Pasted feedback from Gemini claiming Parts 3 and 4 were skipped / missing.]
Fix it.

**Assistant:** Investigated before changing anything and showed the feedback was **false**:
Parts 3 and 4 were fully present — in both the local copy and the published `origin/main`
— with the linearity conditions stated and proved, the derivative matrix built, all five
evaluations computed, and outputs present. Declined to "re-add" them (that would create
duplicates) and explained the likely cause: GitHub failing to fully render the large
notebook in-browser. Suggested a static export to bypass any viewer issue.

### 16. Export a static PDF
**Me:** Export a static asset — a PDF of the fully executed notebook to submit alongside
the `.ipynb`, so the grader sees the exact layout.

**Assistant:** Re-executed the notebook end-to-end, exported it to standalone HTML
(`nbconvert --embed-images`), then printed it to PDF with headless Chrome (waiting for
MathJax to typeset the equations). Produced `ex1/solution.pdf` (15 pages) and verified it
contains all four parts, the computed results, and properly rendered math (no raw-LaTeX
leakage). Committed and pushed it, and linked it from the README. (A second review chat
log from a separate verification session, `chatlog_review.md`, was also included.)

### 17. Update this log
**Me:** Update the log to the current state.

**Assistant:** Updated this `chatlog.md` to cover steps 12–17 and committed it.
