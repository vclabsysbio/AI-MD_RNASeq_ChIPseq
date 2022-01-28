## Report of performance between GPU and CPU

###### Processing : MU-AI HPC (CPU 10, node 1, memory 64 GB)<br>Server : k8smaster1/omega (IP Address 10.134.1.9)<br>Sample : RNA-seq (SRR10989467)

Steps/files created | Programs/Tools | real | user | sys
--- | --- | --- | --- |--- 
fastq | Trimmomatic | 4m54.646s | 4m6.433s | 2m25.941s
SRR10989467.1.fastq|	Fastqc|	0m21.735s|	0m22.806s|	0m1.355s
SRR10989467.2.fastq|	Fastqc|	0m21.272s|	0m21.897s|	0m1.370s
SRR10989467_1_trimmo_paired.fastq|	Fastqc|	0m20.770s|	0m21.525s|	0m1.399s
SRR10989467_2_trimmo_paired.fastq|	Fastqc|	0m20.797s|	0m21.979s|	0m1.354s
SRR10989467 trim|	hisat2|	5m37.831s|	32m39.923s|	0m32.199s
SRR1089467.sam|	samtools|	3m45.601s|	3m29.151s|	0m10.682s
SRR10989467_sorted.bam|	picard|	7m46.290s|	10m23.874s|	0m16.338s
SRR10989467_sorted_rmdup.bam|	samtools flagstat	|0m15.076s|	0m14.172s|	0m0.802s
SRR10989467_sorted_rmdup.bam|	samtools index|	0m15.911s	|0m15.405s	|0m0.417s
SRR10989467_sorted_rmdup.bam|	stringtie|	40m46.360s	|41m50.743s|	0m15.878s
genomeGenerate  |	STAR|	67m11.701s	|280m10.123s	|3m42.097s
SRR10989467 mapping |	STAR|	2m55.012s|	12m42.618s|	0m31.139s		

###### Processing : CPU XX, node X, memory XX GB<br>Server : Sanger17 (10.90.202.246)<br>Sample : RNA-seq (SRR10989467)

Steps/files created | Programs/Tools | real | user | sys
--- | --- | --- | --- |--- 
fastq|	trimmomatic 	|12m40.120s	|6m31.020s	|11m4.076s
SRR10989467.1.fastq	|Fastqc	|0m41.084s	|0m41.764s	|0m2.824s
SRR10989467.2.fastq	|Fastqc	|0m40.972s		| |0m2.364s
SRR10989467_1_trimmo_paired.fastq	|Fastqc|	0m40.318s	|0m41.668s	|0m1.888s
SRR10989467_2_trimmo_paired.fastq|	Fastqc	|0m38.851s	|0m39.700s	|0m1.720s
SRR10989467	|hisat2|	9m53.742s	|52m30.204s|	5m47.388s
SRR1089467.sam	|samtools	|10m47.832s	|10m22.552s	|0m24.704s
SRR10989467_sorted.bam	|picard	|14m33.567s	|73m14.956s	|6m26.196s
SRR10989467_sorted_rmdup.bam	|samtools flagstat	|0m33.883s	|0m30.672s	|0m3.208s
SRR10989467_sorted_rmdup.bam	|samtools index	|0m26.817s	|0m26.232s	|0m0.580s
SRR10989467_sorted_rmdup.bam	|stringtie	|14m19.681s	|14m17.672s	|0m28.544s

