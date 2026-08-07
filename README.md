# Willsey finger-BCI computational reproduction

Student repository for an undergraduate computational reproduction of Willsey et al., *A high-performance brain-computer interface for finger decoding and quadcopter game control in an individual with paralysis*.

The technical goal is to reproduce selected offline analyses from the released data, code, and pretrained checkpoints. The professional goal is to finish with work that can be explained, tested, critiqued, extended, and discussed confidently in a research application.

This is a computational reproduction, not an independent repetition of the implanted-human experiment.

## Start here

| File | Purpose |
|---|---|
| `one_page_syllabus.pdf` | Printable course overview |
| `one_page_syllabus.md` | Editable text version of the overview |
| `detailed_syllabus.md` | Complete eleven-week course plan and expectations |
| `student_capstone.md` | Application-readiness portfolio and mock-interview guide |
| `undergrad_replication_workbook.ipynb` | Primary student notebook, Modules 0-11 |
| `environment.yml` | Conda environment specification |
| `requirements.txt` | Python `venv`/pip alternative |
| `MODULE_COMMIT_CHECKLIST.md` | Required checks before every module commit |

## Required commit policy

**The student must commit immediately after completing every module.** There are twelve required module commits, one for each Module 0 through Module 11, in addition to this initial repository commit.

Do not complete several modules and place them in one bulk commit. The Git history is part of the evidence that predictions, tests, revisions, and interpretations developed in sequence.

Minimum required commit sequence:

| Module | Required commit message prefix | Completed |
|---:|---|:---:|
| 0 | `module 0: scope and preregistration` | [ ] |
| 1 | `module 1: provenance and integrity` | [ ] |
| 2 | `module 2: schema and clock alignment` | [ ] |
| 3 | `module 3: segmentation and fig 1c` | [ ] |
| 4 | `module 4: behavior and statistics` | [ ] |
| 5 | `module 5: neural dimensionality` | [ ] |
| 6 | `module 6: decoder inference` | [ ] |
| 7 | `module 7: directional snr` | [ ] |
| 8 | `module 8: open-loop classification` | [ ] |
| 9 | `module 9: flight path` | [ ] |
| 10 | `module 10: validation and final report` | [ ] |
| 11 | `module 11: application capstone` | [ ] |

Each commit must contain the completed module answers, implementation or analysis, tests, relevant result files, discrepancy notes, and the module's AI/search record. Run the checks in `MODULE_COMMIT_CHECKLIST.md` before committing.

Recommended command pattern:

```bash
git status
git diff --check
git add undergrad_replication_workbook.ipynb outputs/student_replication
git commit -m "module N: concise description of completed work"
git push
```

If a module produces no external result file, add only the notebook and other files genuinely changed. Never use `git add .` without reviewing `git status` first.

## Environment setup

Choose one isolated environment route and record every command in the workbook.

### Conda

```bash
conda env create -f environment.yml
conda activate willsey-undergrad-replication
python -m ipykernel install --user --name willsey-undergrad-replication --display-name "Python 3 (Willsey replication)"
python -m pip check
jupyter notebook undergrad_replication_workbook.ipynb
```

### Python venv

Create a Python 3.9 environment using the launcher appropriate for the operating system, activate it, and then run:

```bash
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
python -m pip check
python -m ipykernel install --user --name willsey-undergrad-replication --display-name "Python 3 (Willsey replication)"
jupyter notebook undergrad_replication_workbook.ipynb
```

## Local data and released code

The downloaded data and authors' checkout are deliberately excluded from Git. Place them locally as:

```text
repository-root/
├── work/
│   ├── code_audit/          # authors' repository at the fixed commit
│   └── replication/
│       └── Data/            # extracted Dryad Data directory
└── outputs/
    └── student_replication/ # generated figures and numerical results
```

Sources:

- Paper: <https://doi.org/10.1038/s41591-024-03341-8>
- Data: <https://doi.org/10.5061/dryad.1jwstqk4f>, version 3
- Authors' code: <https://github.com/WillseyBCILab/BCI_Finger_Decoding_Quadcopter>, commit `addd54935c84db611d2e181b3f61d9c60aa9c412`

## Privacy and publication boundary

Keep this learning repository private while the workbook contains personal records or exported AI conversations. Do not commit:

- downloaded participant data or model checkpoints;
- instructor guides, answer keys, or expected-value files;
- passwords, tokens, private keys, `.env` files, or machine credentials;
- private application correspondence;
- private AI transcript exports outside the course notebook; or
- unrelated personal information.

Module 11 produces a separate sanitized public portfolio. Before making anything public, remove private process records, verify licensing, use authorized data-download instructions rather than redistributing the dataset, and rerun the public repository from a fresh copy.

## Completion

The repository is complete when Modules 0-11 each have a distinct reviewed commit, the notebook runs from a clean kernel, all required figures and machine-readable results regenerate, the technical defense is passed, and the student can defend every claim in the application portfolio.
