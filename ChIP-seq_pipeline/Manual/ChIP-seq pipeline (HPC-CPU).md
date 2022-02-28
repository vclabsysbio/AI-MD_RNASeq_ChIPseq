# Manual
##### Description
ChIP-seq pipeline (CPU-HPC)<br>
The script of mapping follows the link [RNAseq_Pipeline/Manual/Manual_RNA-seq pipeline (CPU).md](https://github.com/vclabsysbio/AI-MD_RNASeq_ChIPseq/blob/main/ChIP-seq_pipeline/Manual/ChIP-seq%20pipeline%20(CPU).md)

### STEP 1 : install shpc
```ruby
git clone https://github.com/singularityhub/singularity-hpc  ##Get shpc package
shpc show  ## show all registry you can download and install
shpc list # show registry you have already downloaded 
```
###  STEP 2 : install tools for RNA-seq analysis
```ruby

#Fastqc
#Ref https://singularityhub.github.io/singularity-hpc/r/quay.io-biocontainers-fastqc/
shpc install quay.io/biocontainers/fastqc

#Bowtie2
#Ref  https://singularityhub.github.io/singularity-hpc/r/biocontainers-bowtie2/
shpc install biocontainers/bowtie2

#Samtools
#Ref https://singularityhub.github.io/singularity-hpc/r/biocontainers-samtools/
shpc install biocontainers/samtools

#genomeCoverageBed
#Ref https://singularityhub.github.io/singularity-hpc/r/ghcr.io-autamus-bedtools2/
shpc install ghcr.io/autamus/bedtools2

#BWA 
#Ref https://singularityhub.github.io/singularity-hpc/r/biocontainers-bwa/
shpc install biocontainers/bwa

#MACS2 from Docker 
#Ref https://hub.docker.com/r/dceoy/macs2/
singularity pull macs2.sif docker://docker.io/dceoy/macs2

#SRA toolskit
singularity pull sratoolskit.sif docker://docker.io/ncbi/sra-tools

```
###  STEP 3 : Export module directory
```ruby
module use ~/singularity-hpc/modules
#module spider ## for module detial 
```

###  STEP 4 : Load modules
```ruby
module load quay.io/biocontainers/fastqc/0.11.9--0/module
module load biocontainers/samtools/v1.9-4-deb_cv1/module
module load biocontainers/bowtie2/v2.4.1_cv1/module
module load biocontainers/bwa/0.7.15/module
module load ghcr.io/autamus/bedtools2/2.30.0/module

```
