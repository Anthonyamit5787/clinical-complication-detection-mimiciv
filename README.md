# Clinical Complication Detection from MIMIC-IV Discharge Summaries

Rule-based clinical NLP workflow for detecting and evaluating complication mentions in ICU discharge summaries. The project combines exploratory biomedical entity extraction with a targeted medSpaCy pipeline, contextual filtering, canonical category mapping, manual review, error analysis, and statistical validation.

**Author:** Anthony Amit Biswas

## Project overview

The system analyses MIMIC-IV and MIMIC-IV-Note discharge summaries and maps extracted complication mentions to 23 canonical categories. scispaCy is used for exploratory biomedical entity extraction, while medSpaCy TargetMatcher and ConText form the final targeted extraction pipeline.

The reviewed evaluation set contains 70 discharge summaries and 491 reference complication mentions. The final evaluation produced 546 canonical predictions.

| Evaluation level | Precision | Recall | F1 |
| --- | ---: | ---: | ---: |
| Exact span | — | — | 0.9026 |
| Exact span + category | — | — | 0.8949 |
| Relaxed overlap + category | — | — | 0.9238 |
| Strict end-to-end | 0.5476 | 0.6090 | 0.5767 |

Strict end-to-end evaluation requires the span, complication category, assertion and temporality attributes to be correct. The differences between evaluation levels highlight the effect of boundary and contextual-classification errors.

## Notebook workflow

| Notebook | Purpose |
| --- | --- |
| `01_explore_mimic_notes.ipynb` | Explore source tables and construct the ICU discharge-summary cohort. |
| `02_understanding_clinical_text.ipynb` | Analyse note structure, headings, length and terminology. |
| `03_clinical_text_preprocessing.ipynb` | Clean formatting and de-identification placeholders conservatively. |
| `04_scispacy_clinical_entity_extraction.ipynb` | Extract exploratory biomedical mentions with scispaCy. |
| `05_medspacy_complication_extraction.ipynb` | Run targeted complication extraction and contextual classification. |
| `06_gold_standard_annotation.ipynb` | Construct and validate the reviewed annotation workflow. |
| `07_system_evaluation.ipynb` | Evaluate span, category, assertion and temporality performance. |
| `08_error_analysis_and_interpretation.ipynb` | Analyse false positives, false negatives and error types. |
| `09_publication_quality_visualisations.ipynb` | Generate consistent research visualisations from frozen results. |
| `10_reproducibility_and_statistical_validation.ipynb` | Produce statistical validation, manifests and reproducibility assets. |

## Data access

This repository does not distribute MIMIC-IV, MIMIC-IV-Note, clinical notes, note identifiers, annotation workbooks containing patient text, or other restricted derivatives.

To run the complete workflow, obtain authorised access through [PhysioNet](https://physionet.org/content/mimiciv/) and comply with the applicable credentialing and data-use requirements. Place authorised files in a local `data/` directory or update the configurable project paths in the notebooks. The `data/` directory is excluded from version control.

## Installation

Create an isolated Python environment and install the general dependencies:

```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

Notebooks 04 and 05 contain their original tested, notebook-specific NLP installation cells. Run the notebooks sequentially because later stages consume validated outputs from earlier stages.

## Research limitations

This is exploratory research software, not a clinically validated or deployable decision-support system. The reference corpus used a candidate-assisted annotation process and therefore may overestimate performance. Independent annotation, inter-annotator agreement, external validation and prospective clinical evaluation would be required before considering operational use.

## Licence

The repository code is released under the MIT License. MIMIC-IV data remains subject to PhysioNet's own terms and is not covered by this repository licence.

