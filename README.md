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

stephanieperez@MacBook-Pro-2 ~/D/D/21sp_advgenomics> cd 21SPStephGAdvancedGenomicsLog/
stephanieperez@MacBook-Pro-2 ~/D/D/2/21SPStephGAdvancedGenomicsLog> ls
README.md
stephanieperez@MacBook-Pro-2 ~/D/D/2/21SPStephGAdvancedGenomicsLog>  git add README.md 
stephanieperez@MacBook-Pro-2 ~/D/D/2/21SPStephGAdvancedGenomicsLog> 
git commit -m 'updating with day02 exercises'
[main 552e36f] updating with day02 exercises
 1 file changed, 81 insertions(+)
stephanieperez@MacBook-Pro-2 ~/D/D/2/21SPStephGAdvancedGenomicsLog> git push -u origin main
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 8 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 1.37 KiB | 1.38 MiB/s, done.
Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
To https://github.com/lorenapr92/21SPStephGAdvanceGenomicslog.git
   e726f87..552e36f  main -> main
Branch 'main' set up to track remote branch 'main' from 'origin'.

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
inside shell script
#!/bin/bash -l                                                                                              

#SBATCH -o stephgzfastqcopy.txt                                                                              
#SBATCH -n 1                                                                                                 
#SBATCH --mail-user=spere004@odu.edu                                                                         
#SBATCH --mail-type=END                                                                                      
#SBATCH --job-name=StephGZfq                                                                                 

gunzip /cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/StephG/data/*.fastq.gz

[spere004@turing1 data]$ sbatch StephGZfq.sh
Submitted batch job 9268787
[spere004@turing1 data]$ squeue -u spere004
             JOBID PARTITION     NAME     USER ST       TIME  NODES NODELIST(REASON) 
           9268786      main       sh spere004  R       7:52      1 coreV3-23-024 
           9268787      main StephGZf spere004  R       0:25      1 coreV1-22-005 

[spere004@turing1 data]$ ls
HADB01-A_S17_L002_R1_001.fastq     HADB03-C_S51_L004_R1_001.fastq.gz  HADB05-F_S86_L006_R1_001.fastq.gz
HADB01-B_S18_L002_R1_001.fastq     HADB03-D_S52_L004_R1_001.fastq.gz  HADB05-G_S87_L006_R1_001.fastq.gz
HADB01-C_S19_L002_R1_001.fastq     HADB03-E_S53_L004_R1_001.fastq.gz  HADB05-H_S88_L006_R1_001.fastq.gz
HADB01-D_S20_L002_R1_001.fastq     HADB03-F_S54_L004_R1_001.fastq.gz  HADB05-I_S89_L006_R1_001.fastq.gz
HADB01-E_S21_L002_R1_001.fastq     HADB03-G_S55_L004_R1_001.fastq.gz  HADB05-J_S90_L006_R1_001.fastq.gz
HADB01-F_S22_L002_R1_001.fastq  

DAY03
1. cp -r /cm/shared/courses/dbarshis/21AdvGenomics/assignments_exercises/day03 ./
pwd
/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/StephG/data
2. mkdir fastq
mv *.fastq fastq/
ls
cd fastq/
ls
3. cp renamingtable_complete.txt /cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/StephG/data/fastq
/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/StephG/scripts
cp /cm/shared/courses/dbarshis/21AdvGenomics/scripts/renamer_advbioinf.py ./
less renamer_advbioinf.py 
4. module load python
python renamer_advbioinf.py /cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/StephG/data/fastq/renamingtable_complete.txt /cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/StephG/data/fastq/*.fastq


5. nano renamer_advbioinf.py
#!/usr/bin/env python
####usage renamer.py renamingtable
#### this script take the entries in the first column of table and renames (mv's) them to files with the nam$
import sys
import os

fin=open(sys.argv[1],'r')
linecount=0
for line in fin:
        linecount+=1
        if linecount>=2:
                cols=line.rstrip().split('\t')
#               print 'mv %s %s' %(cols[0], cols[1])
                os.popen('mv %s %s' %(cols[0], cols[1]))

6. nano Steph_Renamer.sh
#!/bin/bash -l

#SBATCH -o steph_renamercopy.txt
#SBATCH -n 1
#SBATCH --mail-user=spere004@odu.edu
#SBATCH --mail-type=END
#SBATCH --job-name=Steph_Renamer

python /cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/StephG/scripts/renamer_advbioinf.py renamingtable_complete.txt

sbatch Steph_Renamer.sh 
Submitted batch job 9271073

7. DONE

[spere004@turing1 scripts]$ pwd
/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/StephG/scripts
10. cp /cm/shared/courses/dbarshis/21AdvGenomics/scripts/Trimclipfilterstatsbatch_advbioinf.py ./
11. less Trimclipfilterstatsbatch_advbioinf.py

