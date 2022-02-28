# Manual
##### Description
ChIP-seq pipeline (GPU-HPC)

The following template provides a comprehensive set of SBATCH parameters to give users better understanding of the cluster resources.
For the complete information about SBATCH: https://slurm.schedmd.com/sbatch.html.

| Argument | Description | Default
|---|---|---|
|`SBATCH --job-name` |           Job name		  |*default: script name or sbatch*|
|`SBATCH --ntasks`      |              Number of tasks		 | *default: 1 task per node*
|`SBATCH --cpus-per-task`|             Number of CPUs per task	 | *default: 1 CPU per task*
|`SBATCH --mem `       |            Memory size requested	 | *default: 4gb*
|`SBATCH --time `     |         Time limit hrs:min:sec	 | *default: 01:00:00 (+1 hours of extra overtime limit)*
|`SBATCH --output`|           Output file		 | *default: slurm-<jobid>.out*
|`SBATCH --gres   `       |        Number of GPUs requested  |*default: none (0)*
|`SBATCH --nodes   `           | Req min-max of nodes      |*default: 1-as many as possible to satisfy the job without delay*
|`SBATCH --partition	`      | Req specific partition   | *default: batch*
|`SBATCH --export	`	  |    Pass the env var

### STEP 1 : STAR alignment + Coordinate Sorting and Mark Duplicates
```ruby
#!/bin/bash
#SBATCH --job-name=rna_fq2bamSRR            # Job name		  # default: script name or sbatch
#SBATCH --ntasks=4                    # Number of tasks		  # default: 1 task per node
#SBATCH --cpus-per-task=10             # Number of CPUs per task	  # default: 1 CPU per task 
#SBATCH --mem=128gb                    # Memory size requested	  # default: 4gb
#SBATCH --time=5:00:00               # Time limit hrs:min:sec	  # default: 01:00:00 (+1 hours of extra overtime limit) 
#SBATCH --output=my_job%j.log           # Output file		  # default: slurm-<jobid>.out
#SBATCH --gres=gpu:1                  # Number of GPUs requested  # default: none (0)
#SBATCH --nodes=1              # Req min-max of nodes      # default: 1-as many as possible to satisfy the job without delay
#SBATCH --partition=batch	      # Req specific partition    # default: batch
#SBATCH --export=ALL		      # Pass the env var

export MODULEPATH=/shared/software/modules:$MODULEPATH
module load parabricks/3.7.0-1.ampere

pbrun fq2bam --ref 'your_path/Reference_genome/Reference_genome.fa \
--in-fq 'your_path/your_data'_1.fastq 'your_path/your_data'_2.fastq  \
--out-bam 'your_path/your_data.bam' \
--tmp-dir 'your_path/your_data_tmp'

```
