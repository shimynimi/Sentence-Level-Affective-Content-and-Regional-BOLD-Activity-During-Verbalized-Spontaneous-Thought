# Data sources and first audit

## 1. Neuroimaging data

- Repository: [OpenNeuro ds006067](https://openneuro.org/datasets/ds006067)
- Snapshot to use: **2.0.0**
- Expected organization: BIDS, with raw MRI data and a `derivatives/` directory containing preprocessed outputs.
- Dataset descriptor reports 118 participants. This is the released dataset count, not a guarantee that every participant will pass this project's QC.

Files to inspect first:

- `dataset_description.json`
- `participants.tsv` and `participants.json`, if present
- Root-level `README` and `CHANGES`
- For a small pilot subset: one participant's `anat/` and `func/` files, functional JSON sidecar, event/timing files, and corresponding derivative/QC files

## 2. Behavioral and annotation data

- Repository: [OSF — Think Aloud Behavioral Data](https://osf.io/a56rm/)
- Relevant data described in the dataset paper:
  - sentence-level transcript spreadsheets with sentence start/end times;
  - word-level transcript spreadsheets with word start/end times;
  - sentence-level LLM-generated ratings across 14 psychological dimensions;
  - human-validation ratings for 18 transcripts, independently rated by four human raters;
  - post-scan questionnaire files.

The paper describes sentence- and word-level timestamps in seconds relative to acquisition of the first functional image. Inspect the actual spreadsheets and data dictionary before writing any join or timing-conversion code.

## 3. Linking the sources

Use the documented participant/BIDS identifiers to connect MRI and behavioral records. Do not assume identifier formats match until they are checked. Preserve the original identifiers in a local mapping table and do not publish participant-level records.

## 4. First audit checklist

- [ ] Record the exact OpenNeuro snapshot/version and download date.
- [ ] Read the BIDS dataset description, participants table, and change log.
- [ ] Count participant directories and summarize available MRI runs.
- [ ] Check which participants have the required fMRI files and derivatives.
- [ ] Inspect the matching OSF folder/file structure and spreadsheet column names.
- [ ] Confirm the join key and timestamp units.
- [ ] Confirm which sentence-level affective dimensions are present and how they are scored.
- [ ] Inspect the human-validation subset before deciding whether to use all LLM-generated ratings.
- [ ] Produce a local inventory report; do not upload raw MRI, transcripts, or questionnaire data to GitHub.

## Important interpretation limits

LLM-generated sentence ratings are annotations of transcript content, not direct measurements of participants' subjective emotional states. Participant count in the released dataset must not be presented as the final analysis sample; exclusions and missing data must be determined through an explicit QC procedure.
