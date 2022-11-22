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


