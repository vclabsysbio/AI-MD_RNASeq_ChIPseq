# Manual
##### Description
ChIP-seq pipeline (CPU)

### STEP 1 : Quality checking
```ruby
fastqc 'your_data'_1.fastq 
fastqc 'your_data'_2.fastq 
```

### STEP 2 : Mapping
#### Mapping (1): Bowtie2
```ruby
bowtie2 -x 'genome reference' --phred33 -p P-value -1 'your_data'_1.fastq -2 'your_data'_2.fastq -S 'your_data'.sam

```

#### Mapping (2): BWA
##### Building index
```ruby
bwa index 'fasta of reference genome'
```
##### Mapping process

```ruby
bwa mem -t thred -K 10000000 'fasta of reference genome' 'your_data'_1.fastq 'your_data'_2.fastq > 'your_data'.sam
```
### STEP 4 : Sorting

```ruby
samtools sort -o 'your_data'_sorted.bam 'your_data'.sam
```
### STEP 5 : Indexing

```ruby
samtools index 'your_data'_sorted.bam
```

### STEP 6 :  Flagstat

```ruby
samtools flagstat 'your_data'_sorted.bam

```
### STEP 7 : Peak calling

```ruby
macs2 call peak -t test.bam -c control.bam -f format -g genome size -q q-value
```


