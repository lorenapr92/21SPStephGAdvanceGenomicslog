#Stephanie Grizzard's README
#21SPStephGAdvanceGenomicsLog repository


#Exercise2
cd /cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/StephG
mkdir data
mkdir exercises
/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/StephG/exercises
cp /cm/shared/courses/dbarshis/21AdvGenomics/assignments_exercises/day02/Exercise2.fast* ./
ls -alh
13M
gunzip -c Exercise2.fasta.gz > Exercise2.fasta
ls -alh
37M
tar -zxvf Exercise2.fastq.tar.gz 
ls -alh
62M
drwxrwxrwx 2 spere004 users  142 Jan 22 06:38 .
drwxrwxrwx 5 spere004 users  141 Jan 22 06:34 ..
-rwxrwxrwx 1 spere004 users  17M Jan 22 06:37 Exercise2.fasta
-rwxr-xr-x 1 spere004 users 4.3M Jan 22 06:35 Exercise2.fasta.gz
-rw-r--r-- 1 spere004 users  18M Sep  2  2015 Exercise2.fastq
-rwxr-xr-x 1 spere004 users 4.3M Jan 22 06:35 Exercise2.fastq.tar.gz

[spere004@turing1 exercises]$ head -1 Exercise2.fasta
>scaffold10078|size20675
[spere004@turing1 exercises]$ grep -c '>' Exercise2.fasta
138
[spere004@turing1 exercises]$ head -1 Exercise2.fastq
@HS3:541:HAYTUADXX:1:1101:1297:1938 1:N:0:AGTTCC
[spere004@turing1 exercises]$ grep -c '@HS3' Exercise2.fastq
61304
[spere004@turing1 exercises]$ wc -l Exercise2.fastq
245216 Exercise2.fastq
cp /cm/shared/courses/dbarshis/21AdvGenomics/scripts/avg_cov_len_fasta_advbioinf.py /cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/StephG/scripts/

[spere004@turing1 scripts]$ salloc
salloc: Pending job allocation 9268786
salloc: job 9268786 queued and waiting for resources
salloc: job 9268786 has been allocated resources
salloc: Granted job allocation 9268786
This session will be terminated in 7 days. If your application requires
a longer excution time, please use command "salloc -t N-0" where N is the
number of days that you need.
cd /cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/StephG/exercises

[spere004@coreV3-23-024 exercises]$ /cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/StephG/scripts/avg_cov_len_fasta_advbioinf.py Exercise2.fasta
The total number of sequences is 138
The average sequence length is 126640
The total number of bases is 17476447
The minimum sequence length is 1122
The maximum sequence length is 562680
The N50 is 187037
Median Length = 92612
contigs < 150bp = 0
contigs >= 500bp = 138
contigs >= 1000bp = 138
contigs >= 2000bp = 135

#Homework2
cd /cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/StephG/data/
emacs emacs StephFQCp.sh
inside shell script
#!/bin/bash -l                                                                                               

#SBATCH -o stephfastqcope.txt                                                                                
#SBATCH -n 1                                                                                                 
#SBATCH --mail-user=spere004@odu.edu                                                                         
#SBATCH --mail-type=END                                                                                      
#SBATCH --job-name=StephFQCp                                                                                 

cp /cm/shared/courses/dbarshis/21AdvGenomics/classdata/Astrangia_poculata/originalfastqs/*.fastq.gz /cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/StephG/data

sbatch StephFQCp.sh
#Submitted batch job 9268702
squeue -u spere004
             JOBID PARTITION     NAME     USER ST       TIME  NODES NODELIST(REASON) 
           9268702      main StephFQC spere004  R       0:19      1 coreV3-23-044 

emacs StephGZfq.sh
#inside shell script

