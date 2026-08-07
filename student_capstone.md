# Willsey Lab application-readiness capstone

## Purpose

The final goal of this practicum is not merely to regenerate figures. It is to help the student become a credible, technically prepared, and intellectually honest applicant to the Willsey Laboratory for Brain-Computer Interfaces.

“Application ready” means that the student can:

- explain the lab's current research direction from official sources;
- connect completed work to the lab's needs without exaggerating experience;
- show a clean, reproducible technical portfolio;
- discuss one useful next research question rather than stopping at replication;
- explain every major analytical function without relying on AI during the conversation;
- communicate respectfully about human-participant neural data and clinical translation; and
- send a concise, tailored inquiry with a CV and evidence of completed work.

Completion of this course does not guarantee a position, endorsement, interview, or admission. It prepares the student to make a serious application.

## Current official context

Verify these pages again immediately before applying. The statements below were checked on **7 August 2026**.

- [Willsey Lab home](https://www.willseylab.org/): the University of Michigan lab studies implantable BCIs for severe motor and speech disabilities. Its stated themes include multi-effector fine-motor and digital-interface control, nonlinear decoding, neural instability, speech neuroprostheses, and motor neuroscience.
- [University of Michigan lab page](https://medschool.umich.edu/departments/neurosurgery/research/willsey-lab-brain-computer-interfaces): the lab is led by Matthew S. Willsey, MD, PhD, and combines implantable BCIs, decoding algorithms, multi-effector control, computational neuroscience, and new BCI applications.
- [Matthew Willsey's U-M profile](https://medschool.umich.edu/profile/12961/matthew-s-willsey): lists appointments in Neurosurgery and Biomedical Engineering and currently marks him as available to mentor.
- [Interested in joining](https://www.willseylab.org/home/interested-in-joining): currently describes graduate, postdoctoral, and research-specialist/clinical-BCI-assistant routes and requests a cover letter and CV by email.

The joining page does **not** currently name a specific undergraduate-research category, application deadline, or U-M job number. The student must not state that an undergraduate vacancy exists unless a current official source or direct reply confirms it. A current undergraduate can instead make a concise inquiry about whether an appropriate opportunity exists, or use this portfolio to prepare for a later graduate or research-specialist application.

## Required application portfolio

### 1. Public-safe project repository

Prepare a repository or shareable archive containing:

- a concise landing-page README;
- the scientific question and a plain-language summary;
- exact paper DOI, Dryad version, and authors' code commit;
- reproducible environment instructions for Conda and `venv`;
- tested student-written functions;
- a figure gallery with captions and links to generating cells;
- full-precision result and discrepancy tables;
- a clear “what I reproduced / what I did not reproduce” section;
- one proposed follow-up analysis; and
- acknowledgments and the licenses/citations required by the original sources.

Do not publish private credentials, unrelated conversation history, instructor answer keys, or source data merely because they were locally available. Link to the authorized source and follow its license and terms.

### 2. One-page technical brief

Use these headings:

1. **Question:** What did the paper test, and what did this project attempt?
2. **Methods:** Which data, environments, and independently implemented analyses were used?
3. **Results:** Which central numerical and visual results were recovered?
4. **Audit findings:** Which discrepancy or sensitivity analysis taught the most?
5. **Limitations:** What could not be inferred from one participant and released offline artifacts?
6. **Next question:** What concrete analysis should follow?

### 3. Five-minute research talk

Prepare five slides:

1. scientific motivation and strict reproduction scope;
2. data-to-result pipeline;
3. one behavioral or neural result;
4. one discrepancy, failure, or sensitivity analysis; and
5. proposed next analysis and fit with the lab's current work.

The student must be able to deliver the talk without reading and answer questions from the underlying notebook.

### 4. CV entry

Write one project title and two or three evidence-based bullets. Quantify only work the student actually completed. A model structure is:

> **Computational reproduction of an intracortical finger-BCI study** — Independent research project, [dates]
>
> - Reconstructed selected offline analyses from released human iBCI MAT data in a version-controlled Python/Jupyter environment, including multirate alignment, behavioral metrics, neural dimensionality, pretrained-decoder evaluation, directional SNR, classification, and 3-D trajectory visualization.
> - Recovered the paper's reported values at stated precision and built synthetic tests, provenance checks, cross-validation audits, and sensitivity analyses to identify leakage, random-stream, indexing, and aggregation risks.
> - Documented the limits of single-participant offline reproduction and proposed [student's genuinely completed follow-up analysis].

Shorten this to the work actually completed. Do not use “replicated the clinical study,” “built a BCI,” or “conducted a human trial.”

### 5. Tailored inquiry or cover letter

The final message should contain:

- the student's present status and the exact type of opportunity being sought;
- one sentence showing current, source-verified knowledge of the lab;
- two concrete pieces of evidence from the portfolio;
- one research question the student would like to explore;
- a direct but low-pressure question about fit or opportunity;
- links or attachments requested by the official page; and
- an acknowledgement that no undergraduate opening is assumed if none is posted.

Model structure—replace every bracketed field and remove anything not true:

> **Subject:** Undergraduate inquiry — reproducible neural-decoding analysis
>
> Dear Dr. Willsey,
>
> I am a [year and major] at [institution] seeking [precise opportunity and dates]. I have been studying your lab's work on [one current theme verified from an official source], beginning with a computational reproduction of the finger-decoding and quadcopter paper.
>
> Using the released Dryad data and fixed GitHub source, I independently implemented and tested [two specific completed components]. I recovered [one concise result], documented [one meaningful discrepancy or sensitivity analysis], and prepared a reproducible notebook and short technical brief: [link]. This work led me to ask [one concrete next research question].
>
> I did not see a specifically listed undergraduate route on the current joining page, so I wanted to ask whether there may be an appropriate way for an undergraduate with experience in [honest skills] to contribute or prepare for future work with the lab. I have attached my CV and would be grateful for any guidance.
>
> Sincerely,<br>
> [Name]

The instructor should review factual accuracy and tone. The student, not AI, makes the final claims and sends the message.

### 6. Two-minute project pitch

Prepare a spoken answer to “Tell me about this project.” It must cover:

- the question and released artifacts;
- two technically specific things the student implemented;
- one result;
- one problem discovered or sensitivity analysis;
- the boundary between computational reproduction and experiment replication;
- one next analysis; and
- why that next question connects to a current lab theme.

### 7. One-page follow-up proposal

Choose a question that can be started with the released data. Recommended example:

**Does trial-grouped cross-validation reduce directional-SNR estimates or change their channel-count scaling compared with random sample-level folds?**

Include:

- hypothesis;
- motivation;
- available inputs;
- unit of analysis;
- train/test grouping and leakage controls;
- primary statistic and uncertainty;
- expected outcomes and alternative explanations;
- one limitation; and
- a first-week implementation plan.

## Application-readiness questions

Write answers in the application section of the notebook, then practice them orally.

1. In two sentences, what does the Willsey Lab currently study? Cite official sources and the date checked.
2. Which three completed project artifacts best demonstrate fit, and what does each fail to demonstrate?
3. What exactly did you reproduce, and what did you not reproduce?
4. Which technical decision in the analysis required the most judgment?
5. Describe one discrepancy without implying misconduct. What was its numerical and scientific impact?
6. Which follow-up analysis would you start first, and why is its validation plan stronger?
7. Why this lab rather than a generic neurotechnology lab?
8. What could you contribute during an initial research period, and what would you need to learn?
9. How would you handle public human neural data responsibly?
10. What should you do if no undergraduate role is listed?
11. How did AI or search assistance enter the project, and how did you verify it?
12. Deliver the two-minute project pitch without notes.

## Designing insightful questions for Dr. Willsey

The student should not end an interview with a question improvised from nerves. Question design is part of the capstone because a strong question demonstrates preparation, scientific judgment, curiosity, and the ability to listen.

### What makes a question insightful?

A strong question:

- is motivated by a current official project, recent paper, or a concrete finding from the reproduction;
- asks for judgment, tradeoffs, failure experience, or future direction rather than a fact already published online;
- is specific to this lab but understandable without a long preamble;
- connects naturally to something the student genuinely understands;
- does not pretend the student already has an affiliation or specialized experience;
- is open-ended without being vague;
- can be asked in approximately 20 seconds; and
- creates a natural follow-up based on the answer.

### Question-design process

1. Re-read the current lab, people, publications, clinical-trials, and joining pages.
2. Read at least two current projects or papers beyond the finger/quadcopter paper.
3. Review the student's discrepancy log, follow-up proposal, and identified skills gap.
4. Draft at least five candidate questions without trying to perfect them.
5. For each question, record the source that motivated it, why the answer matters, why it is not already public, and one possible follow-up.
6. Remove questions that are generic, answerable online, yes/no, adversarial, excessively long, or based on an unsupported assumption.
7. Select two: one scientific question and one research-practice, mentorship, or useful-contribution question.
8. Practice asking each concisely, then practice listening and asking a follow-up rather than immediately returning to a prepared speech.

## Final readiness check

Before the student contacts the lab, confirm that:

- every application claim points to a real artifact or completed action;
- the current lab page and current joining instructions were rechecked that week;
- the target route is explicit and does not assume an unlisted vacancy;
- the public repository runs in a clean environment and excludes instructor materials;
- the one-page brief and five-minute talk agree with the notebook;
- the CV uses “computationally reproduced selected analyses,” not “replicated the experiment”;
- the student can explain and modify two randomly selected functions without AI;
- the student can discuss one failure or limitation calmly and precisely;
- the proposed next analysis has a testable question and valid unit of analysis;
- the student has prepared two evidence-grounded questions that are not answered by the current website and can ask a genuine follow-up;
- all discussion of the participant is respectful and evidence-bounded; and
- the inquiry is concise, specific, proofread, and genuinely written in the student's voice.

Confidence should come from ownership of the work, not certainty of receiving a position.
