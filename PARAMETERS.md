# Key analysis parameters

This file summarises key analysis settings and decision rules explicitly encoded
in the supplied R Markdown scripts.

## General

- Random seed used in the main analysis: `123`
- Random seed used for repeated diagnostic-model resampling: `567`
- Copy-number bin size: 50 kb

## Capsule-sponge GW-CNA framework

- Per-bin alteration reference: healthy-control distribution
- Arm-wise bounds: median ± 1.5 × IQR
- Binary high GW-CNA burden threshold: 95th percentile of the healthy-control
  GW-CNA burden distribution

## Diagnostic model evaluation

- Cross-validation: repeated stratified 5-fold cross-validation
- Repeats: 10
- Random seed for the shared resampling folds: `567`

## Elastic-net feature selection

- Alpha grid: 0.0 to 1.0 in increments of 0.1
- For each alpha: 10 runs of 5-fold cross-validation
- Initial random seed: `123`
- Run-specific seeds: `123 + i`, where `i` ranges from 1 to 10
- Accuracy and sparsity are evaluated using `lambda.1se`
- Alpha-selection tolerance: 0.002 absolute accuracy
  (0.2 percentage points below the best mean accuracy)
- Within the accuracy plateau, alpha is selected according to the
  sparsity-based rule encoded in the script
- The final lambda is selected from the candidate `lambda.1se` values using a
  50:50 composite of predictive accuracy and sparsity

## Elastic-net robustness and final feature narrowing

- Leave-one-out refitting is performed using the selected fixed alpha and lambda
- Robust-feature inclusion threshold: non-zero coefficient in at least 70% of
  leave-one-out refits
- Minimum coefficient sign consistency: 0.70
- Effect-size stability metric: coefficient of variation of relative risk
  (`cvRR`)
- Feature-prioritisation score: 50% normalised absolute coefficient magnitude
  and 50% normalised `cvRR`
- Priority threshold: top quartile of the composite score
- Final fixed genomic panel: features meeting both the leave-one-out robustness
  criteria and the top-quartile composite-score criterion

## Multiple-comparison procedures

- Benjamini-Hochberg correction is used for specified capsule-sponge Dunn
  post-hoc analyses.
- Hochberg correction is used for the ESD GW-CNA Dunn post-hoc analysis.
- Where explicitly calculated in the ESD trend analyses, adjusted P values are
  reported according to the correction procedures encoded in the analysis
  script.

## GEE sensitivity analyses

- Family: binomial
- Link: logit
- Working correlation structure: independence
