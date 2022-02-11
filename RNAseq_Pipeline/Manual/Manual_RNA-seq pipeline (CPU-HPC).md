# Manual
##### Description
RNA-seq pipeline (CPU-HPC)<br>
The script follows the link [RNAseq_Pipeline/Manual/Manual_RNA-seq pipeline (CPU).md](https://github.com/vclabsysbio/AI-MD_RNASeq_ChIPseq/blob/main/RNAseq_Pipeline/Manual/Manual_RNA-seq%20pipeline%20(CPU).md)

### STEP 1 : install shpc
```ruby
git clone https://github.com/singularityhub/singularity-hpc  ##Get shpc package
shpc show  ## show all registry you can download and install
shpc list # show registry you have already downloaded 
```
###  STEP 2 : install tools for RNA-seq analysis
```ruby
##Trimmomatic
#Ref : https://singularityhub.github.io/singularity-hpc/r/quay.io-biocontainers-trimmomatic/
shpc install quay.io/biocontainers/trimmomatic

#Fastqc
#Ref : https://singularityhub.github.io/singularity-hpc/r/quay.io-biocontainers-fastqc/
shpc install quay.io/biocontainers/fastqc

#Hisat2
#Ref https://singularityhub.github.io/singularity-hpc/r/ghcr.io-autamus-hisat2/
shpc install ghcr.io/autamus/hisat2  #require reference .ht

#Samtools
#Ref https://singularityhub.github.io/singularity-hpc/r/biocontainers-samtools/
shpc install biocontainers/samtools

#Picard 
#Ref https://singularityhub.github.io/singularity-hpc/r/biocontainers-picard/ 
shpc install biocontainers/picard

#Stringtie 
#Ref https://singularityhub.github.io/singularity-hpc/r/ghcr.io-autamus-stringtie/
shpc install ghcr.io/autamus/stringtie # require reference .gtf

#STAR
#Ref https://singularityhub.github.io/singularity-hpc/r/quay.io-biocontainers-star/
shpc install quay.io/biocontainers/star
```
###  STEP 3 : Export module directory
```ruby
module use ~/singularity-hpc/modules
#module spider ## for module detial 
```

###  STEP 4 : Load modules
```ruby
module load quay.io/biocontainers/trimmomatic/0.39--0/module
module load quay.io/biocontainers/fastqc/0.11.9--0/module
module load ghcr.io/autamus/hisat2/2.2.0/module
module load biocontainers/samtools/v1.9-4-deb_cv1/module
module load biocontainers/picard/v1.139_cv3/module
module load ghcr.io/autamus/stringtie/2.1.7/module
module load quay.io/biocontainers/star/2.7.9a--h9ee0642_0/module
```
