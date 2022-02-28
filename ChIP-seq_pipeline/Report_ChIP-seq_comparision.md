## Report of performance between GPU and CPU

###### Processing : MU-AI HPC (CPU 10, node 1, memory 64 GB)<br>Server : k8smaster1/omega (IP Address 10.134.1.9)<br>Sample : ChIP-seq (SRR18027086 and SRR18027089)

Steps/files created | Programs/Tools | real
--- | --- | --- |
SRR18027086_1|	Fastqc|	2m3.906s
SRR18027086_2|	Fastqc|	2m2.770s
SRR18027089_1|	Fastqc|	2m49.765s
SRR18027089_2|	Fastqc|	2m49.786s
SRR18027086|	bowtie2|	52m59.399s
SRR18027089|	bowtie2|	73m34.798s
hg38.fa | BWA index|	56m53.433s
SRR18027086 |	BWA|	67m0.664s
SRR18027089|	BWA|	95m14.718s
SRR18027086.sam|	samtools sort|	7m51.202s
SRR18027089.sam|	samtools sort|	10m47.672s
SRR18027086_sorted.bam|	samtools flagstat	|0m35.283s
SRR18027089_sorted.bam|	samtools flagstat	|0m47.864s
SRR18027086_sorted.bam|	samtools index|	0m36.325s
SSRR18027089_sorted.bam|	samtools index|	0m48.468s
SRR18027086_sorted.bam|	Bedtools|	6m56.071s
SRR18027086_sorted.bam and SRR18027089_sorted.bam|	macs2|	10m41.784s

###### Processing : CPU246 Server : Sanger17 (10.90.202.246)<br>Sample : ChIP-seq (SRR18027086 and SRR18027089)

Steps/files created | Programs/Tools | real
--- | --- | ---
SRR18027086_1|	Fastqc|	4m23.841s
SRR18027086_2|	Fastqc|	5m27.860s
SRR18027089_1|	Fastqc|	20m40.407s
SRR18027089_2|	Fastqc|	9m31.138s
SRR18027086|	bowtie2|	119m34.830s
SRR18027089|	bowtie2|	130m52.938s
hg38.fa | BWA index|	111m28.182s
SRR18027086 |	BWA|	38m17.264s
SRR18027089|	BWA|	50m25.024s
SRR18027086.sam|	samtools sort|	28m29.187s
SRR18027089.sam|	samtools sort|	40m50.788s
SRR18027086_sorted.bam|	samtools flagstat	|1m0.182s
SRR18027089_sorted.bam|	samtools flagstat	|1m45.105s
SRR18027086_sorted.bam|	samtools index|	1m33.081s
SSRR18027089_sorted.bam|	samtools index|	1m29.192s
SRR18027086_sorted.bam|	Bedtools|	12m6.249s
SRR18027086_sorted.bam and SRR18027089_sorted.bam|	macs2|	20m7.530s

### Comparing time used in different GPU for ChIP-seq pipeline
SRR18027086

![image](https://github.com/vclabsysbio/AI-MD_RNASeq_ChIPseq/blob/main/ChIP-seq_pipeline/Figures/GPU_SRR18027086.png)
|No. of GPU|Time(s)|
|---|---|
|1|24m29s|
|2|14m12s|
|3|10m9s|
|4|8m56s|

SRR18027089

![image](https://github.com/vclabsysbio/AI-MD_RNASeq_ChIPseq/blob/main/ChIP-seq_pipeline/Figures/GPU_SRR18027089.png)
|No. of GPU|Time(s)|
|---|---|
|1|38m58s|
|2|19m52s|
|3|15m59s|
|4|13m28s|

### Comparing performance among CPU246, CPU-HPC and GPU-HCP
![image](https://github.com/vclabsysbio/AI-MD_RNASeq_ChIPseq/blob/main/RNAseq_Pipeline/Figures/Run_CPU-GPU.png)
