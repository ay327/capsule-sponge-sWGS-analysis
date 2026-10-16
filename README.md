# Capsule-sponge shallow whole-genome sequencing analysis

This repository contains the custom R code used for the capsule-sponge shallow
whole-genome sequencing (sWGS) copy-number analyses reported in:

**Genetic analyses of pan-oesophageal capsule-sponge samples and microdissected
tissue highlight an instability signature for earlier diagnosis of oesophageal
squamous cancer**

## Repository contents

- `scripts/capsule_sponge_resubmission_analysis.Rmd`
  - Main capsule-sponge copy-number analysis, diagnostic modelling, sensitivity
    analyses, figure generation and microdissected ESD analyses.
- `scripts/capsule_sponge_elastic_net_feature_selection.Rmd`
  - Elastic-net feature-selection and robustness analysis used to evaluate
    chromosome-arm predictors.
- `data/README.md`
  - Description of the controlled-access input files required to run the code.
- `data/example/`
  - Synthetic schema examples only. These are not study data and cannot be used
    to reproduce the reported results.
- `PREPROCESSING.md`
  - Summary of the upstream sequencing and copy-number preprocessing workflow
    used to generate the analysis-ready input files.
- `PARAMETERS.md`
  - Key analysis settings and model parameters.
- `environment/`
  - Information on the R and software environment used for the analyses.

## Data access

Participant-derived sequencing and clinical data are **not included in this
public code repository**. The study data are subject to controlled access.

Authorised users should obtain the processed study data from the repository
identified in the manuscript Data Availability statement and place the following
files in the local `data/` directory using these exact filenames:

1. `capsule_sponge_50kb_segmented.tsv`
2. `clinical_metadata.tsv`
3. `esd_segments.tsv`

The `clinical_metadata.tsv` file contains the final analysis-ready clinical
metadata used for the reported analyses.

The `.gitignore` file is configured to prevent study-data files, generated
results and figures from being committed accidentally.

## Running the analyses

Run the R Markdown files from the repository root.

### Main analysis

Render:

`./scripts/capsule_sponge_resubmission_analysis.Rmd`

This script requires the three controlled-access input files listed above and
creates analysis outputs in `results/` and `figures/`. It also generates:

`results/capsulesponge_gw_burden_df.rds`

which is required by the elastic-net feature-selection analysis.

### Elastic-net feature-selection analysis

After running the main analysis, render:

`./scripts/capsule_sponge_elastic_net_feature_selection.Rmd`

This script requires:

- `data/capsule_sponge_50kb_segmented.tsv`
- `data/clinical_metadata.tsv`
- `results/capsulesponge_gw_burden_df.rds`

Outputs from this analysis are written to:

`results/elastic_net_model/`

## Software environment

Exact R and package versions used for the final analysis are provided in
`environment/sessionInfo.txt`. Additional information is provided in
`environment/README.md`.

## Citation

The version of the code corresponding to the published manuscript is archived
in Zenodo.

GitHub: https://github.com/ay327/capsule-sponge-sWGS-analysis

Archived release: https://doi.org/10.5281/zenodo.23423132