# Manual
##### Description
RNA-seq pipeline (CPU)

### STEP 1 : Quality checking
```ruby
fastqc 'your_data'_1.fastq 
fastqc 'your_data'_2.fastq 
```
### STEP 2 : Trimming
```ruby
trimmomatic PE -threads 6 -phred33 -trimlog trimmolog1.txt 'your_data'_1.fastq 'your_data'_2.fastq 'your_data'_1_trimmo_paired.fastq 'your_data'_1_trimmo_unpaired.fastq  'your_data'_2_trimmo_paired.fastq 'your_data'_2_trimmo_unpaired.fastq ILLUMINACLIP:'your path'/adapters/TruSeq3-PE-2.fa:2:30:10
```
### STEP 3 : Mapping
#### Mapping (1): HISAT2
```ruby
hisat2 -p 6 -q --no-mixed --no-discordant --dta -x 'your_path/Reference_genome' -1 'your_data'_1_trimmo_paired.fastq -2 'your_data'_2_trimmo_paired.fastq -S 'your_data'.sam
```

#### Mapping (2): STAR
##### Building index
```ruby
wget https://hgdownload.soe.ucsc.edu/goldenPath/'your_reference'.fa.gz
wget https://hgdownload.soe.ucsc.edu/goldenPath/'your_reference'.ncbiRefSeq.gtf.gz
```
##### Mapping process

```ruby
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
### STEP 4 : Sorting

```ruby
samtools sort -o 'your_data'_sorted.bam 'your_data'.sam
```
### STEP 5 : Duplicate removal

```ruby
picard MarkDuplicates INPUT='your_data'_sorted.bam OUTPUT='your_data'_sorted_rmdup.bam METRICS_FILE=dup.txt VALIDATION_STRINGENCY=LENIENT REMOVE_DUPLICATES=true > 'your_data'_markdup_stderr_renamed_hisat_dta_nomixed.txt
```

### STEP 6 : ?? 


```ruby
samtools flagstat 'your_data'_sorted_rmdup.bam

```
### STEP 7 : Indexing

```ruby
samtools index 'your_data'_sorted_rmdup.bam
```
### STEP 8 :Transcription level estimation

```ruby
stringtie 'your_data'_sorted_rmdup.bam -G 'your path'/'your_reference'.annotated.gtf -p 6 -e -B -A 'your_data'_sorted_rmdup_bam.txt -o 'your_data'_sorted_rmdup.gtf

```
