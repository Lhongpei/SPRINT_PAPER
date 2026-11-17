# SPRINT paper

Draft of **SPRINT: A GPU Interior-Point Method for Sum-of-Squares Relaxations of
Robot Trajectory Optimization**.

SPRINT is an interior-point solver for SOS relaxations of multistage polynomial
optimization. This paper focuses on robot trajectory problems.

| Path | Contents |
|---|---|
| `SPRINT_draft.pdf` | compiled draft; red `[TODO: ...]` markers are open items |
| `main.tex` | main file; replace `\drafttrue` with `\draftfalse` to hide TODO markers |
| `sections/` | one file per section, appendices A–C |
| `references.bib` | bibliography (entered from memory: verify DOIs and pages before submission) |
| `data/` | CSVs behind the plots and tables, with `PROVENANCE.txt` |

## Build

pdfLaTeX + BibTeX (Overleaf works as is). On Quest: `module load texlive/2026`.

```
pdflatex main && bibtex main && pdflatex main && pdflatex main
```

or `latexmk main`.

## Sources

- Theory and algorithm: adapted from the October 7, 2026 trajectory SOS note.
- PushBox vs MOSEK/BRISK at strict 1e-6 accuracy, and the 3D pendulum vs MOSEK:
  November 2026 result summaries (transcribed into `data/`).
- A100 phase breakdown and optimization rounds: solver benchmark reports, October 14–16, 2026.

## Open items

1. Authors, affiliations, venue and template.
2. BRISK: reference and a one-sentence description of its algorithm.
3. Instance sizes (m, number and orders of PSD blocks) for PushBox N=2..80 and the 3D
   pendulum; pendulum model description (meaning of "180°", relaxation order).
4. Confirm the strict Rule B (1e-6) metric definitions, in particular unaveraged complementarity.
5. PushBox: SPRINT's largest Rule B metric and iteration counts per N
   (the source summary was cut off).
6. What the SDP reduction step in the pendulum pipeline does, and whether it is exact.
7. Hardware details (altman CPU model and cores), MOSEK threads for PushBox, BRISK options.
8. Rerun full cuDSS against the latest stage backend in one allocation, with phase timings.
9. Optional: scaling run to N ≥ 300 recording Φ₁, Φ₂, B₂ and panel sizes.
10. Code availability statement.
