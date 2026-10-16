# Controlled-access input data

The analysis scripts require three participant-derived study-data files in this
directory. These files are subject to controlled access and are **not included**
in the public GitHub repository.

Authorised users should obtain the study data through the repository and access
procedure described in the manuscript Data Availability statement and place the
files in the local `data/` directory using the exact filenames below.

## 1. capsule_sponge_50kb_segmented.tsv

Processed capsule-sponge shallow whole-genome sequencing (sWGS) copy-number data
in wide format.

Expected content:

- genomic chromosome
- bin start coordinate
- bin end coordinate
- chromosome-arm annotation
- one segmented relative copy-number column per sequencing library

The study file contains participant-derived genomic profiles and sequencing
library identifiers and should remain in the approved controlled-access data
repository.

## 2. clinical_metadata.tsv

Final analysis-ready metadata used to map capsule-sponge sequencing libraries to
study specimens, participants, clinical outcomes and covariates.

The file used by the analysis scripts contains variables including:

`sequencing_ID`, `specimen_ID`, `case_ID`, `age`, `sex`, `bmi`, `chest_rth`,
`group`, `endoscopy_outcome_binarized`, `endoscopy_outcome_trichotomize`,
`cytosponge_definite_sq_atypia`, `p53_staining_binarized`, and
`smoking_binary`.

This file contains participant-level clinical information together with
pseudonymous study identifiers and should remain in the approved
controlled-access data repository.

## 3. esd_segments.tsv

Processed 50-kb segmented copy-number data for microdissected endoscopic
submucosal dissection (ESD) regions in long format, with specimen and pathology
annotations.

Expected variables include:

`chromosome`, `start`, `end`, `chromosomal_arm`, `SequencingID`,
`segmented_CN`, `CaseID`, `SpecimenID`, `Specimen_pathology`,
`Sequencingbatch`, `SequencingID(barcodeonly)`,
`metadatasheet_sample_sequence`, and `Specimenphenotype`.

This file contains participant-derived genomic data together with pseudonymous
case, specimen and sequencing identifiers and should remain under controlled
access.

## Synthetic examples

Files in `data/example/` contain invented identifiers and values and are provided
only to illustrate the expected file structure. They are not study data and
cannot be used to reproduce the reported results.
