# Chat Log — Review of solution.ipynb against Exercise 1 requirements

This is a second chat log (the assignment-solving prompts were uploaded separately).
This conversation was a verification pass: checking that `solution.ipynb` satisfies
every requirement in `Exercise1_LinearAlgebra.pdf`.

---

**User:**
> go over solution.ipynb and see that it matches the requirements of
> Exercise1_LinearAlgebra.pdf. If not, ask me to approve the fixes.

**Assistant:**
Extracted the PDF requirements and read the notebook, then compared them
part-by-part. Found the notebook matches all four parts (and exceeds them):

- **Part 1 — Word Embeddings:** Loads GloVe vectors for king, queen, dog, cat,
  coffee; reports dimensionality (100); computes pairwise cosine distances;
  identifies closest pair (dog–cat, 0.120) and furthest (queen–coffee, 0.834).
- **Part 2 — Linear System:** Writes the system as A@x=b, checks invertibility
  via det(A)=4, solves x=(1,2,3). Also shows the explicit inverse via cofactors
  and Gaussian elimination.
- **Part 3 — Linearity:** States the two conditions (additivity + homogeneity),
  proves them entry-by-entry, verifies numerically.
- **Part 4 — Derivative Matrix:** Builds D, computes D@p, p.T@D, D@D, the scalar
  p.T@D@p=10 (= q'(1)), and the general case n(n−1)/2.

Conclusion: nothing to fix. Noted that the PDF also asks to submit chat logs /
prompts alongside the notebook.

---

**User:**
> nothing to fix? are you sure? already uploaded the prompt.

**Assistant:**
Re-verified by actually executing the self-contained code (Parts 2–4) rather than
trusting the saved outputs:

- det(A) = 4.0, x = [1. 2. 3.]
- General derivative result p.T @ D @ p = n(n−1)/2 confirmed for n = 2, 3, 5, 8
  (values 1, 3, 10, 28).

Still no correctness error found. Flagged three judgment calls a grader might
care about (not bugs):
1. Part 1 uses GloVe + cosine distance, whereas the PDF example mentions
   Word2Vec/gensim and just says "distances."
2. Part 1 re-running requires downloading GloVe (~128MB) + gensim; outputs are
   cached in the notebook.
3. The notebook goes beyond the spec (explicit inverse, Gaussian elimination,
   plots), which is a style call.

---

**User:**
> just download this conversation and upload as another chat log to the repo.

**Assistant:**
Saved this chat log to the repository as `chatlog_review.md`.
