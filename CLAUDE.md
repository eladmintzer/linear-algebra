# Project conventions — Linear Algebra coursework

Read this before working on any exercise in this repo.

## Identity / git (IMPORTANT)

- Use **`eladm1993@gmail.com`** for ALL git config in this repo — both author and
  committer. Set it per-repo: `git config --local user.email eladm1993@gmail.com`.
- **Never** use any other personal email address anywhere: not in commits, not in
  author/committer fields, and **not in any committed file** (chat logs, HTML exports,
  docs). If a transcript or export contains an old address, redact it before committing.
- Before claiming a task done, `grep` the working tree AND history to confirm no
  disallowed email is present.

## Per-exercise submission workflow (`ex1/`, `ex2/`, …)

1. **Design first.** Brainstorm → spec in `docs/superpowers/specs/` → plan in
   `docs/superpowers/plans/`. Keep a `docs/superpowers/PROGRESS.md` handoff note.
2. **Build `exN/solution.ipynb`.** One section per part. Each part =
   explanatory markdown (LaTeX for math) + code that computes the answer +
   `assert` checks against hand-derived values + a matplotlib figure.
3. **Run clean end-to-end:**
   `.venv/bin/jupyter nbconvert --to notebook --execute --inplace exN/solution.ipynb`
4. **Static PDF (immutable submission asset).** GitHub renders `.ipynb` natively but
   often fails on large notebooks, so always also ship a PDF:
   - `.venv/bin/jupyter nbconvert --to html --embed-images --output /tmp/sol.html exN/solution.ipynb`
   - headless Chrome `--headless=new --print-to-pdf=exN/solution.pdf --virtual-time-budget=30000`
     (the budget lets MathJax typeset the equations). Verify the PDF has all parts and
     no raw-LaTeX leakage (`\begin{bmatrix}`, `$$`, `\frac`).
5. **Chat logs.** Write `exN/chatlog.md`; include any review logs.
6. **Conversation export (optional, Gemini-style).** Render the Claude session JSONL to a
   styled HTML with MathJax. **Redact personal emails before committing.**
7. **README links.** Notebook, PDF, chat logs, and (for HTML) a `raw.githack.com` live
   URL — GitHub does not render `.html` inline.
8. **Commit per part; push to GitHub.**

## Notes

- `.venv/` and `exN/*.png` are git-ignored; figures embed inline in notebook outputs.
- "Tests" here = inline `assert`s comparing computed results to hand-derived values.
