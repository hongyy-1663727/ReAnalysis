# Module commit checklist

Complete this checklist immediately after finishing each module and before creating that module's commit.

## Required checks

- [ ] All module questions are answered in the student's own words.
- [ ] Predictions or pseudocode were recorded before consulting reference code or numerical answers.
- [ ] Each implemented function states its purpose, inputs, outputs, shapes, units, assumptions, and failure behavior.
- [ ] Synthetic known-answer tests and required module checks pass.
- [ ] Relevant figures, JSON/CSV results, and discrepancy notes are saved.
- [ ] The AI/search record contains the authentic exported conversation and/or exact search terms, the affected step, and an independent check.
- [ ] No downloaded `.mat` data, checkpoints, credentials, instructor answer files, or private correspondence are staged.
- [ ] `git diff --check` reports no whitespace errors.
- [ ] `git status` contains only files intentionally changed for this module.
- [ ] The notebook opens successfully and the module cells are in a coherent order.

## Commit procedure

```bash
git status
git diff --check
git diff --stat
git add undergrad_replication_workbook.ipynb
git add outputs/student_replication   # only when this module created reviewed outputs
git status
git commit -m "module N: concise description"
git push
```

Never run `git add .` without first checking exactly which files are untracked or modified.

## Required commit messages

```text
module 0: scope and preregistration
module 1: provenance and integrity
module 2: schema and clock alignment
module 3: segmentation and fig 1c
module 4: behavior and statistics
module 5: neural dimensionality
module 6: decoder inference
module 7: directional snr
module 8: open-loop classification
module 9: flight path
module 10: validation and final report
module 11: application capstone
```

Additional descriptive text may follow the required prefix. Do not combine two modules in one commit. If a correction is discovered after review, make a new transparent correction commit rather than rewriting reviewed history.

## Evidence to show during the checkpoint

```bash
git log --oneline --decorate --max-count=15
git show --stat --oneline HEAD
git status --short
```

The working tree should be clean before beginning the next module.
