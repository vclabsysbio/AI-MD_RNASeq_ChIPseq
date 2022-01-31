# Manual
##### Description

# Installation

### Quality checking : FastQC (For Pair-End RNA-seq dataset)<br>
Input file : 
* `'your_data'_1.fastq` 
* `'your_data'_2.fastq` 
```
fastqc 'your_data'_1.fastq 
fastqc 'your_data'_2.fastq 
```
### Trimming : Trimmomatic
Input file : 
* `'your_data'_1.fastq`<br>
* `'your_data'_2.fastq`<br>

Output file :
* `'your_data'_1_trimmo_paired.fastq`
* `'your_data'_1_trimmo_unpaired.fastq`
* `'your_data'_2_trimmo_paired.fastq`
* `'your_data'_2_trimmo_unpaired.fastq`
* `trimmolog1.txt` for exporting report <br>
Directory : `'your path'/adapters/TruSeq3-PE-2.fa`
```
trimmomatic PE -threads 6 -phred33 -trimlog trimmolog1.txt 'your_data'_1.fastq 'your_data'_2.fastq 'your_data'_1_trimmo_paired.fastq 'your_data'_1_trimmo_unpaired.fastq  'your_data'_2_trimmo_paired.fastq 'your_data'_2_trimmo_unpaired.fastq ILLUMINACLIP:'your path'/adapters/TruSeq3-PE-2.fa:2:30:10
```
### Mapping
#### Mapping (1): HISAT2
Input file : 
* `'your_data'_1_trimmo_paired.fastq`<br>
* `'your_data'_2_trimmo_paired.fastq`<br>

Output file :
* `'your_data'.sam` <br>
Directory : `'your_path/Reference_genome'`
```
hisat2 -p 6 -q --no-mixed --no-discordant --dta -x 'your_path/Reference_genome' -1 'your_data'_1_trimmo_paired.fastq -2 'your_data'_2_trimmo_paired.fastq -S 'your_data'.sam
```

#### Mapping (1): HISAT2
##### Building index
```
wget https://hgdownload.soe.ucsc.edu/goldenPath/'your_reference'/bigZips/hg38.fa.gz
wget https://hgdownload.soe.ucsc.edu/goldenPath/'your_reference'/bigZips/genes/hg38.ncbiRefSeq.gtf.gz
```
##### Mapping process
Input file : 
* `'your_data'_1_trimmo_paired.fastq` 
* `'your_data'_2_trimmo_paired.fastq`

Output file :
* `'your_data'.bam`

Directory : 
* `'your_path/Reference_genome'` 
* `'your_path/Reference_genome/Reference_genome.fa'`
* `'your_path/Reference_genome/Reference_genome.ncbiRefSeq.gtf'`
* `'your_path/sample_test'`

```
STAR --runThreadN 6 \
--runMode genomeGenerate \
--genomeDir 'your_path/Reference_genome' \
--genomeFastaFiles 'your_path/Reference_genome/Reference_genome.fa' \
--sjdbGTFfile  'your_path/Reference_genome/Reference_genome.ncbiRefSeq.gtf' \
--sjdbOverhang 99

STAR --genomeDir /home/peerapat.kha/hg38STAR/ \
--runThreadN 6 \
--readFilesIn 'your_data'_1_trimmo_paired.fastq 'your_data'_2_trimmo_paired.fastq \
--outFileNamePrefix sample_test/'your_data' \
--outSAMtype BAM SortedByCoordinate
```
