## Report of performance between GPU and CPU

###### Processing : MU-AI HPC (CPU 10, node 1, memory 64 GB)<br>Server : k8smaster1/omega (IP Address 10.134.1.9)<br>Sample : RNA-seq (SRR10989467)

Steps/files created | Programs/Tools | real
--- | --- | --- |
fastq | Trimmomatic | 4m54.646s
SRR10989467.1.fastq|	Fastqc|	0m21.735s
SRR10989467.2.fastq|	Fastqc|	0m21.272s
SRR10989467_1_trimmo_paired.fastq|	Fastqc|	0m20.770s
SRR10989467_2_trimmo_paired.fastq|	Fastqc|	0m20.797s
SRR10989467 trim|	hisat2|	5m37.831s
SRR1089467.sam|	samtools|	3m45.601s
SRR10989467_sorted.bam|	picard|	7m46.290s
SRR10989467_sorted_rmdup.bam|	samtools flagstat	|0m15.076s
SRR10989467_sorted_rmdup.bam|	samtools index|	0m15.911s
SRR10989467_sorted_rmdup.bam|	stringtie|	40m46.360s
genomeGenerate  |	STAR|	67m11.701s
SRR10989467 mapping |	STAR|	2m55.012s		

###### Processing : CPU XX, node X, memory XX GB<br>Server : Sanger17 (10.90.202.246)<br>Sample : RNA-seq (SRR10989467)

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
![image](https://github.com/vclabsysbio/AI-MD_RNASeq_ChIPseq/blob/main/RNAseq_Pipeline/Figures/No_GPU_time.png?raw=true)
|No. of GPU|Time(s)|
|---|---|
|1|4m16s|
|2|3m0s|
|3|2m33s|
|4|2m32s|
