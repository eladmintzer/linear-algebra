# Exercise 1 — Progress / Handoff

**Last updated:** 2026-06-01
**Repo:** https://github.com/eladmintzer/linear-algebra (private)
**Spec:** `docs/superpowers/specs/2026-06-01-ex1-linear-algebra-design.md`
**Plan:** `docs/superpowers/plans/2026-06-01-ex1-linear-algebra.md`

## How to resume

Execute the plan inline, **Part by Part with an explanation + user approval at each
checkpoint** (user learns best from **static matplotlib figures** showing the geometry —
add one per part). Working style: explain concept → build cells → run → show figure →
wait for approval → next part.

## Done ✅

- **Task 1** — repo initialized, scaffolding (`.gitignore`, `README.md`,
  `requirements.txt`), GitHub repo created + pushed.
- **Task 2** — `.venv` created, deps installed (numpy 1.26.4, scipy 1.13.1,
  gensim 4.4.0), Jupyter kernel `la-ex1` registered.
- **Task 3** — `ex1/solution.ipynb` skeleton (title + 4 part headers).
- **Task 4 / Part 2 (Linear System)** — DONE + approved by user. Includes:
  solve cell (det=4, x=(1,2,3), verified), geometric figure (three planes meeting
  at the solution), and a Gaussian-elimination step-by-step figure. Later EXTENDED
  (user request) with a third route: explicit inverse via cofactors/adjugate
  (`A^-1 = adj(A)/det`, verified vs np.linalg.inv and A@A^-1=I) + a note comparing
  the three solution routes' cost/stability.
- **Task 6 / Part 3 (Linearity)** — DONE (built ahead of Part 4 at user request).
  Markdown proof of additivity & homogeneity (entry-by-entry), numeric demo on
  random data, and parallelogram figure `fig_part3_linearity.png` showing
  A(u+v)=Au+Av. Runs green. NOTE: committed locally, NOT yet pushed.

- **Task 5 / Part 4 (Derivative matrix)** — DONE. Built D (superdiagonal 1,2,3,4),
  all 5 items computed + asserted (Dp=[1,2,3,4,0]; pᵀD=[0,1,2,3,4]; D²; pᵀDp=10;
  general n(n-1)/2 for n=2,3,5,8). Figure `fig_part4_derivative.png`: q vs q'=Dp
  with q'(1)=pᵀDp=10 marked. Runs green. NOTE: committed locally, NOT yet pushed.

## Remaining ⏳ (in this order)

- **Task 7 / Part 1 (Word embeddings)** — model already cached locally; load
  glove-wiki-gigaword-100 (dim 100), 5 words, pairwise cosine-distance matrix +
  heatmap, closest/furthest. Figure: 2D (PCA) scatter of the 5 word vectors.
- **Task 8** — generate styled `ex1/report.html` (nbconvert → HTML), add header
  links (local notebook + GitHub blob URL
  `https://github.com/eladmintzer/linear-algebra/blob/main/ex1/solution.ipynb`)
  and the **visible joke footer** (no grade instruction — see spec).
- **Task 9** — write `ex1/chatlog.md` (reconstruct this session's prompts/responses).
- **Task 10** — final clean run, regenerate report, push.

## Environment notes (important if resuming on a different machine / Claude web)

- `.venv/` and downloaded models are **git-ignored** — not in the repo. To rebuild:
  `python3 -m venv .venv && .venv/bin/pip install -r requirements.txt`.
- The GloVe model is cached at `~/gensim-data/` on this Mac; a fresh machine will
  re-download (~128 MB) on first `api.load("glove-wiki-gigaword-100")`.
- Generated figures (`ex1/*.png`) are git-ignored; they're embedded inline in the
  notebook outputs and the exported HTML, so they regenerate on each notebook run.
- Run/execute notebook: `.venv/bin/jupyter nbconvert --to notebook --execute --inplace ex1/solution.ipynb`
- Notebook cells are inserted programmatically via `nbformat`; figures save with
  paths **relative to `ex1/`** (notebook cwd), e.g. `"fig_part2_planes.png"`.

## Verified answers (for reference)

- Part 2: x = (1, 2, 3); det(A) = 4.
- Part 4: D@p=[1,2,3,4,0]; p.T@D=[0,1,2,3,4]; D²=second-derivative matrix;
  p.T@D@p = 10; general n: pᵀDp = n(n−1)/2.
