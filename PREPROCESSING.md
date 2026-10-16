# Upstream sequencing and copy-number preprocessing

The analysis code in this repository begins from the processed, analysis-ready
input files described in `data/README.md`.

Upstream sequencing and copy-number preprocessing was performed using standard
bioinformatics software before the downstream R analyses contained in this
repository.

The workflow comprised:

1. sequencing quality assessment;
2. alignment to the GRCh37 human reference genome;
3. alignment and BAM processing;
4. shallow whole-genome copy-number processing using QDNAseq with 50-kb bins;
5. segmentation;
6. chromosome-arm annotation;
7. generation of the analysis-ready tables used by the supplied R scripts.

## Software

Software versions that can be verified from the archived analysis environment
include:

- BWA-MEM: 0.7.17
- Picard: 2.27.4
- SAMtools: 1.15
- QDNAseq: 1.36.0
- DNAcopy: 1.70.0
- GenomicRanges: 1.54.0
- BEDTools: version not recorded in the archived analysis environment
- FastQC: version not recorded in the archived analysis environment

Historical software versions that cannot be verified have not been replaced
retrospectively with newly installed versions.

## Chromosome-arm annotation

Chromosome-arm annotation was performed using BEDTools intersection of the
50-kb bins with an arm-level cytoband annotation.

The archived command was:

```bash
bedtools intersect \
  -a S02_50kb_bins_sorted.bed \
  -b cytoBand_armLevel_vo1.bed \
  -loj \
  > S03_50kb_bins_arminfo.txt
```

## Downstream analysis inputs

The resulting  files required by the downstream analyses are:

- `data/capsule_sponge_50kb_segmented.tsv`
- `data/clinical_metadata.tsv`
- `data/esd_segments.tsv`

These participant-derived files are not distributed through the public GitHub
repository and are subject to the controlled-access procedure described in the
manuscript Data Availability statement.
