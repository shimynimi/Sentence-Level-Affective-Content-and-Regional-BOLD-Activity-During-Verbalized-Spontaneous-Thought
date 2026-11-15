# Research Protocol

**Working title:** Sentence-Level Affective Content and Regional BOLD Activity During Verbalized Spontaneous Thought

**Status:** Proposed secondary analysis; protocol development in progress. No participant-level analysis has been conducted for this project.

## 1. Background and rationale

Spontaneous thought is internally generated and can include memories, plans, perceptions, and affective content. The ThinkAloud dataset makes it possible to examine naturally verbalized thought alongside fMRI data and time-aligned language annotations.

The current dataset release provides sentence- and word-level timing, LLM-generated psychological ratings, human validation ratings, and preprocessed MRI derivatives. This creates an opportunity to formulate a sentence-level question that focuses on affective annotations rather than simply reproducing analyses of thought transitions or broad category differences.

## 2. Primary research question

Are sentence-level affective characteristics of spontaneous thought associated with within-person variation in regional BOLD activity, beyond effects attributable to thought category and speech-related features?

This question is provisional. It will be refined after the source data dictionaries, annotation dimensions, timing conventions, and existing analyses have been inspected.

## 3. Candidate hypotheses

These are hypotheses to be evaluated, not results:

- **H1 (affective association):** Sentence-level affective annotation scores may explain variation in event-related regional BOLD responses.
- **H2 (incremental association):** Affective features may explain variance beyond a baseline model containing thought category and speech-related variables.
- **H3 (robustness):** Any observed association should be evaluated for sensitivity to participant-level variability, motion/QC decisions, and alternative affective feature specifications.

The direction, exact affective dimensions, and target regions will not be fixed until the rating scales and a priori neuroanatomical rationale have been verified.

## 4. Data sources and sample

### Neuroimaging
OpenNeuro ds006067, version 2.0.0. The release page reports 118 participants and provides BIDS-organized MRI data and derivatives. The final sample available for this proposed analysis is unknown and must be determined from the actual files and documented QC criteria.

### Behavioral and annotation
OSF project “Think Aloud Behavioral Data” (https://osf.io/a56rm/), described as containing:
- sentence-level transcripts and timestamps;
- word-level transcripts and timestamps;
- LLM-generated sentence-level ratings across 14 psychological dimensions;
- human ratings for a validation subset;
- post-scan questionnaire measures.

The participant ID mapping, exact annotation variables, missingness, and file-level completeness must be checked directly.

## 5. Proposed variables

| Role | Candidate information | Verification required |
|---|---|---|
| Main predictors | Sentence-level affective annotation dimensions | Rating names, scale, direction, missingness, and provenance |
| Outcome | Event-related regional BOLD response | Run availability, timing, preprocessing, ROI definition |
| Baseline covariates | Thought category and speech-related features | Annotation definitions and usable timing/feature fields |
| Nuisance variables | Motion and run-level confounds | Derivative availability and column definitions |
| Exploratory moderators | Questionnaire measures | Instrument names, scoring, missingness, and research rationale |

No variable should be treated as available until its source file and data dictionary have been inspected.

## 6. Proposed analysis approach

1. Audit the OpenNeuro BIDS structure and data derivatives.
2. Audit the OSF behavioral files and verify participant identifiers.
3. Confirm that transcript timestamps refer to the first acquired functional volume and determine how they relate to the fMRI time series.
4. Define the treatment of sentences spanning run boundaries, overlapping/missing timing, non-speech utterances, and excluded volumes.
5. Pre-specify participant/run QC and report exclusions transparently.
6. Construct event-level affective predictors and an appropriate baseline model.
7. Estimate within-participant associations using an approach that accounts for repeated events nested within participants.
8. Define a limited, theory-driven ROI analysis before inspecting outcome associations; consider whole-brain analyses only with appropriate correction and a clear rationale.
9. Check model assumptions, collinearity, influential observations, uncertainty, and robustness to alternative specifications.
10. Report null, ambiguous, and positive findings without overstating causal interpretation.

The exact GLM specification, hemodynamic response model, temporal filtering, ROI atlas, autocorrelation treatment, and multiple-comparison procedure remain to be decided after inspecting the preprocessed data and relevant methodological literature.

## 7. Interpretation limits

- BOLD is an indirect hemodynamic measure and does not directly measure thoughts or emotions.
- LLM ratings describe the linguistic content of a transcript and are not equivalent to self-reported emotional experience.
- Speech production, respiration, movement, and timing uncertainty may contribute to measured BOLD variation.
- Observational associations in this secondary dataset cannot by themselves establish that affective content causes regional activation.
- The dataset's released participant count is not the final analytic sample.

## 8. Current status and planned milestones

| Milestone | Status |
|---|---|
| Identify candidate dataset and research direction | Completed |
| Document source repositories and initial audit checklist | Completed |
| Download and inspect local source files | Not started |
| Audit participant IDs, annotations, timestamps, and missingness | Not started |
| Finalize QC criteria and statistical analysis plan | Not started |
| Run event alignment and fMRI analysis | Not started |
| Validate models and prepare figures/tables | Not started |
| Write up findings | Not started |

## References

- Zhang, M., Liu, P. R., Su, H., et al. (2026). *An fMRI dataset of verbalized spontaneous thought with annotated transcripts and self-report trait measures*. Scientific Data. https://doi.org/10.1038/s41597-026-08414-6
- Su, H., Li, X., Born, S., et al. (2025). *Neural dynamics of spontaneous memory recall and future thinking in the continuous flow of thoughts*. Nature Communications, 16, 6433. https://doi.org/10.1038/s41467-025-61807-w
