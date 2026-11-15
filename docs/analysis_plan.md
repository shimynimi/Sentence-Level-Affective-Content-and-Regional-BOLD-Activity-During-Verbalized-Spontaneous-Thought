# Planned Analysis Workflow

This document describes a proposed workflow. It is not a record of analyses already run.

## Stage 0 — Source and version lock

- Record OpenNeuro accession, snapshot version, download date, and file manifest.
- Record OSF project/file identifiers and download date.
- Preserve original source files locally and keep a reproducible manifest.
- Do not commit participant-level source data to GitHub.

## Stage 1 — BIDS and imaging audit

- Run `src/audit_bids_dataset.py` on the local OpenNeuro directory.
- Validate the BIDS structure and dataset metadata.
- Inventory participants, sessions, tasks, runs, anatomical/functional files, JSON sidecars, and derivatives.
- Inspect fMRIPrep confounds and QC outputs where available.
- Verify TR, number of volumes, acquisition timing, and run consistency.

**Deliverable:** local BIDS inventory and a written audit summary with no participant-identifying information.

## Stage 2 — Behavioral and annotation audit

- Inspect the OSF directory and data dictionaries.
- Identify sentence-level and word-level transcript files.
- Confirm participant IDs and their mapping to BIDS labels.
- Verify time units and time origin.
- Identify the 14 rating dimensions, score ranges, directionality, missingness, and provenance.
- Locate human-validation ratings and decide how they may inform annotation sensitivity checks.

**Deliverable:** schema summary, missingness report, and verified participant-level file map stored locally.

## Stage 3 — Event construction and alignment

- Build one event record per eligible sentence using the verified transcript timestamps.
- Match records to the correct participant and functional run.
- Check sentence onsets/offsets against scan boundaries and acquisition timing.
- Resolve or exclude ambiguous events according to pre-specified rules.
- Derive speech-related features only from columns supported by the data.

**Deliverable:** a derived event table with no raw transcript text or direct identifiers in the public repository.

## Stage 4 — Quality control

- Determine available preprocessed outputs and motion measures.
- Define run- and participant-level QC rules before testing affective associations.
- Document all exclusions and reasons.
- Summarize the number of participants, runs, and events retained at each stage.

**Deliverable:** QC flow summary and non-identifying aggregate tables.

## Stage 5 — Statistical modelling

Proposed model comparison:

- **Baseline model:** thought category, speech-related predictors, run/time terms, and appropriate nuisance variables.
- **Augmented model:** baseline terms plus prespecified affective annotation predictors.

Use a repeated-measures approach that reflects the nesting of sentences/events within participants. Candidate implementations may include subject-level event-related GLMs followed by group-level inference or an appropriate hierarchical model, depending on the available derivatives and sampling structure.

Pre-specify ROI selection, model contrasts, uncertainty intervals, multiple-comparison handling, and sensitivity analyses after reviewing relevant methods and the data structure.

## Stage 6 — Robustness and reporting

- Inspect model assumptions and collinearity.
- Assess sensitivity to annotation dimensions and missingness.
- Consider human-validated ratings only for analyses supported by their subset size and sampling.
- Report null and inconclusive findings as well as positive findings.
- Avoid causal claims from observational secondary analysis.

## Planned software

The current BIDS inventory utility uses only the Python standard library. Potential analysis dependencies include pandas, NumPy, SciPy, statsmodels, nibabel, Nilearn, PyBIDS, openpyxl, and plotting libraries. The final environment file should be pinned after implementation and testing.
