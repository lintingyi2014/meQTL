#General

##Use snakefile as main pipeline and defines paths for files and directives 

##Conda environment 
Run pipeline in Conda specified env 
Install Github ver of matrix-EQTL (manually)
Install annotation package for methylation hg19 (manually)

1. install the conda environment found under `envs/rbio.yaml` (conda has to be installed on the system):
```
conda env create -f envs/rbio.yaml
``` 
2. Activate env after installation 
```
conda activate rbio
``` 

