# General
Use snakefile as main pipeline and defines paths for files and directives 

## Conda environment 
Run pipeline in Conda specified env 
1. Install the conda environment found under `envs/rbio.yaml` (conda has to be installed on the system):
```
conda env create -f envs/rbio.yaml
``` 
2. Activate env after installation 
```
conda activate rbio
``` 
3. Start R terminal 
4. Install 1) devtools + MatrixEQTL and 2) `IlluminaHumanMethylationEPICanno.ilm10b2.hg19` (or other annotation template)
```
# matrixEQTL
install.packages("devtools")
devtools::install_github("andreyshabalin/MatrixEQTL")
# annotation package
BiocManager::install("IlluminaHumanMethylationEPICanno.ilm10b2.hg19")
```
## Configuration
* `maf` : the minor allele frequency threshold to be applied when converting impute2 genotypes to dosages.
* `post_maf` : the minor allele frequency threshold to be applied after matrixEQTL has been run. useful to define different summaries.
* `cisDist` : the maximal distance between SNP-CpGs pairs until which it counts as a 'cis-pairs'. cis-pairs will be reported in a separate file.
* `pvThresholdCis` : The p-value threshold to be applied for cis-meQTLs. Only associations with `p-value < pvThresholdCis` will be reported
* `pvThresholdTrans` : The p-value threshold to be applied for trans-meQTLs. Only associations with `p-value < pvThresholdTrans` will be reported
* `significant_pv_cutoff` : For final results files: at which threshold should an association be called significant? e.g.: 1e-14

