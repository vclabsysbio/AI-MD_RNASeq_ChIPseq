# AI-MD_RNASeq_ChIPseq
CPU-HPC project (2022)

## Description
This repository contains scripts used for RNA-sequencing and ChIP-sequencing analysis and report of performaces when we analyse in GPU and HPC.

## Data
Data used in this analysis was downloaded from the Sequence Read Archive (SRA) under the accession number **SRR10989467** for RNA-seq analysis and **SRR__** for ChIP-seq analysis

## Information of CPU and HPC
### Server : Sanger17 CPU (IP Address 10.90.202.246)<br>Information : -
**CPU model/make :** Intel Core Processor (Broadwell, IBRS)<br>
**Socket(s) :** 39<br>
**CPU Core :** 1<br>
**Thread per core :** 1<br>
**Total threads :** (CPU Core x Thread per core)<br>
**CPU op-mode(s) :** 32-bit, 64 bits<br>
**Byte order :** Little Endian<br>
**Vendor ID :** GenuineIntel<br>
**CPU MHz :** 2199.998

### Server : MU-AI HPC (Mahidol University) (IP Address 10.134.1.9)<br>Information : CPU-HPC (CPU 10, node 1, memory 64 GB)
**CPU model/make :** AMD EPYC 7742 64-Core Processor (Cascadelake)<br>
**Socket(s) :** 2<br>
**CPU Core :** 64<br>
**Thread per core :** 2<br>
**Total threads :** (CPU Core x Thread per core)<br>
**CPU op-mode(s) :** 32-bit, 64 bits<br>
**Byte order :** Little Endian<br>
**Vendor ID :** AuthenticAMD<br>
**CPU MHz :** 3388.619

## Tools and programs used in this analysis
- sratoolkit (2.8.2)
- Trimmomatic (0.39)
- FastQC (0.11.9)
- HiSAT2 (2.2.0)
- Samtools (1.9-4)
- Picard (1.139)
- Stringtie (2.1.7)
- STAR (2.7.9a and 2.7.1a)

Data analyses were performed on Ubuntu 20.04.3 LTS
