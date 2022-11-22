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
4. Install 1) devtools + MatrixEQTL and 2) annotation template
```
# matrixEQTL
install.packages("devtools")
devtools::install_github("andreyshabalin/MatrixEQTL")
# annotation package
BiocManager::install("IlluminaHumanMethylationEPICanno.ilm10b2.hg19")
```
## Configuration
* `maf` : the minor allele frequency threshold   
> Converting impute2 genotypes to dosages.
* `post_maf` : the minor allele frequency threshold to be applied after matrixEQTL has been run.  
> Useful to define different summaries.
* `cisDist` : the maximal distance between SNP-CpGs pairs until which it counts as a 'cis-pairs'.   
> Cis-pairs will be reported in a separate file.
* `pvThresholdCis` : The *P* value threshold to be applied for cis-meQTLs.   
> Only associations with *P* value < pvThresholdCis will be reported
* `pvThresholdTrans` : The p-value threshold to be applied for trans-meQTLs.   
> Only associations with *P* value < pvThresholdTrans will be reported
* `significant_pv_cutoff` : For final results files.  
> *P* value significant threshold e.g.: 1e-14

## Execution
Execute `snakemake` in the project directory to run the full pipeline  
Manually call the `all_dosage_to_matrixEQTL` and the `all_methylation_to_matrixEQTL` rules   
 
Run snakemake with parallel task processing
```
./scripts/run_pipeline.sh <num-parallel-tasks>
```
Configure the script above to your VM capacity with: 
`[scripts/run_pipeline.sh](scripts/run_pipeline.sh)` 

## Covariates 
```
meth ~ geno + sex + age + bmi + wbc + PCs1..20 + houseman estimates (except gran) + plate + batch
```
