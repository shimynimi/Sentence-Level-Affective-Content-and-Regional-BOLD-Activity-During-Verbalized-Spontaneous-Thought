# Sentence-Level Affective Content and Regional BOLD Activity

A proposed secondary analysis of **OpenNeuro ds006067** investigating whether affective characteristics of spontaneous thought are associated with regional brain activity during verbalized thought.

## Research question

**Do sentence-level affective characteristics of spontaneous thought explain within-person variation in regional BOLD activity after accounting for thought category and speech-related features?**

The project is designed as an NLP-informed fMRI analysis. The affective variables are computational annotations of transcript content; they should not be interpreted as direct measurements of participants' subjective emotional states.

## Data sources

This project requires two linked public data sources:

1. **Neuroimaging data — [OpenNeuro ds006067, version 2.0.0](https://openneuro.org/datasets/ds006067)**  
   BIDS-organized anatomical and functional MRI data, including fMRIPrep/FreeSurfer derivatives and associated quality-control outputs. The dataset descriptor reports 118 participants. The final analysis sample will be determined by project-specific data checks and quality control.

2. **Behavioral and annotation data — [OSF: Think Aloud Behavioral Data](https://osf.io/a56rm/)**  
   Sentence-level transcripts and timestamps, word-level transcripts and timestamps, LLM-generated sentence-level ratings across 14 psychological dimensions, human ratings for a validation subset, and post-scan questionnaire data.

The two sources must be linked using the participant identifiers documented by the dataset. MRI and behavioral files are hosted separately; downloading OpenNeuro alone is not sufficient for the proposed content-level analysis.

### Annotation note

The sentence-level affective and sensory ratings are LLM-generated annotations of transcript content. They are not direct physiological measurements or participant self-reports of emotion. The dataset release describes a human-validation subset consisting of 18 transcripts rated by four independent human raters.

## Planned analysis

1. Audit the BIDS structure, participant identifiers, imaging files, and available derivatives.
2. Inspect transcript, timestamp, rating, and questionnaire schemas in the OSF behavioral release.
3. Match sentence-level events and annotations to each participant's fMRI time series.
4. Define preprocessing/QC criteria and document exclusions before statistical analysis.
5. Estimate event-related models and examine prespecified regional/ROI-level associations.
6. Account for thought category, speech-related features, and relevant motion/nuisance variables; correct for multiple comparisons where appropriate.

The exact feature set, ROI definitions, QC thresholds, and statistical model will be finalized after inspecting the source files and confirming data availability.

## Repository contents

- `src/audit_bids_dataset.py` — inventories files and basic metadata in a local BIDS dataset. It does not run fMRI preprocessing, quality control, event alignment, or statistical analysis.
- `results/` — reserved for derived, non-identifying audit reports, QC summaries, tables, and figures.
- `docs/data_sources.md` — data provenance, expected inputs, and the first audit checklist.

## Run the current BIDS inventory script

```bash
python src/audit_bids_dataset.py --bids-dir /path/to/ds006067 --output results/bids_inventory.json
```

The script uses only the Python standard library. It inventories local files; it does not establish that a participant or scan is suitable for statistical analysis.

## Current status

The research question and preliminary analysis plan are documented, and a basic BIDS inventory utility is available. The empirical fMRI analysis has **not started**. No preprocessing, participant-level QC, transcript-to-BOLD modelling, or statistical results are claimed.

## Data protection

Do not upload raw MRI files, participant-level transcripts, questionnaire responses, or other source data to this GitHub repository. Keep downloaded source data locally and follow the data providers' terms and applicable research ethics requirements.

## References

- Zhang et al. (2026). [An fMRI dataset of verbalized spontaneous thought with annotated transcripts and self-report trait measures](https://doi.org/10.1038/s41597-026-08414-6). *Scientific Data*.
- Su et al. (2025). [Neural dynamics of spontaneous memory recall and future thinking in the continuous flow of thoughts](https://doi.org/10.1038/s41467-025-61807-w). *Nature Communications*.
