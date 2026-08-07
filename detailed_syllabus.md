# Detailed syllabus: computational reproduction of a finger BCI study

## Course title

**Guided Computational Reproduction of Willsey et al., “A high-performance brain–computer interface for finger decoding and quadcopter game control in an individual with paralysis”**

Article: *Nature Medicine* 31, 96–104 (2025)

DOI: `10.1038/s41591-024-03341-8`

Format: ten-week technical practicum plus a one-week application capstone

Expected effort: approximately 6–8 hours per week

Primary working document: `undergrad_replication_workbook.ipynb`

## Course description

This course guides one undergraduate student through a computational reproduction of selected quantitative results from Willsey et al. The student will work from the published article, public Dryad data, and released source code to reconstruct the path from raw files to scientific claims. The work begins with an independently designed analysis and only later uses the authors’ implementation as an auditable reference.

The course is not a code-running exercise. Each result must be supported by an identified data source, a stated analytical choice, tested functions, full-precision numerical output, and a scientific interpretation. A visually similar figure is useful evidence, but it is not sufficient by itself. The student must be able to explain the purpose, inputs, outputs, assumptions, units, and failure modes of any function used.

The professional capstone turns verified technical work into an ethical application portfolio for the Willsey Laboratory for Brain-Computer Interfaces or a related neural-engineering group. The student will produce a public-safe repository, technical brief, research talk, CV entry, inquiry draft, two-minute pitch, evidence-to-claim map, and follow-up proposal. These materials may describe only work the student genuinely completed and can defend orally; completing the practicum does not imply affiliation with, endorsement by, or an available position in the Willsey Lab.

AI assistants and search engines are permitted. Their use is treated like any other external source: the student records the exported AI conversation and/or exact search terms, tests suggestions independently, and remains responsible for every retained line of code and every conclusion. Understanding is evaluated through weekly oral check-ins and a final oral defense rather than a point-based rubric.

## Central course question

**How much of the paper’s data-to-figure pipeline can be reproduced from the released artifacts, how closely do the results agree, and what scientific conclusions remain outside the scope of that reproduction?**

## Final professional goal

By the end of Module 11, the student should be able to apply confidently to the Willsey Lab or a related group with a portfolio whose technical claims are specific, reproducible, current-source informed, and orally defensible. Confidence here means knowing both what the student can contribute and what training is still needed—not assuming that a position is available or that polished materials guarantee selection.

## Learning objectives

By the end of the course, the student should be able to:

1. Distinguish computational reproduction, reanalysis, and independent experimental replication.
2. Create and document an isolated, OS-neutral Python environment and connect it to the correct Jupyter kernel.
3. Establish provenance for source code, data, software versions, and analytical decisions.
4. Inspect unfamiliar MATLAB data files and construct a data dictionary containing shapes, data types, units, and clock fields.
5. Align streams sampled on different clocks without silent extrapolation or endpoint errors.
6. Translate task definitions into explicit trial-segmentation and behavioral-metric algorithms.
7. Implement and test participation ratio, lagged normalized correlation, directional SNR, and a diagonal-covariance classifier.
8. Load released PyTorch checkpoints safely and trace tensor shapes through deterministic inference.
9. Reconstruct the requested manuscript and Extended Data plots in Python and compare numerical results at full precision.
10. Recognize data leakage, pseudoreplication, inappropriate units of analysis, unstable random procedures, and visually concealed numerical errors.
11. Classify discrepancies as numerical, code-related, data-related, or presentational and assess their scientific impact.
12. Defend an analysis orally, predict the effect of a code mutation before running it, and modify unfamiliar code without relying on AI in real time.
13. Explain how completed artifacts connect to current implantable-BCI, neural-decoding, multi-effector-control, and neural-stability research using current official sources.
14. Translate technical evidence into a concise public portfolio, CV entry, research-fit statement, and spoken project pitch without inflating the scientific scope.
15. Propose a feasible next analysis with an explicit hypothesis, unit of analysis, leakage controls, validation plan, and limitation.

## Prerequisites

The student should enter with:

- introductory Python experience, including functions, exceptions, loops, arrays, file paths, and plotting;
- familiarity with NumPy-style array indexing and the idea of vectorization;
- introductory probability and statistics, including means, variance, standard error, correlation, hypothesis tests, and cross-validation;
- introductory linear algebra, including vectors, projections, eigenvalues, covariance, and principal component analysis;
- willingness to use Git for small, frequent commits; and
- willingness to read scientific Methods and source code closely.

Prior experience with PyTorch, MATLAB, neural data, or brain–computer interfaces is helpful but not required. MATLAB is not required: the student will read selected MATLAB routines and reproduce their relevant behavior in Python.

If the student has not used Git, Python environments, or Jupyter kernels before, the instructor should provide a short orientation but should not create the environment or repair the notebook on the student’s behalf.

## Required materials

### Scientific and computational sources

- Willsey et al., *A high-performance brain–computer interface for finger decoding and quadcopter game control in an individual with paralysis*.
- Dryad dataset DOI `10.5061/dryad.1jwstqk4f`, version 3.
- Authors’ GitHub repository `WillseyBCILab/BCI_Finger_Decoding_Quadcopter`, fixed at commit `addd54935c84db611d2e181b3f61d9c60aa9c412`.
- The Dryad data README and the repository README.
- The student workbook, `undergrad_replication_workbook.ipynb`.
- The student application guide, `student_capstone.md`.
- `environment.yml` for Conda and `requirements.txt` for `venv`/pip.

### Computing resources

The student needs a computer capable of running Python 3.9, Jupyter, NumPy, SciPy, pandas, Matplotlib, scikit-learn, and CPU PyTorch. The reduced analyses should run on an ordinary contemporary laptop or desktop. A GPU is not required. The complete channel-count dSNR sweep performs tens of thousands of fits and may require roughly 75 minutes on a CPU; it should be run only after the reduced version passes all tests.

The project should have enough free space for the 192,043,671-byte extracted source dataset (about 192 MB decimal or 183 MiB), the authors’ repository, environments, generated figures, cached numerical outputs, and notebook checkpoints. Data should be downloaded once, verified, and then treated as read-only.

## Project organization

Use a project-relative layout rather than fixed machine-specific paths:

```text
project-root/
├── undergrad_replication_workbook.ipynb
├── environment.yml
├── requirements.txt
├── work/
│   ├── code_audit/          # fixed authors' repository checkout
│   └── replication/
│       └── Data/            # extracted Dryad Data directory
├── outputs/
│   └── student_replication/ # figures, tables, JSON/CSV and logs
└── portfolio/
    ├── public/              # README, brief, selected figures/results and slides
    └── private_application/ # CV, inquiry, fit statement and interview notes
```

The exact outer directory may differ across computers. Notebook code must locate project resources from a project root or a documented override. It must not assume a drive letter, home directory, slash direction, or operating system.

## Environment setup expectations

Creating the computing environment is part of the course. The student chooses either Conda or Python `venv`; neither route is preferred solely because of the student’s operating system.

The setup record must contain:

1. the chosen environment manager and reason for choosing it;
2. every environment-creation, activation, installation, kernel-registration, and notebook-launch command;
3. the Python version requested and the version actually resolved;
4. `sys.executable`, `sys.version`, `platform.platform()`, and key package versions printed from inside the notebook;
5. successful `python -m pip check` output;
6. confirmation that the selected Jupyter kernel points inside the new environment rather than a system interpreter or Conda base environment; and
7. every failed installation and any instructor-approved compatibility substitution.

Exact historical package pins should be attempted because numerical routines and random partitions can change across versions. If a historical build is unavailable for the student’s hardware or operating system, the student should preserve the error, explain the incompatibility, obtain approval for a substitution, and test whether the substitution changes any reported result. A silent upgrade is not acceptable.

At the end of the course, the student must demonstrate a clean-kernel run in the documented environment. Ideally, a second person should recreate the environment from the supplied specification in a fresh directory.

## Working method

Each module follows the same research cycle:

1. **Read:** identify the scientific question, relevant figure, and Methods description.
2. **Predict:** answer the before-coding questions and state expected behavior before viewing reference implementations or numerical answer keys.
3. **Specify:** write the function’s purpose, inputs, outputs, shapes, data types, units, assumptions, invariants, and failure behavior.
4. **Implement:** write the smallest clear implementation that satisfies the specification.
5. **Test:** begin with a synthetic case with a known answer, then add edge cases and an unseen instructor case.
6. **Apply:** run the function on released data and save full-precision values separately from the plotted values.
7. **Compare:** compare with the paper and released code only after the independent attempt is committed.
8. **Interpret:** explain what agrees, what differs, and whether the difference affects a scientific claim.
9. **Record assistance:** attach the lightweight AI/search record described below.
10. **Defend:** complete the week’s oral check-in and any live test or code mutation.

The student should make at least one coherent Git commit for each module. Commits should separate predictions or tests from later reference-guided revisions when practical. Source data must remain unchanged; generated artifacts belong in `outputs/student_replication`.

## AI and search policy

AI use is permitted for explanation, syntax, debugging, test ideas, and code review. Search engines and online documentation are also permitted. The goal is not to prevent assistance but to preserve a trace of what information entered the analysis and to determine whether the student evaluated it.

At the end of each module, the student supplies only the following lightweight record:

- If AI was used, paste or attach the exported conversation in its original prompt-and-response order. If no AI was used, write `AI not used.`
- If a search engine was used, list the exact search terms in the order used. Links may be added, but a prose search diary is not required. If no search engine was used, write `Search engine not used.`
- Name the notebook step or function affected.
- Point to one independent check, such as a synthetic test cell, official documentation, a manually derived value, a source-code line, or a second implementation.

The student may redact passwords, tokens, private information, or unrelated personal material, marking each removal as `[REDACTED]`. The student should never submit private credentials or restricted data to an AI service.

Exported AI conversations are private course evidence by default and should not automatically be published with the portfolio. A public `AI_USE.md` may summarize which kinds of assistance were used, which parts of the project they affected, and how suggestions were independently checked, without exposing personal transcripts.

Pasting a conversation is disclosure, not validation. The student remains responsible for testing the suggestion, recognizing incorrect or overconfident answers, explaining every retained implementation, and changing it during an oral check. A correct plot produced by code the student cannot explain does not establish completion of the module.

## Evaluation through oral examination

There is no point-based assessment rubric. Progress is evaluated through the notebook artifacts, weekly oral conversations, and a final oral defense.

### Weekly oral check-ins

Each weekly check-in should take approximately 30 minutes, with up to 45 minutes for the decoder, dSNR, final-validation, and application modules. The instructor will normally:

1. inspect the week’s committed notebook, output files, tests, and AI/search attachment;
2. choose one function or analytical choice and ask the student to explain its purpose, shapes, units, assumptions, and likely failure mode;
3. introduce an unseen synthetic input or a small code mutation;
4. ask the student to predict the direction and scope of the effect before executing code; and
5. ask the student to interpret one result without reading prepared notebook prose.

A module is ready to close when the student can reproduce its artifacts, explain the analysis in their own words, pass an unseen check, and repair or reject a flawed modification. If not, the student revises the notebook and repeats the relevant portion of the oral check. The purpose is mastery, not a one-attempt performance.

### Final oral defense

The final defense should take approximately 20 minutes. The instructor selects one data-loading or alignment function and one analytical function at random. The student must:

- explain both functions’ purpose, shapes, units, assumptions, complexity, and failure behavior;
- predict and test a small modification;
- interpret one reproduced figure from the visual alone;
- explain at least one discrepancy and its scientific impact;
- distinguish a numerical match from independent scientific confirmation; and
- name at least one paper claim that cannot be established from the released artifacts.

After the technical defense, the student completes a separate 30-minute application-readiness mock interview. The student gives a two-minute pitch, connects a proposed next analysis to a currently verified lab theme, answers technical/research-fit/human-data questions, identifies a real skills gap, and repairs one overclaimed application sentence.

## Reproducibility standards

All submitted analyses are expected to satisfy the following standards:

- Code and data are identified by immutable references: Git commit, Dryad version, file inventory, and hashes.
- The environment is isolated, documented, and connected to the displayed notebook kernel.
- Paths are project-relative and work on different operating systems.
- Raw input data remain unchanged.
- Every core function has a purpose statement, input/output contract, known-answer test, and defined failure behavior.
- Shapes, units, monotonic clocks, array finiteness, channel counts, and index conventions are asserted rather than assumed.
- Random choices use explicit, recorded seeds and passed random-number generators.
- Preprocessing learned from data, including PCA and regression parameters, is fitted only on training folds.
- Full-precision results are saved in JSON or CSV; rounding occurs only for presentation.
- Figure files are generated programmatically and traceable to numerical outputs.
- Numerical tolerances are declared before consulting full-precision reference answers.
- Discrepancies are retained and classified rather than hidden by manual editing.
- The completed notebook runs from top to bottom from a clean kernel and regenerates outputs from an empty output directory.

## Eleven-week schedule

### Week 1 — Environment, scope, preregistration, and provenance

**Notebook coverage:** Setup and Modules 0–1.

**Read before coding**

- Paper abstract, Figs. 1–4 and their captions, Methods headings, Data availability, and Code availability.
- Dryad and repository README files.
- Official setup documentation for the student’s chosen environment manager, pip, and Jupyter kernel registration.
- A short Git reference covering commits, commit hashes, and ignored/generated files.

**Concepts**

- Computational reproduction versus experimental replication.
- Claims, observational units, nesting, and preregistration.
- Environment isolation, code provenance, data provenance, and file integrity.
- Streaming hashes and why a digest differs from a filename or file count.

**Practical work**

- Create and activate the isolated environment and register its Jupyter kernel.
- Record the environment audit from inside the notebook.
- Read the paper without opening the authors’ analysis function bodies.
- Write a claim map identifying the input data and observational unit behind each main quantitative result.
- Fill the preregistration table with statistics, tolerances, and failure criteria.
- Implement and test `sha256_file` using chunked reads.
- Inventory the release by relative path, suffix, size, and SHA-256 digest.
- Record the article DOI, Dryad version, repository URL, and exact Git commit.

**Evidence due**

- Environment command log and notebook environment audit.
- Initial claim map and completed preregistration table.
- Data/code provenance record and hash manifest.
- Passing known-digest and altered-byte tests.
- Module 0 and Module 1 AI/search attachments.
- A Git commit preserving the independent predictions.

**Oral check-in prompts**

- What can this project reproduce, and what would require a new experiment?
- How do `sys.executable` and the notebook kernel identify the environment actually in use?
- What fact does a SHA-256 digest establish, and what does it not establish?
- Why can two analyses produce the same rounded plot despite different data bytes?
- What is the observational unit behind one selected paper claim?

### Week 2 — MAT schema, clocks, interpolation, and velocity

**Notebook coverage:** Module 2.

**Read before coding**

- Paper Methods: “Finger tasks,” “Closed-loop decoding software,” and “Offline analyses.”
- Dryad README variable descriptions.
- Official SciPy documentation for `loadmat` and the chosen interpolation routine.
- The authors’ relevant loading code only after the student commits a schema and interpolation design.

**Concepts**

- MATLAB structures loaded into Python.
- Time-by-feature conventions and transposed-array hazards.
- Multiple Redis clocks, overlap intervals, interpolation, and extrapolation.
- Position, finite differences, milliseconds, seconds, and velocity units.
- Constant-channel behavior during standardization.

**Practical work**

- Implement `mat_manifest` and build a data dictionary for a representative closed-loop block.
- Identify estimated position, target position, neural features, and clock arrays.
- Draw every relevant input/output shape and annotate units.
- Implement `align_stream_to_clock` with explicit monotonicity, shape, and range validation.
- Test a linear ramp, unsorted time, duplicate time, no overlap, out-of-range destinations, and transposed values.
- Align task variables onto the retained neural timestamps.
- Compute velocity with an explicit millisecond-to-second conversion and inspect the median bin interval.
- Identify and explain the released `binTrial` interpolation defect without silently reproducing it.

**Evidence due**

- MAT data dictionary and representative shapes/dtypes.
- Clock-overlap diagram or table.
- Tested alignment function and velocity-unit derivation.
- At least one diagnostic plot made before a manuscript-style plot.
- Module 2 AI/search attachment.

**Oral check-in prompts**

- Why align task streams to the neural clock rather than the reverse?
- What exactly goes wrong when a destination time lies outside the source clock?
- Derive the velocity units, including the factor of 1,000.
- Predict what the function should do with duplicate or unsorted timestamps.
- How could a clock-alignment error remain visually subtle in a final figure?

### Week 3 — Target changes, trial segmentation, and Fig. 1c

**Notebook coverage:** Module 3.

**Read before coding**

- Paper Fig. 1 and caption.
- Methods: “Closed-loop 2D finger tasks,” “Closed-loop 4D finger tasks,” and the description of the 500-ms hold and 10-s timeout.
- The relevant trajectory-plotting cells in `ManuscriptFigsFinal.ipynb`, but only after the student commits trial-boundary pseudocode and tests.

**Concepts**

- Multivariate target transitions.
- Tolerances for floating-point equality.
- Inclusive and half-open endpoint conventions.
- Trial starts, trial ends, zero-duration segments, first/last incomplete segments, and hold windows.
- Visual traceability from figure pixels to source rows.

**Practical work**

- Implement and test `transition_indices`.
- Implement `load_aligned_position_and_target` using the alignment decisions from Week 2.
- Specify which finger columns correspond to the selected degrees of freedom.
- Detect target segments and document every exclusion.
- Convert a 500-ms hold into the corresponding number of 50-ms bins.
- Implement `plot_target_trajectories` and recreate the first 100 seconds of Fig. 1c.
- Save the figure programmatically and trace one selected ten-second interval back to source timestamps and rows.
- Investigate the authors’ later overwrite of the block-45 output filename with block 48.

**Evidence due**

- Trial-transition tests, including tolerance and endpoint cases.
- Table of raw segments, retained trials, and exclusions for the exemplar block.
- Reproduced Fig. 1c and one clock-alignment diagnostic plot.
- A traceability note connecting a plotted interval to arrays and source rows.
- Module 3 AI/search attachment.

**Oral check-in prompts**

- Where can an off-by-one error enter the hold-window logic?
- Why should index zero appear exactly once in the transition list?
- How is target width obtained from the stored half-width parameter?
- How would you distinguish a wrong block from an incorrectly aligned correct block?
- What evidence establishes that a saved filename was overwritten?

### Week 4 — Behavioral metrics and Fig. 1e

**Notebook coverage:** Module 4A.

**Read before coding**

- Paper Results discussing 2D and 4D closed-loop performance, Fig. 1e, and Table 1.
- Methods: “Online metrics” and relevant Supplementary Methods.
- Authors’ behavioral-analysis cells only after pseudocode and primitive tests are committed.

**Concepts**

- Acquisition time, final hold, time to target, orbiting time, completion, target rate, and path efficiency.
- Trial-level versus block-level quantities.
- Successful and failed trial inclusion rules.
- Population-standard-deviation and sample-standard-deviation SEM conventions.
- Aggregation order and weighting.

**Practical work**

- Implement and test `sem_population` and `path_efficiency`.
- Write pseudocode for `analyze_block` before implementing it.
- Implement `analyze_block` with explicit exclusions and retained failure information.
- Implement `aggregate_blocks`, preserving the distinction between trial summaries and per-block target rates.
- Analyze the specified 2D and 4D blocks.
- Recreate the six-panel Fig. 1e comparison and export its full-precision numerical basis.
- Compare against preregistered rounded targets without changing the implementation to force agreement.

**Evidence due**

- Primitive metric tests and block-analysis tests.
- Per-trial and per-block machine-readable result tables.
- Reproduced Fig. 1e.
- A note explaining every failed or excluded segment.
- Initial numerical discrepancy table.
- Module 4 AI/search attachment begun for the two-week module.

**Oral check-in prompts**

- Why is the final hold excluded from acquisition time?
- Why do failures affect completion but not successful-trial timing summaries?
- Why is mean targets per minute not generally the reciprocal of mean acquisition time?
- Prove the upper bound for path efficiency using the triangle inequality.
- Predict which panels change if the hold interval is changed from 500 to 450 ms.

### Week 5 — Statistical reproduction and unit-of-analysis sensitivity

**Notebook coverage:** Module 4B.

**Read before coding**

- Paper “Statistical analysis” and the inferential claims associated with Figs. 1 and 2.
- Official documentation for the two-sample t-test used in the Python reproduction.
- A short reference on nested or repeated-measures data and pseudoreplication.
- Relevant MATLAB `ttest2` documentation to understand source-faithful defaults.

**Concepts**

- Two-sample, two-tailed t-tests and degrees of freedom.
- Effect sizes, confidence intervals, and p-values.
- Population versus sample SEM.
- Trials nested within blocks and days.
- Source-faithful reproduction versus a more defensible sensitivity analysis.

**Practical work**

- Reproduce the paper-associated comparisons and report statistic, degrees of freedom, p-value, sample counts, and effect direction.
- Reconstruct the percentage increase in acquisition time with an explicit numerator and denominator.
- Repeat at least one comparison using block means or day means.
- Compare the trial-level and grouped conclusions without replacing the source-faithful result.
- List every analytical choice required to reproduce the reported value.
- Complete the Module 4 interpretation answers and AI/search attachment.

**Evidence due**

- Full statistical output table.
- One block- or day-level sensitivity analysis.
- Short interpretation distinguishing numerical reproduction from strength of evidence.
- Completed Module 4 commit.

**Oral check-in prompts**

- What changes when `ddof=0` becomes `ddof=1`, and what does not change?
- Why can treating all trials as independent understate uncertainty?
- What is the unit of analysis in the source test and in the sensitivity analysis?
- Can a very small p-value compensate for a weak experimental unit? Why or why not?
- Which behavioral result is most sensitive to a one-sample boundary error?

### Week 6 — Neural dimensionality and Fig. 2a

**Notebook coverage:** Module 5.

**Read before coding**

- Paper section describing neural dimensionality and Fig. 2a.
- Methods “Offline analyses” and relevant Supplementary Methods.
- Official documentation for covariance/eigenvalue or PCA routines used.
- The authors’ dimensionality-analysis function after synthetic tests and a written pipeline prediction are committed.

**Concepts**

- Eigenvalue spectra and effective dimensionality.
- Participation ratio and scale invariance.
- Z-scoring, temporal smoothing, neural/behavioral delay, movement-window selection, condition balancing, and folds.
- Session values versus group summaries.
- Association versus mechanistic interpretation.

**Practical work**

- Derive the participation-ratio formula and implement `participation_ratio`.
- Test equal-rank, single-rank, rescaled, all-zero, negative, and nonfinite spectra.
- Trace and document the full session-level preprocessing pipeline.
- Implement `session_dimensionality` with the chosen normalization and balancing conventions.
- Compute the three requested groups and reproduce Fig. 2a.
- Examine how imbalanced target conditions change a synthetic estimate.
- Propose data that could separate neural from behavioral explanations for increased dimensionality.

**Evidence due**

- Participation-ratio derivation and synthetic tests.
- Session-level dimensionality table and eigenvalue diagnostics.
- Reproduced Fig. 2a.
- Condition-imbalance sensitivity demonstration.
- Module 5 AI/search attachment.

**Oral check-in prompts**

- Compute participation ratio for `[5, 5, 0]` and `[9, 1, 0]` without code.
- Why is participation ratio scale-invariant and potentially noninteger?
- How can trial selection change dimensionality without any change in electrodes?
- Why does doubling decoded degrees of freedom not mathematically require doubled neural dimensionality?
- Which plotted points are sessions and which are summaries?

### Week 7 — Released decoder inference and Fig. 2c–d

**Notebook coverage:** Module 6.

**Read before coding**

- Paper “Decoding algorithm,” “Closed-loop decoding software,” and Fig. 2c–d.
- `NNDecoders.py` and the metadata associated with one released checkpoint.
- Official PyTorch documentation for loading checkpoints, CPU mapping, evaluation mode, and disabled gradients.
- The relevant authors’ inference cells after the student draws the expected tensor shapes.

**Concepts**

- Time-by-channel-by-history inputs.
- Shared time-feature transforms, fully connected layers, batch normalization, dropout, and activation functions.
- Active-channel masks that retain a 256-wide model input while zeroing 64 of its positions.
- Input normalization and output denormalization.
- Zero-lag correlation versus maximum-lag normalized cross-correlation, and source-faithful uncentered versus centered sensitivity statistics.
- Correlation, calibration, bias, and amplitude.

**Practical work**

- Draw the tensor shape at each network stage from three 50-ms bins to decoder output.
- Implement and test `lagged_normalized_correlation`, including lag-sign convention, zero-energy behavior, the source-faithful uncentered mode, and a separately labelled centered sensitivity mode.
- Implement `run_released_decoder` with CPU-safe loading, a 256-wide mask containing exactly 192 active positions, correct normalization, three-bin windows, evaluation mode, and no gradients. Do not slice the checkpoint input to width 192.
- Confirm deterministic repeated inference.
- Recreate a 30-second Fig. 2c trace and the five-block means in Fig. 2d.
- Compare zero-lag and maximum-lag measures and explain why they answer different questions.

**Evidence due**

- Network architecture and tensor-shape audit.
- Cross-correlation tests, including a known time shift.
- Deterministic decoder-output record.
- Reproduced Fig. 2c–d and block-level correlation table.
- Module 6 AI/search attachment.

**Oral check-in prompts**

- Why must the checkpoint input remain 256-wide even though only 192 mask positions are active?
- Why do `eval()` and disabled gradients serve different purposes?
- What happens if the wrong normalization axis is used?
- Does a correlation near 0.68 establish correct amplitude or absence of bias?
- Diagnose repeated predictions that change when the same input is evaluated twice.

### Week 8 — Directional SNR, channel count, and Fig. 3b–c

**Notebook coverage:** Module 7.

**Read before coding**

- Paper Fig. 3 and caption, “Dependency of decoding accuracy on channel count,” and Methods “dSNR.”
- Official documentation for PCA, linear regression, cross-validation, least-squares log–log fitting, and coefficient of determination.
- Authors’ dSNR implementation after the projection and power-law primitives pass their tests.

**Concepts**

- Projection along intended direction and orthogonal residual.
- Train-only PCA and regression.
- Cross-validation leakage in temporally adjacent samples.
- Repeated random channel subsets and controlled random-number generation.
- Power-law fits on log-transformed data and the highest-channel-count fit region.
- Methods/code inconsistencies and limits on extrapolation.

**Practical work**

- Define dSNR in words, geometry, and an explicit formula.
- Implement and test `signal_and_noise_components` and `fit_power_law`.
- Implement `directional_snr_channel_sweep` with a passed random generator. For exact source mode, create one `np.random.RandomState(0)` object and advance it continuously through sessions in the released call order; label `default_rng` results as a sensitivity analysis.
- Run the reduced development sweep using five channel counts and five subsets.
- Verify that PCA and regression are fitted only within training folds.
- Design a trial-grouped alternative to sample-level folds and predict its effect.
- Investigate the paper’s 25-subset statement versus the released notebook’s 50-subset implementation.
- After the reduced analysis passes, run or explicitly cache the full sweep and recreate Fig. 3b–c.

**Evidence due**

- Projection and exact synthetic power-law tests.
- Reduced seeded sweep and reproducibility check.
- Train/test preprocessing audit and leakage discussion.
- Source-faithful Methods/code discrepancy note.
- Reproduced Fig. 3b–c, full-precision fit values, and optional full-sweep cache.
- Module 7 AI/search attachment.

**Oral check-in prompts**

- Why is fitting PCA before splitting data a form of leakage?
- Why repeat random channel subsets at the same channel count?
- What does an exponent below one-half suggest under the paper’s assumptions?
- Why does improvement through 192 channels not justify extrapolation beyond 192?
- Predict what should happen when added channels are exact duplicates of existing channels.

### Week 9 — Open-loop classification and the quadcopter exemplar

**Notebook coverage:** Modules 8–9.

**Read before coding**

- Methods “Open-loop finger task” and Extended Data Fig. 1b–c.
- Paper “Quadcopter tasks,” Fig. 4 and caption.
- Released MATLAB files `RunAnalysis.m`, `simpleClassify.m`, `t5_parse.m`, `RunFlightPathVis.m`, and `PlotFlightPath.m` as relevant.
- Official references for confusion matrices and three-dimensional plotting.

**Concepts**

- Pooled diagonal-covariance Gaussian classification.
- Class priors, stratified folds, compatible random partitions, and windowed features.
- Count confusion matrices versus row-normalized confusion matrices.
- Shuffled-label negative controls.
- MATLAB-inclusive indexing versus Python half-open slices.
- Coordinate conventions, elevation sign, hard-coded geometry, and exemplar-versus-aggregate evidence.

**Practical work: open-loop classification**

- Implement and test `diaglinear_predict`.
- Implement `row_normalized_confusion` and verify row denominators.
- Implement `run_open_loop_reproduction` in Python with documented fold and random-stream behavior. For the exact port, create one `np.random.RandomState(5489)` object, pass it first to the two-second analysis and then to the 150-ms analysis, and do not reset it between calls.
- Reproduce the two-second and 150-ms confusion matrices.
- Run a shuffled-label control and investigate any persistent above-chance structure.
- Identify the most common confusions and offer a cautious neurophysiological interpretation.

**Practical work: flight path**

- Inspect the quadcopter MAT schema and identify x, y, and z position arrays.
- Implement `make_ring` with a documented coordinate plane and order.
- Implement `plot_flight_path`, including the `-z` elevation convention and MATLAB-compatible lap boundaries.
- Recreate the full Fig. 4c path and four lap panels.
- Verify sample count and duration and distinguish measured trajectories from hard-coded ring centers.
- State which claims about 12 flights cannot be recovered from the single released exemplar.

**Evidence due**

- Classifier and confusion-matrix tests.
- Two reproduced confusion matrices plus shuffled-label control.
- Reproduced full and four-lap Fig. 4c plots.
- Coordinate and indexing audit with sample counts.
- Separate scope statement for exemplar and aggregate flight claims.
- Module 8 and Module 9 AI/search attachments.

**Oral check-in prompts**

- What assumption is imposed by diagonal covariance?
- Why are overall accuracy and the mean diagonal of a row-normalized confusion matrix not always identical?
- What should a shuffled-label confusion matrix look like, and what would residual structure imply?
- Why do adjacent lap slices share a boundary sample?
- Which visual and scientific conclusions change if the z sign is not inverted?
- Why can one released trajectory not reconstruct uncertainty across 12 completed flights?

### Week 10 — Clean reproduction, discrepancy report, and technical defense

**Notebook coverage:** Module 10 and final submission checklist.

**Read before coding**

- Re-read the paper’s Results, Discussion limitations, Data availability, and Code availability.
- Re-read the student’s Week 1 preregistration without changing the original entry.
- Review every module commit, AI/search attachment, numerical output, and discrepancy note.

**Concepts**

- Numerical, code, data, and presentation discrepancies.
- Paper-rounded agreement versus full-precision agreement.
- Reproduction scope and evidential limits.
- Clean execution and artifact traceability.
- Scientific reporting under uncertainty.

**Practical work**

- Clear or move the generated-output directory without altering source data.
- Restart the kernel and run the notebook from top to bottom in the declared environment.
- Regenerate all required figures and machine-readable results.
- Complete the comparison table using preregistered tolerances.
- Complete a discrepancy log that includes the Fig. 1c filename overwrite, Methods/code subset-count mismatch, clipped Fig. 3c annotation, released trial-interpolation bug, and at least one independently discovered discrepancy.
- Classify each mismatch, identify its cause, and state whether it changes interpretation.
- Write a concise final report and a 150-word replication verdict covering scope, successes, limitations, and provenance.
- Prepare for live explanation and modification of any core function.

**Evidence due**

- Cleanly executed final notebook.
- Regenerated figures: Fig. 1c, Fig. 1e, Fig. 2a, Fig. 2c–d, Fig. 3b–c, Extended Data Fig. 1b–c, and Fig. 4c.
- Full-precision JSON or CSV results and figure-source tables.
- Completed preregistration comparison and discrepancy log.
- Environment, provenance, commit, and AI/search records.
- Final report and replication verdict.

**Oral defense prompts**

- Which result is most robust to reasonable implementation choices, and which is least robust?
- Identify one numerical match that does not independently validate the biological claim.
- Propose a hierarchical or repeated-measures alternative to one trial-level comparison.
- Describe one new analysis supported by the released data and one that requires unreleased data or a new experiment.
- How should a last-decimal package-version difference be reported?
- Demonstrate and modify one randomly selected loading/alignment function and one analysis function.

### Week 11 — Willsey Lab application-readiness capstone

**Notebook coverage:** Module 11 and `student_capstone.md`.

Begin this week only after the technical defense. Recheck all current lab facts and joining instructions during the application week; positions and research emphases can change.

**Read before drafting**

- [Willsey Lab home](https://www.willseylab.org/).
- [University of Michigan Willsey Lab page](https://medschool.umich.edu/departments/neurosurgery/research/willsey-lab-brain-computer-interfaces).
- [Matthew Willsey's U-M faculty profile](https://medschool.umich.edu/profile/12961/matthew-s-willsey).
- [Current “Interested in joining?” page](https://www.willseylab.org/home/interested-in-joining).
- Two recent lab publications or current projects selected from official sources.
- The student's own final notebook, discrepancy log, and technical defense notes.

As checked on 7 August 2026, official descriptions emphasize implantable BCIs for severe motor and speech disabilities, multi-effector control, digital interfaces, nonlinear decoding, neural instability, speech neuroprostheses, and motor/computational neuroscience. The joining page names graduate, postdoctoral, and research-specialist routes but does not name a specific undergraduate category. The student must verify this again and must not assume an unlisted opening.

**Concepts**

- Evidence-to-claim mapping and application-language boundaries.
- The distinction between the Stanford-era 2025 paper and the current University of Michigan lab.
- Research fit based on current work rather than generic enthusiasm.
- Public technical artifacts versus private application materials.
- Respectful communication about human participants and translational research.
- Confidence grounded in technical ownership, including the ability to discuss failures and skills gaps.

**Practical work**

- Choose and verify the exact application route: undergraduate inquiry, later research-specialist role, formal graduate application, or another confirmed route.
- Create a public-safe repository README with provenance, reproducible setup, selected results, tests, discrepancies, limitations, and a next question.
- Write a one-page technical brief and prepare a five-slide, five-minute research talk.
- Draft one CV project entry and an inquiry or cover letter tailored to the verified route.
- Create an evidence-to-claim matrix linking every application statement to a cell, test, figure, result, commit, or report section.
- Prepare a two-minute project pitch and one-page follow-up proposal.
- Draft at least five evidence-grounded questions for Dr. Willsey, document why each is not already answered publicly, and select one scientific plus one research-practice/mentorship question.
- Separate public portfolio material from private AI transcripts, instructor keys, credentials, source data, and correspondence.
- Complete a 30-minute mock interview and revise materials based on factual or clarity problems discovered orally.

**Evidence due**

- Current-source and access-date record.
- Public repository or shareable portfolio archive that reruns from a fresh copy.
- One-page technical brief and five-slide talk.
- Evidence-bounded CV entry and tailored inquiry draft.
- Completed evidence-to-claim matrix.
- Two-minute pitch and one-page follow-up proposal.
- Five-question worksheet, selected final two, and a plausible follow-up for each.
- Module 11 AI/search attachment kept private by default.
- Mock-interview notes and corrected final materials.

**Mock-interview prompts**

- What exactly did you reproduce, and what did you not reproduce?
- Why does this project fit the current Willsey Lab rather than a generic neurotechnology lab?
- Describe one difficult implementation decision and one discrepancy without overstating either.
- What could you contribute initially, and what must you still learn?
- How did AI assistance enter the project, and how did you verify it?
- How would you handle public human neural data responsibly?
- What follow-up analysis would you propose, and how would its validation avoid the original pipeline's leakage or unit-of-analysis risks?
- Which two questions would you ask Dr. Willsey, what evidence motivated them, and how would you follow up rather than returning to a script?

## Final deliverables

The student submits a coherent project directory containing:

1. a completed, cleanly executed `undergrad_replication_workbook.ipynb`;
2. an environment recreation record, package specification, `pip check` result, kernel identity, and any approved compatibility notes;
3. a code/data provenance manifest with article DOI, Dryad version, Git commit, file inventory, and hashes;
4. tested implementations of every required function, with contracts and failure behavior;
5. programmatically generated versions of Fig. 1c, Fig. 1e, Fig. 2a, Fig. 2c–d, Fig. 3b–c, Extended Data Fig. 1b–c, and Fig. 4c;
6. full-precision result tables in JSON or CSV;
7. the original preregistration, completed comparison table, and discrepancy log;
8. one lightweight AI/search attachment per module;
9. a readable Git history containing at least one commit per module;
10. a short final report that distinguishes computational reproduction from experimental replication;
11. a successful final technical oral defense with live prediction, testing, interpretation, and code modification;
12. a public-safe portfolio README and one-page technical brief;
13. a five-slide, five-minute research talk and two-minute project pitch;
14. an evidence-bounded CV entry and tailored inquiry or cover-letter draft;
15. an evidence-to-claim matrix and one-page follow-up proposal;
16. a five-question professor-question worksheet with two justified selections and follow-ups; and
17. a completed application-readiness mock interview followed by factual revisions.

## Scope and limitations

### Supported by the released artifacts

The public release supports computational reproduction of central offline quantitative analyses using closed-loop finger blocks, pretrained decoder checkpoints, open-loop classification files, and one quadcopter trajectory. It permits the student to test whether specified numerical summaries and plots can be regenerated from the released bytes under documented analytical choices.

### Not supported by the released artifacts

This course does not independently repeat the implanted-human experiment. It does not reproduce electrode implantation, data acquisition, the real-time Redis system, participant instruction, decoder training or online recalibration, the Unity finger display, the AirSim controller, participant experience, supplementary videos, or the aggregate distribution across all 12 obstacle-course flights. A successful notebook therefore establishes computational reproducibility within the public release; it does not independently confirm every biological, clinical, or experiential claim.

### Interpretive cautions

- The dataset comes from one participant, so trial counts do not create a multi-participant clinical sample.
- Trials are nested within blocks and days; trial-level tests may overstate effective independence.
- A pretrained-checkpoint inference result is not a reproduction of training.
- A visually matching plot can conceal different source rows, aggregation rules, random partitions, or rounding.
- Improvement through the maximum released channel count does not establish behavior at larger channel counts.
- One flight exemplar cannot supply between-flight variation or recreate summary statistics across 12 flights.
- Source-code defects and manuscript/code mismatches should be reported even when they do not change the displayed headline result.

### Application-language boundaries

Accurate descriptions include “computationally reproduced selected offline analyses,” “reimplemented key functions in Python,” “ran released pretrained checkpoints,” and “analyzed released participant data.” Unsupported descriptions include “replicated the clinical study,” “trained the online decoder,” “worked with the participant,” “built the BCI or quadcopter system,” “conducted a human trial,” or “worked with the Willsey Lab.”

The student should distinguish the 2025 paper, whose experimental work occurred during Dr. Willsey's Stanford period, from the current University of Michigan Willsey Lab. The portfolio may say it is based on Willsey et al. and motivated by the current lab's research; it must not imply current lab membership, collaboration, or endorsement.

## Completion standard

The technical practicum is complete when the student can regenerate the required artifacts in a clean environment, trace each central number to source data and code, explain every core function, pass reasonable unseen tests, repair a small live mutation, and state a defensible verdict about what was and was not reproduced. Application readiness additionally requires a public-safe portfolio, evidence-to-claim audit, current-source research-fit explanation, feasible next analysis, concise written materials, two thoughtful questions for the professor with real follow-ups, and a mock interview in which every claim can be defended or corrected. The standard is demonstrated ownership of the analytical chain—not visual similarity, code volume, prompt quality, polished application language, or the absence of mistakes on a first attempt.
