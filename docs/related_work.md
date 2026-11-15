# Related Work and Positioning

This is an initial, non-systematic reading note. It is not a completed systematic literature review, and no novelty claim is made.

## 1. Existing analysis of the ThinkAloud dataset

Su et al. (2025) used a think-aloud fMRI paradigm to study the dynamics of spontaneous thought. Their analyses examined thought categories, topic/semantic transitions, thought boundaries, and functional interactions involving default and control networks. The present proposal should not simply repeat those transition-focused questions.

**Reference:** Su, H., Li, X., Born, S., et al. (2025). Neural dynamics of spontaneous memory recall and future thinking in the continuous flow of thoughts. *Nature Communications, 16*, 6433. https://doi.org/10.1038/s41467-025-61807-w

## 2. Expanded dataset release

Zhang et al. (2026) describe an expanded release with preprocessed MRI, finer-grained word timestamps, sentence-level LLM-generated psychological ratings, human validation ratings, and post-scan questionnaires. The data descriptor reports validation analyses, including agreement between LLM and human ratings and neural associations involving speech/sensory content.

**Reference:** Zhang, M., Liu, P. R., Su, H., et al. (2026). An fMRI dataset of verbalized spontaneous thought with annotated transcripts and self-report trait measures. *Scientific Data*. https://doi.org/10.1038/s41597-026-08414-6

## 3. Proposed direction

The current proposal focuses on whether sentence-level affective annotations explain regional BOLD variation after accounting for thought category and speech-related features. This is a candidate analysis direction, not a confirmed gap in the literature.

Before making a novelty claim, the literature review must inspect:
- all analyses and code released with the expanded dataset;
- the exact emotion/affect dimensions and neural validation analyses already reported;
- related work on affective language, spontaneous thought, speech production, and naturalistic fMRI;
- overlap between proposed event-level predictors, existing annotations, and published contrasts.

## 4. Interpretation cautions

LLM-generated affective scores characterize transcript content according to a model's annotation process. They are not direct measurements of a participant's experienced affect. Human validation, where available, should be treated as evidence about annotation agreement rather than proof that annotations are ground-truth emotion labels.

The proposed analyses are observational and cannot establish causal effects of emotion on brain activity.
