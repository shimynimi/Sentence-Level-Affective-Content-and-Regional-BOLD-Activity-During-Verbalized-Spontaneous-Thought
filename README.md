# Sentence-Level Affective Content and Regional BOLD Activity During Verbalized Spontaneous Thought

**An NLP-informed secondary fMRI research project using the ThinkAloud dataset (OpenNeuro ds006067).**

This repository develops a research protocol for studying how affective characteristics expressed in spontaneous verbal thought relate to regional brain activity. It combines sentence-level language annotations and timing information with functional MRI data.

> **Project status — research in preparation.** The research question, data sources, and preliminary analysis plan are documented, and a basic BIDS inventory utility is available. The dataset has not yet been locally audited for this project; preprocessing, participant-level quality control, event alignment, model fitting, and statistical analyses have not been completed. No empirical findings are claimed.

## Research question

**Are sentence-level affective characteristics of spontaneous thought associated with within-person variation in regional BOLD activity, beyond effects attributable to thought category and speech-related features?**

The planned focus is on affective dimensions of sentence content. The exact dimensions, covariates, regions of interest, and statistical contrasts will be finalized only after inspecting the released files and reviewing relevant prior analyses.

## Why this dataset?

The ThinkAloud dataset captures spontaneous verbalized thought during functional MRI. Its current release combines BIDS-organized neuroimaging data with preprocessed derivatives, transcript timing at sentence and word levels, LLM-generated sentence-level psychological ratings, human validation ratings, and post-scan questionnaire measures.

### Data sources

1. **Neuroimaging:** [OpenNeuro ds006067 — version 2.0.0](https://openneuro.org/datasets/ds006067/versions/2.0.0)  
   The dataset page reports 118 participants. This is the released dataset count, not the expected final analysis sample. Project-specific inclusion and exclusion criteria must be applied after inspection and QC.

2. **Behavioral and annotation data:** [OSF — Think Aloud Behavioral Data](https://osf.io/a56rm/)  
   Includes sentence- and word-level transcripts with timestamps, sentence-level LLM-generated ratings across 14 psychological dimensions, human ratings for a validation subset, and post-scan questionnaire data.

The two sources are hosted separately and must be linked using verified participant identifiers. Downloading the OpenNeuro MRI dataset alone is not sufficient for the planned sentence-level analysis.

## Proposed workflow

1. **Dataset audit:** inspect BIDS metadata, participant identifiers, available scans, derivatives, and QC outputs.
2. **Behavioral-data audit:** inspect transcript, timestamp, annotation, and questionnaire files; verify column definitions and units.
3. **Data integration:** establish the participant-level join and align sentence events to the corresponding fMRI acquisition timeline.
4. **Quality control:** define and document participant/run inclusion criteria before inferential analysis.
5. **Feature construction:** summarize sentence-level affective annotations at the event level while retaining appropriate within-participant structure.
6. **Neuroimaging analysis:** develop event-related and ROI-level models, with relevant speech, thought-category, motion, and temporal nuisance variables.
7. **Inference and robustness:** assess model assumptions, uncertainty, multiple-comparison control, and sensitivity to alternative annotation/feature choices.

See [Research Protocol](docs/research_protocol.md), [Analysis Plan](docs/analysis_plan.md), [Data Sources](docs/data_sources.md), and [Related Work](docs/related_work.md).

## Repository contents

- `src/audit_bids_dataset.py` — preliminary inventory of a local BIDS directory; it does not perform preprocessing, QC, event alignment, or statistical analysis.
- `docs/` — research protocol, planned analysis workflow, data-source notes, and related-work context.
- `results/` — reserved for derived, non-identifying audit reports, QC summaries, tables, and figures.
- `requirements.txt` — Python packages for the planned analysis environment.

## Current implementation

The available script can inventory a local BIDS directory:

```bash
python src/audit_bids_dataset.py --bids-dir /path/to/ds006067 --output results/bids_inventory.json
```

It uses the Python standard library. The output is a file/metadata inventory only; counts do not establish data quality or participant eligibility.

## Important interpretation and scope notes

- LLM-generated sentence ratings are computational annotations of transcript content, not direct measurements of participants' subjective emotional states.
- The final sample size is not known until project-specific QC is completed.
- The project is a secondary analysis of existing, de-identified research data; data-use conditions and ethics documentation must be checked before analysis.
- No raw MRI files, participant-level transcripts, or questionnaire responses should be uploaded to this repository.
- The proposed research angle is not presented as novel or confirmed until a focused literature review and comparison with all analyses released alongside the dataset are completed.

## References

- Zhang, M., Liu, P. R., Su, H., et al. (2026). *An fMRI dataset of verbalized spontaneous thought with annotated transcripts and self-report trait measures*. **Scientific Data**. [https://doi.org/10.1038/s41597-026-08414-6](https://doi.org/10.1038/s41597-026-08414-6)
- Su, H., Li, X., Born, S., et al. (2025). *Neural dynamics of spontaneous memory recall and future thinking in the continuous flow of thoughts*. **Nature Communications, 16**, 6433. [https://doi.org/10.1038/s41467-025-61807-w](https://doi.org/10.1038/s41467-025-61807-w)

## Author

Shima Rezai
