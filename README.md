# Claude's Cycles — Interactive Visualisation

An interactive 3D visualisation of the Hamiltonian cycle decomposition discovered by Claude Opus 4.6 and described in Don Knuth's note [*Claude's Cycles*](https://www-cs-faculty.stanford.edu/~knuth/papers/claude-cycles.pdf) (February 2026).

## The problem

Consider the digraph on m³ vertices ijk (0 ≤ i, j, k < m) where each vertex has three outgoing arcs: bump i, bump j, or bump k (mod m). Can the 3m³ arcs be decomposed into three directed Hamiltonian cycles?

## The construction

Claude found a rule that assigns, at each vertex, which coordinate to bump for each of the three cycles. For cycle 0 the rule depends on the fiber index s = (i + j + k) mod m:

| Condition | Action |
|---|---|
| s = 0, j = m−1 | bump i |
| s = 0, j ≠ m−1 | bump k |
| 0 < s < m−1, i = m−1 | bump k |
| 0 < s < m−1, i ≠ m−1 | bump j |
| s = m−1, i > 0 | bump j |
| s = m−1, i = 0 | bump k |

> **This construction produces a valid Hamiltonian cycle only when m is odd and m > 2.** The case m = 2 was proved impossible by Aubert and Schneider (1982). Even values of m > 2 remain an open problem — Claude found individual solutions for m = 4, 6, 8 by search but no general pattern.

## Live demo

👉 **[https://xgfd.github.io/knuth-claude-cycle-visualisation/](https://xgfd.github.io/knuth-claude-cycle-visualisation/)**

## The visualisation

Open `index.html` in a browser, or visit the live demo above. No build step or dependencies beyond a CDN link to Three.js.

- **Pick m** from the dropdown (3–11, odd and even)
- **Step** through one arc at a time, or **auto-run** the full cycle
- **Drag** to rotate the cube
- **Hover** over any vertex to see its label and fiber index
- Wrap-around edges (where a coordinate goes from m−1 back to 0) are drawn as **portal arrows** — an exit stub, a matching entry stub, and a dashed connector — so they don't overlap with the forward edges on the same axis
- The six rules highlight in real time as the cycle progresses
- For even m, a warning is displayed confirming the cycle is not Hamiltonian

## References

- D. E. Knuth, [*Claude's Cycles*](https://www-cs-faculty.stanford.edu/~knuth/papers/claude-cycles.pdf), 2026
- D. E. Knuth, [*Hamiltonian paths and cycles*](https://cs.stanford.edu/~knuth/fasc8a.ps.gz) (draft for TAOCP)
- J. Aubert and B. Schneider, *Graphes orientés indécomposables en circuits hamiltoniens*, JCTB 32 (1982), 347–349
