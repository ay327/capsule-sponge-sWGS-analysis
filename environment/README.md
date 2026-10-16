# Software environment

The R and package versions used for the final analyses are recorded in
`environment/sessionInfo.txt`.

The analysis scripts use R packages including:

- tidyverse
- caret
- glmnet
- pROC
- rstatix
- ggpubr
- ggsignif
- patchwork
- cowplot
- scales
- fmsb
- geepack
- broom
- ggrepel

## Generating sessionInfo.txt

After running or rendering both analysis scripts in the exact R environment used
for the final analysis, generate the environment record from the repository root
using:

```r
sink("environment/sessionInfo.txt")

sessionInfo()

if (requireNamespace("BiocManager", quietly = TRUE)) {
  cat("\nBioconductor version:\n")
  print(BiocManager::version())
}

sink()
```

This records the R version, operating system/platform, attached packages, loaded
namespaces and Bioconductor version associated with the final analysis
environment.
