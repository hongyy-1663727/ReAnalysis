# One-page syllabus: Willsey et al. computational reproduction and lab readiness

**Format:** 10 technical weeks plus a 1-week application capstone, approximately 6-8 hours per week

**Primary artifact:** `undergrad_replication_workbook.ipynb`

**Final goal:** confidently and honestly apply to the Willsey Lab or a related neural-engineering group with work the student can reproduce, explain, critique, and extend.

## Course purpose

Reconstruct selected analyses and figures from Willsey et al., *A high-performance brain-computer interface for finger decoding and quadcopter game control in an individual with paralysis*, using the released Dryad data, fixed GitHub source, and pretrained checkpoints. The student must distinguish computational reproduction from repeating the implanted-human experiment.

## What the student will master

- Cross-platform Conda or `venv` setup, Jupyter kernels, Git, hashes, and provenance.
- MATLAB-file inspection, multirate clock alignment, interpolation, trial segmentation, and indexing.
- Behavioral metrics, uncertainty, nested observations, and unit-of-analysis limitations.
- Participation-ratio dimensionality, pretrained PyTorch inference, and normalized cross-correlation.
- Directional SNR, channel-count scaling, PCA/regression, leakage-safe validation, and controlled RNG streams.
- Diagonal-covariance classification, confusion matrices, negative controls, and 3-D trajectory reconstruction.
- Clean reruns, discrepancy analysis, scientific limitations, and evidence-bounded communication.

## Weekly arc

| Week | Focus and principal evidence |
|---:|---|
| 1 | Environment, scope, preregistration, code/data provenance and hashes |
| 2 | MAT schema, clocks, interpolation, velocity, and synthetic alignment tests |
| 3 | Target changes, trial segmentation, traceable Fig. 1c reconstruction |
| 4 | Behavioral functions, block summaries, and Fig. 1e |
| 5 | Statistical tests, nesting, SEM, effect sizes, and block/day sensitivity |
| 6 | Participation-ratio dimensionality and Fig. 2a |
| 7 | Released decoder architecture, deterministic inference, and Fig. 2c-d |
| 8 | Directional SNR, train-only PCA, channel scaling, and Fig. 3b-c |
| 9 | Open-loop classification, shuffled-label control, and Fig. 4c flight path |
| 10 | Clean rerun, full-precision comparison, discrepancy report, and technical defense |
| 11 | Public-safe portfolio, research fit, application materials, professor questions, and mock interview |

## Working expectations

For each module, the student predicts before coding, specifies each function, tests a known-answer case, applies it to released data, compares only after the independent attempt, records discrepancies, and completes an oral checkpoint. AI and search are allowed. The student privately supplies the exported AI conversation and/or exact search terms plus an independent check, and must explain or modify retained code without AI. There is no point-based rubric; progress is established orally through demonstrated ownership.

## Final technical outputs

A clean executable notebook; tested implementations; environment and provenance records; selected reconstructions of Figs. 1c, 1e, 2a, 2c-d, 3b-c, Extended Data Fig. 1b-c, and Fig. 4c; full-precision JSON/CSV results; discrepancy log; short final report; and a technical oral defense with a live code modification.

## Application capstone

After the technical defense, the student prepares a public-safe repository README, one-page technical brief, five-slide talk, evidence-based CV entry, tailored inquiry draft, two-minute pitch, evidence-to-claim matrix, and one-page follow-up proposal. The student also drafts five questions for Dr. Willsey, documents what motivated each and why it is not already answered publicly, then selects one scientific and one research-practice or mentorship question with genuine follow-ups.

## Completion standard

The student can regenerate the work in a clean environment, trace every central number to source data and code, explain core functions and limitations, repair an unseen error, distinguish offline reproduction from experimental replication, identify a feasible next analysis, and defend every public or application claim. Completion does not imply Willsey Lab affiliation, endorsement, admission, or an available undergraduate position; current official lab and joining pages must be rechecked before contact.
