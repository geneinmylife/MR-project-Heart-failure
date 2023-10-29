# MR-project-Heart-failure
This repository contains code for reproducing the Sex-stratified transcriptome-wide Mendelian randomization examined in 'Sex-stratified genome-wide association and transcriptome-wide Mendelian randomization study reveal novel drug targets of heart failure via left ventricular ejection fraction'. In this study, we identified 32 sex-differential putative causal genes for HF/HFrEF and 27 sex-differential genes for LVEF. Three novel drug target genes showed sex-differential effects on HF/HFrEF via influencing LVEF. Our study highlighted the importance of considering sex-differential genetic effects in sex-balanced diseases such as HF, and emphasized the value of sex-stratified GWAS and MR in identifying putative novel genetic variants, causal genes, and candidate drug targets for HF, which was not identifiable using sex-combined strategy.

To start using the code, you need to install TwoSampleMR package:

install.packages("remotes") 

remotes::install_github("MRCIEU/TwoSampleMR") 

devtools::install_github("mrcieu/ieugwasr") 

The following code were used in this study:

1. Sex-combined MR analysis for HF. R: To identify causal genes for HF in the sex-combined population and subsequently investigate whether these genes exhibit sex-differential effects.

2. Sex-stratified MR analysis for HF. R: To examine sex differences in HF and extensively investigate genes with sex-differential causal effects.

3. Sex-stratified MR analysis for LVEF. R: To identify sex-differential causal genes for LVEF.

4. MR analysis testing causal effects of LVEF on HF. R: To test the causal effects between LVEF and HF/HF subtypes.

5. Male-specific MR analysis for HF subtypes. R: To identify male-specific causal genes for HFrEF and HFpEF.

6. LD check. R: To assess approximate colocalization evidence for causal genes with robust MR evidence (FDR < 0.05).
