## Report of performance between GPU and CPU

###### Processing : MU-AI HPC (CPU 10, node 1, memory 64 GB)<br>Server : k8smaster1/omega (IP Address 10.134.1.9)<br>Sample : ChIP-seq (SRR18027086 and SRR18027089)

Steps/files created | Programs/Tools | real
--- | --- | --- |

SRR18027086_1|	Fastqc|	0m21.735s
SRR18027086_2|	Fastqc|	0m21.272s
SRR18027089_1|	Fastqc|	0m20.770s
SRR18027089_2|	Fastqc|	0m20.797s
SRR18027086|	bowtie2|	5m37.831s
SRR18027089|	bowtie2|	5m37.831s
hg38.fa | BWA index|	5m37.831s
SRR18027086 |	BWA|	5m37.831s
SRR18027089|	BWA|	5m37.831s
SRR18027086.sam|	samtools|	3m45.601s
SRR18027089.sam|	samtools|	3m45.601s
SRR18027086_sorted.bam|	samtools flagstat	|0m15.076s
SRR18027089_sorted.bam|	samtools flagstat	|0m15.076s
SRR18027086_sorted.bam|	samtools index|	0m15.911s
SSRR18027089_sorted.bam|	samtools index|	0m15.911s
SRR18027086_sorted.bam|	Bedtools|	40m46.360s
SRR18027086_sorted.bam and SRR18027089_sorted.bam|	macs2|	40m46.360s

###### Processing : CPU246 Server : Sanger17 (10.90.202.246)<br>Sample : ChIP-seq (SRR18027086 and SRR18027089)

Steps/files created | Programs/Tools | real
--- | --- | ---
fastq|	trimmomatic 	|12m40.120s
SRR10989467.1.fastq	|Fastqc	|0m41.084s
SRR10989467.2.fastq	|Fastqc	|0m40.972s
SRR10989467_1_trimmo_paired.fastq	|Fastqc|	0m40.318s
SRR10989467_2_trimmo_paired.fastq|	Fastqc	|0m38.851s
SRR10989467	|hisat2|	9m53.742s	|
SRR1089467.sam	|samtools	|10m47.832s
SRR10989467_sorted.bam	|picard	|14m33.567s
SRR10989467_sorted_rmdup.bam	|samtools flagstat	|0m33.883s
SRR10989467_sorted_rmdup.bam	|samtools index	|0m26.817s
SRR10989467_sorted_rmdup.bam	|stringtie	|14m19.681s

### Comparing time used in different GPU
SRR18027086
![image](https://github.com/vclabsysbio/AI-MD_RNASeq_ChIPseq/blob/main/RNAseq_Pipeline/Figures/No_GPU_time.png?raw=true)
|No. of GPU|Time(s)|
|---|---|
|1|24m29s|
|2|14m12s|
|3|10m9s|
|4|8m56s|

SRR18027089
![image](https://github.com/vclabsysbio/AI-MD_RNASeq_ChIPseq/blob/main/RNAseq_Pipeline/Figures/No_GPU_time.png?raw=true)
|No. of GPU|Time(s)|
|---|---|
|1|38m58s|
|2|19m52s|
|3|15m59s|
|4|13m28s|

### Comparing performance among CPU246, CPU-HPC and GPU-HCP
![image](https://github.com/vclabsysbio/AI-MD_RNASeq_ChIPseq/blob/main/RNAseq_Pipeline/Figures/Run_CPU-GPU.png)
