# Sentence-Level Affective Content and Regional BOLD Activity

A proposed secondary analysis of **OpenNeuro ds006067** examining whether sentence-level affective content during verbalized spontaneous thought is associated with regional BOLD activity.

## Method

The planned analysis uses sentence-level affective ratings, transcript timestamps, and fMRI data. The protocol proposes motion-aware quality control, event-related GLM modelling, and ROI-level group analysis.

## Repository

- `src/audit_bids_dataset.py` — inventories files and basic metadata in a local BIDS dataset. It does not run fMRI preprocessing, quality control, or statistical analysis.
- `results/` — location for generated reports, tables, and figures.

## Current status

The research question and analysis plan are documented. The empirical fMRI analysis has **not started**; therefore, no statistical or neuroimaging results are reported yet.

## Run the inventory script

```bash
python src/audit_bids_dataset.py --bids-dir /path/to/ds006067 --output results/bids_inventory.json
```

The script uses only the Python standard library. Do not upload participant-level or otherwise restricted data to this repository.
