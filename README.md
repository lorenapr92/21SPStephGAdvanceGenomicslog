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
12. pwd
/cm/shared/courses/dbarshis/21AdvGenomics/assignments_exercises/day03
[spere004@turing1 day03]$ cp adapterlist_advbioinf.txt /cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/StephG/data/fastq/
13. [spere004@turing1 fastq]$ nano Steph_Trimclipfilter.sh
#!/bin/bash -l

#SBATCH -o steph_trimmerclip.txt
#SBATCH -n 4
#SBATCH --mail-user=spere004@odu.edu
#SBATCH --mail-type=END
#SBATCH --job-name=Steph_Trimmerclipfilter

python /cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/StephG/scripts/Trimclipfilterstatsbatch_advbioinf.py adapterlist_advbioinf.txt *.fastq
 
[spere004@turing1 fastq]$ sbatch Steph_Trimclipfilter.sh 
Submitted batch job 9271091

Homework04

1a.  [spere004@turing1 fastq]$ /cm/shared/courses/dbarshis/21AdvGenomics/scripts/Schafran_trimstatstable_advbioinf_clippedtrimmed.py -h
Written by Peter Schafran pscha005@odu.edu 5-Oct-2015

This script takes a stats output file from fastx_clipper and converts it into a table.

Usage: Schafran_trimstatstable.py [-c, -v, -h] inputfile.txt outputfile.txt

Options (-c and -v must be listed separately to run together):
-h	Display this help message
-c	Use comma delimiter instead of tabs
-v	Verbose mode (print steps to stdout)

1b.   pwd
/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/StephG/data/fastq/filteringstats
/cm/shared/courses/dbarshis/21AdvGenomics/scripts/Schafran_trimstatstable_advbioinf_clippedtrimmed.py trimclipstats.txt Steph_trimclipstatsout.txt
head -10 Steph_trimclipstatsout.txt 
tail -n +2 Steph_trimclipstatsout.txt | head
1c.  tail -n +2 Steph_trimclipstatsout.txt >> /cm/shared/courses/dbarshis/21AdvGenomics/classdata/Astrangia_poculata/Fulltrimclipstatstable.txt

[spere004@turing1 QCFastqs]$ pwd
/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/StephG/data/fastq/QCFastqs
3. nano Steph_clippedtrimmedbowtie.sh

#!/bin/bash -l

#SBATCH -o steph_clippedtrimmedbowtie.txt
#SBATCH -n 1
#SBATCH --mail-user=spere004@odu.edu
#SBATCH --mail-type=END
#SBATCH --job-name=Steph_clippedtrimmedbowtie

enable_lmod
module load bowtie2/2.4
for i in *_clippedtrimmed.fastq; do bowtie2 --rg-id ${i%_clippedtrimmed.fastq} \
--rg SM:${i%_clippedtrimmed.fastq} \
--very-sensitive -x /cm/shared/courses/dbarshis/21AdvGenomics/classdata/Astrangia_poculata/refassembly/Apoc_hostsym -U $i \
> ${i%_clippedtrimmedfilterd.fastq}.sam --no-unal -k 5; done

3. sbatch Steph_clippedtrimmedbowtie.sh
Submitted batch job 9271724

Homework05
#Working with John. He copied his fastq files into my sandbox. Created a list with his fast names for shell script
pwd
/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/StephG/data/fastq/QCFastqs
ls *.fastq | head -32
nano Steph_trinity.sh
#! /bin/bash -l

#SBATCH -o steph_trinity.txt
#SBATCH -n 32
#SBATCH -p himem
#SBATCH --mail-user=spere004@odu.edu
#SBATCH --mail-type=END
#SBATCH --job-name=Steph_trinity

enable_lmod
module load container_env trinity

crun Trinity --seqType fq --max_memory 768G --normalize_reads --single RI_B_05_18_clippedtrimmed.fastq,RI_B_05_22_clippedtrimmed.fastq,RI_B_06_14_clippedtrimmed.fastq,RI_B_06_22_clippedtrimmed.fastq,RI_W_05_18_clippedtrimmed.fastq,RI_W_05_22_clippedtrimmed.fastq,RI_W_06_14_clippedtrimmed.fastq,RI_W_06_22_clippedtrimmed.fastq,VA_B_05_18_clippedtrimmed.fastq,VA_B_05_22_clippedtrimmed.fastq,VA_B_06_14_clippedtrimmed.fastq,VA_B_06_22_clippedtrimmed.fastq,VA_W_05_18_clippedtrimmed.fastq,VA_W_05_22_clippedtrimmed.fastq,VA_W_06_14_clippedtrimmed.fastq,VA_W_06_22_clippedtrimmed.fastq,RI_B_02_14_clippedtrimmed.fastq,RI_B_02_18_clippedtrimmed.fastq,RI_B_02_22_clippedtrimmed.fastq,RI_B_09_SNP_clippedtrimmed.fastq,RI_W_02_14_clippedtrimmed.fastq,RI_W_02_18_clippedtrimmed.fastq,RI_W_02_22_clippedtrimmed.fastq,RI_W_09_SNP_clippedtrimmed.fastq,VA_B_02_14_clippedtrimmed.fastq,VA_B_02_18_clippedtrimmed.fastq,VA_B_02_22_clippedtrimmed.fastq,VA_B_08_SNP_clippedtrimmed.fastq,VA_W_02_14_clippedtrimmed.fastq,VA_W_02_18_clippedtrimmed.fastq,VA_W_02_22_clippedtrimmed.fastq,VA_W_09_SNP_clippedtrimmed.fastq --CPU 32

sbatch Steph_trinity.sh 
Submitted batch job 9272350
FAILED
sbatch Steph_trinity.sh
Submitted batch job 9272374
#w/o --normalized reads

#Homework06

1. [spere004@turing1 QCFastqs]$ salloc
salloc: Pending job allocation 9272855
[spere004@coreV2-22-028 QCFastqs]$ cd djbtestassembly/
[spere004@coreV2-22-028 djbtestassembly]$ ls
Trinity.fasta
 /cm/shared/apps/trinity/2.0.6/util/TrinityStats.pl Trinity.fasta
################################
## Counts of transcripts, etc.
################################
Total trinity 'genes':	20980
Total trinity transcripts:	21992
Percent GC: 46.21

########################################
Stats based on ALL transcript contigs:
########################################

	Contig N10: 1178
	Contig N20: 694
	Contig N30: 514
	Contig N40: 414
	Contig N50: 347

	Median contig length: 273
	Average contig: 356.95
	Total assembled bases: 7850006


#####################################################
## Stats based on ONLY LONGEST ISOFORM per 'GENE':
#####################################################

	Contig N10: 1027
	Contig N20: 643
	Contig N30: 486
	Contig N40: 397
	Contig N50: 336

	Median contig length: 271
	Average contig: 347.72
	Total assembled bases: 7295061
2. [spere004@coreV2-22-028 scripts]$ pwd
/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/StephG/scripts/python avg_cov_len_fasta_advbioinf.py /cm/shared/courses/dbarshis/21AdvGenomics/classdata/Astrangia_poculata/refassembly/15079_Apoc_hostsym.fasta
The total number of sequences is 15079
The average sequence length is 876
The total number of bases is 13210470
The minimum sequence length is 500
The maximum sequence length is 10795
The N50 is 881
Median Length = 578
contigs < 150bp = 0
contigs >= 500bp = 15079
contigs >= 1000bp = 3660
contigs >= 2000bp = 536

3. [spere004@coreV2-22-028 QCFastqs]$ pwd
/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/StephG/data/fastq/QCFastqs
a) grep "overall alignment rate" steph_clippedtrimmedbowtie.txt
b) grep "aligned exactly 1 time" steph_clippedtrimmedbowtie.txt | cut -d " " -f 5
c) grep "aligned exactly 1 time" steph_clippedtrimmedbowtie.txt | cut -d "%" -f 1 | cut -d "(" -f 2
d) grep "aligned >1 time" steph_clippedtrimmedbowtie.txt | cut -d "%" -f 1 | cut -d "(" -f 2

4. nano alignedstats_sg.txt
lane5_sg	2.03	1.11	235455.75	0.92
cat alignedstats_sg.txt >> /cm/shared/courses/dbarshis/21AdvGenomics/classdata/Astrangia_poculata/alignmentstatstable.txt 

5. [spere004@coreV2-22-028 data]$ pwd 
/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/StephG/data
mkdir testassembly
a) [spere004@coreV2-22-028 djbtestassembly]$ pwd
/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/StephG/data/fastq/QCFastqs/djbtestassembly
mv Trinity.fasta /cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/StephG/data/testassembly/

b) /cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/StephG/data/fastq
nano cleanup.sh
#!/bin/bash -l

#SBATCH -o cleanup.txt
#SBATCH -n 1
#SBATCH --mail-user=spere004@odu.edu
#SBATCH --mail-type=END
#SBATCH --job-name=cleanup

rm -r /cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/StephG/data/fastq/originalfastqs
rm -r /cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/StephG/data/fastq/filteringstats
rm -r /cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/StephG/data/fastq/QCFastqs/trinity_out_dir 

sbatch cleanup.sh

6.  pwd
/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/StephG/data
nano steph_blast.sh
#!/bin/bash -l

#SBATCH -o blastout.txt
#SBATCH -n 6
#SBATCH --mail-user=spere004@odu.edu
#SBATCH --mail-type=END
#SBATCH --job-name=steph_blast

enable_lmod
module load container_env blast
blastx -query Trinity.fasta -db /cm/shared/apps/blast/databases/uniprot_sprot_Sep2018 -out blastx.outfmt6 -evalue 1e-20 -num_threads 6 -max_target_seqs 1 -outfmt 6

sbatch steph_blast.sh 
Submitted batch job 9273231

7. [spere004@turing1 QCFastqs]$ pwd
/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/StephG/data/fastq/QCFastqs
head -20 RI_B_05_18_clippedtrimmed.fastq.sam
@HD	VN:1.0	SO:unsorted
@SQ	SN:TR78|c0_g1_i1_coral	LN:1109
@SQ	SN:TR78|c0_g2_i1_coral	LN:1109
@SQ	SN:TR79|c0_g1_i1_coral	LN:610
@SQ	SN:TR79|c0_g2_i1_coral	LN:1549
@SQ	SN:TR87|c0_g1_i1_coral	LN:732
@SQ	SN:TR93|c0_g1_i1_coral	LN:550

8. grep -v '@' RI_B_05_18_clippedtrimmed.fastq.sam | head
K00188:59:HMTFHBBXX:6:1101:2788:1648	0	TR47986|c1_g3_i2_sym	9	255	51M	*	0	0	CNGGCAGTATGTGCAAAATTTATCTCCTGTTCACCTTTAAGTAACTAACCA	A#<AFF-FJAFAJJJJJJFJJJFJ-FJJJFFJJFJAJJJJJJJJJFJJJJJ	AS:i:-1	XN:i:0	XM:i:1	XO:i:0	XG:i:0	NM:i:1	MD:Z:1G49	YT:Z:UU	RG:Z:RI_B_05_18
K00188:59:HMTFHBBXX:6:1101:16823:1666	16	TR47986|c1_g3_i2_sym	684	255	51M	*	0	0	TAAT

9. salloc 
salloc: Pending job allocation 9273245
salloc: job 9273245 queued and waiting for resources
salloc: job 9273245 has been allocated resources
salloc: Granted job allocation 9273245

/cm/shared/courses/dbarshis/21AdvGenomics/scripts/get_explain_sam_flags_advbioinf.py RI_B_05_*.sam
RI_B_05_18_clippedtrimmed.fastq.sam
['0', '272', '256', '16']
0 :
272 :
	read reverse strand
	not primary alignment
256 :
	not primary alignment
16 :
	read reverse strand
RI_B_05_22_clippedtrimmed.fastq.sam
['0', '272', '256', '16']
0 :
272 :
	read reverse strand
	not primary alignment
256 :
	not primary alignment
16 :
	read reverse strand


10. /cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/StephG/data/fastq/QCFastqs
nano steph_SNPcall.sh

#!/bin/bash -l

#SBATCH -o steph_SNPcall.txt
#SBATCH -n 1
#SBATCH --mail-user=spere004@odu.edu
#SBATCH --mail-type=END
#SBATCH --job-name=steph_SNPcall

enable_lmod
module load samtools/1
for i in *.sam; do `samtools view -bS $i > ${i%.sam}_UNSORTED.bam`; done

for i in *UNSORTED.bam; do samtools sort $i > ${i%_UNSORTED.bam}.bam
samtools index ${i%_UNSORTED.bam}.bam
done

sbatch steph_SNPcall.sh 
Submitted batch job 9273232

#Homework07

[spere004@turing1 data]$ pwd
/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/StephG/data/testassembly/
1. nano blast parsing.sh
#!/bin/bash -l

#SBATCH -o blastparseout.txt
#SBATCH -n 1
#SBATCH --mail-user=spere004@odu.edu
#SBATCH --mail-type=END
#SBATCH --job-name=blastparsing


/cm/shared/apps/trinity/2.0.6/util/analyze_blastPlus_topHit_coverage.pl blastx.outfmt6 Trinity.fasta /cm/shared/apps/blast/databases/uniprot_sprot_Sep2018.fasta

sbatch blastparsing.sh 
Submitted batch job 9276480

cat blastparseout.txt
#hit_pct_cov_bin        count_in_bin    >bin_below
100     143     143
90      52      195
80      77      272
70      87      359
60      110     469
50      133     602
40      219     821
30      395     1216
20      726     1942
10      674     2616

2. [spere004@turing1 QCFastqs]$ pwd
/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/StephG/data/fastq/QCFastqs
ls *_UNSORTED.bam
RI_B_05_18_clippedtrimmed.fastq_UNSORTED.bam  VA_B_05_18_clippedtrimmed.fastq_UNSORTED.bam
RI_B_05_22_clippedtrimmed.fastq_UNSORTED.bam  VA_B_05_22_clippedtrimmed.fastq_UNSORTED.bam
RI_B_06_14_clippedtrimmed.fastq_UNSORTED.bam  VA_B_06_14_clippedtrimmed.fastq_UNSORTED.bam
RI_B_06_22_clippedtrimmed.fastq_UNSORTED.bam  VA_B_06_22_clippedtrimmed.fastq_UNSORTED.bam
RI_W_05_18_clippedtrimmed.fastq_UNSORTED.bam  VA_W_05_18_clippedtrimmed.fastq_UNSORTED.bam
RI_W_05_22_clippedtrimmed.fastq_UNSORTED.bam  VA_W_05_22_clippedtrimmed.fastq_UNSORTED.bam
RI_W_06_14_clippedtrimmed.fastq_UNSORTED.bam  VA_W_06_14_clippedtrimmed.fastq_UNSORTED.bam
RI_W_06_22_clippedtrimmed.fastq_UNSORTED.bam  VA_W_06_22_clippedtrimmed.fastq_UNSORTED.bam
nano rmunsorted.sh 
#!/bin/bash -l

#SBATCH -o rmunsortout.txt
#SBATCH -n 1
#SBATCH --mail-user=spere004@odu.edu
#SBATCH --mail-type=END
#SBATCH --job-name=rmunsorted

rm *_UNSORTED.bam

sbatch rmunsorted.sh 
Submitted batch job 9276496
ls *_UNSORTED.bam
ls: No match. ##all unsorted bam files are gone.
rm rmunsorted.txt ##unnecessary txt file to keep

3. /cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/StephG/data/fastq/QCFastqs
nano steph_bayes.sh
#!/bin/bash -l

#SBATCH -o bayesout.txt
#SBATCH -n 1         
#SBATCH --mail-user=spere004@odu.edu
#SBATCH --mail-type=END
#SBATCH --job-name=steph_bayes

enable_lmod
module load dDocent
freebayes --genotype-qualities -f /cm/shared/courses/dbarshis/21AdvGenomics/classdata/Astrangia_poculata/refassembly/15079_Apoc_hostsym.fasta *.bam > SGmergedfastqs.vcf

sbatch steph_bayes.sh 
Submitted batch job 9276570


##Homework08

1. /cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/StephG/data
mkdir BAMs
mkdir SAMs
mkdir VCF
salloc
salloc: Pending job allocation 9278250
salloc: job 9278250 queued and waiting for resources
salloc: job 9278250 has been allocated resources
salloc: Granted job allocation 9278250
/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/StephG/data/fastq/QCFastqs
mv *.sam /cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/StephG/data/SAMs/
mv *.bam *.bam.bai /cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/StephG/data/BAMs/
NO unfiltered vcfs
rm *.fastq

enable_lmod
module load dDocent
vcftools

3. [spere004@turing1 VCF]$ pwd
/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/StephG/data/VCF
cp /cm/shared/courses/dbarshis/21AdvGenomics/classdata/Astrangia_poculata/VCF/mergedfastq_HEAAstrangiaAssembly.vcf ./

4. [spere004@turing1 VCF]$ /cm/shared/apps/vcftools/0.1.12b/bin/vcftools --vcf mergedfastq_HEAAstrangiaAssembly.vcf

VCFtools - v0.1.12b
(C) Adam Auton and Anthony Marcketta 2009

Parameters as interpreted:
	--vcf mergedfastq_HEAAstrangiaAssembly.vcf

After filtering, kept 40 out of 40 Individuals
After filtering, kept 1214003 out of a possible 1214003 Sites
Run Time = 10.00 seconds

[spere004@turing1 VCF]$ /cm/shared/apps/vcftools/0.1.12b/bin/vcftools --vcf SGmergedfastqs.vcf 

VCFtools - v0.1.12b
(C) Adam Auton and Anthony Marcketta 2009

Parameters as interpreted:
	--vcf SGmergedfastqs.vcf

After filtering, kept 16 out of 16 Individuals
After filtering, kept 130505 out of a possible 130505 Sites
Run Time = 1.00 seconds

5. cp /cm/shared/courses/dbarshis/21AdvGenomics/classdata/Astrangia_poculata/VCF/GoodCoralGenelistForVCFSubsetter.txt ./
[spere004@turing1 VCF]$ ls
GoodCoralGenelistForVCFSubsetter.txt  mergedfastq_HEAAstrangiaAssembly.vcf  out.log  SGmergedfastqs.vcf


grep -c "##contig" SGmergedfastqs.vcf 
15079

6. /cm/shared/courses/dbarshis/21AdvGenomics/scripts/21Sp_vcfsubsetter_advbioinf.py GoodCoralGenelistForVCFSubsetter.txt mergedfastq_HEAAstrangiaAssembly.vcf 

7. [spere004@coreV3-23-031 VCF]$ vcftools --vcf mergedfastq_HEAAstrangiaAssembly_subset.vcf

VCFtools - 0.1.14
(C) Adam Auton and Anthony Marcketta 2009

Parameters as interpreted:
	--vcf mergedfastq_HEAAstrangiaAssembly_subset.vcf

After filtering, kept 40 out of 40 Individuals
After filtering, kept 432676 out of a possible 432676 Sites
Run Time = 6.00 seconds

 --vcf mergedfastq_HEAAstrangiaAssembly.vcf 

VCFtools - 0.1.14
(C) Adam Auton and Anthony Marcketta 2009

Parameters as interpreted:
	--vcf mergedfastq_HEAAstrangiaAssembly.vcf

After filtering, kept 40 out of 40 Individuals
After filtering, kept 1214003 out of a possible 1214003 Sites
Run Time = 5.00 seconds

[spere004@coreV3-23-031 VCF]$ vcftools --vcf SGmergedfastqs.vcf 

VCFtools - 0.1.14
(C) Adam Auton and Anthony Marcketta 2009

Parameters as interpreted:
	--vcf SGmergedfastqs.vcf

After filtering, kept 16 out of 16 Individuals
After filtering, kept 130505 out of a possible 130505 Sites
Run Time = 1.00 seconds


8. [spere004@coreV3-23-031 VCF]$ vcftools --vcf mergedfastq_HEAAstrangiaAssembly_subset.vcf --max-missing 0.5 --mac 3 --minQ 30 --recode --recode-INFO-all --out raw.g5mac3

VCFtools - 0.1.14
(C) Adam Auton and Anthony Marcketta 2009

Parameters as interpreted:
	--vcf mergedfastq_HEAAstrangiaAssembly_subset.vcf
	--recode-INFO-all
	--mac 3
	--minQ 30
	--max-missing 0.5
	--out raw.g5mac3
	--recode

After filtering, kept 40 out of 40 Individuals
Outputting VCF file...
After filtering, kept 99853 out of a possible 432676 Sites
Run Time = 31.00 seconds

vcftools --vcf raw.g5mac3.recode.vcf --minDP 3 --recode --recode-INFO-all --out raw5.g5mac3dp3 

VCFtools - 0.1.14
(C) Adam Auton and Anthony Marcketta 2009

Parameters as interpreted:
	--vcf raw.g5mac3.recode.vcf
	--recode-INFO-all
	--minDP 3
	--out raw5.g5mac3dp3
	--recode

After filtering, kept 40 out of 40 Individuals
Outputting VCF file...
After filtering, kept 99853 out of a possible 99853 Sites
Run Time = 25.00 seconds

vcftools --vcf raw5.g5mac3dp3.recode.vcf --missing-indv

VCFtools - 0.1.14
(C) Adam Auton and Anthony Marcketta 2009

Parameters as interpreted:
	--vcf raw5.g5mac3dp3.recode.vcf
	--missing-indv

After filtering, kept 40 out of 40 Individuals
Outputting Individual Missingness
After filtering, kept 99853 out of a possible 99853 Sites
Run Time = 2.00 seconds
[spere004@coreV3-23-031 VCF]$ cat out.imiss
INDV	N_DATA	N_GENOTYPES_FILTERED	N_MISS	F_MISS
RI_W_06_merged	99853	0	67075	0.671737
RI_W_07_merged	99853	0	63917	0.640111
VA_B_03_merged	99853	0	56586	0.566693
RI_W_02_merged	99853	0	73105	0.732126
RI_W_04_merged	99853	0	71159	0.712638
VA_W_09_SNP_clipped	99853	0	19459	0.194876
RI_B_08_SNP_clipped	99853	0	88110	0.882397
VA_W_08_SNP_clipped	99853	0	83344	0.834667
VA_B_08_SNP_clipped	99853	0	94221	0.943597
VA_W_02_merged	99853	0	71050	0.711546
VA_B_07_merged	99853	0	62687	0.627793
RI_B_05_merged	99853	0	43945	0.440097
VA_W_06_merged	99853	0	65164	0.652599
VA_W_04_merged	99853	0	50911	0.509859
VA_W_01_merged	99853	0	67150	0.672489
VA_B_10_SNP_clipped	99853	0	82831	0.829529
VA_B_06_merged	99853	0	57724	0.57809
VA_W_05_merged	99853	0	66297	0.663946
RI_B_09_SNP_clipped	99853	0	85107	0.852323
VA_W_10_SNP_clipped	99853	0	83234	0.833565
RI_W_08_SNP_clipped	99853	0	77802	0.779165
RI_B_06_merged	99853	0	79766	0.798834
RI_W_10_SNP_clipped	99853	0	91323	0.914574
RI_B_04_merged	99853	0	46717	0.467858
VA_W_03_merged	99853	0	64016	0.641102
RI_B_07_merged	99853	0	70798	0.709022
RI_W_05_merged	99853	0	57117	0.572011
RI_W_09_SNP_clipped	99853	0	88492	0.886223
VA_B_01_merged	99853	0	47217	0.472865
VA_B_09_SNP_clipped	99853	0	79187	0.793036
RI_B_10_SNP_clipped	99853	0	82779	0.829009
RI_W_01_merged	99853	0	73169	0.732767
RI_B_01_merged	99853	0	69619	0.697215
VA_B_04_merged	99853	0	58190	0.582757
RI_B_02_merged	99853	0	87439	0.875677
RI_W_03_merged	99853	0	38760	0.388171
VA_B_02_merged	99853	0	78381	0.784964
VA_W_07_merged	99853	0	64592	0.646871
VA_B_05_merged	99853	0	54401	0.544811
RI_B_03_merged	99853	0	80369	0.804873
[spere004@coreV3-23-031 VCF]$ bash
[spere004@coreV3-23-031 VCF]$ mawk '!/IN/' out.imiss | cut -f5 > totalmissing
[spere004@coreV3-23-031 VCF]$ gnuplot << \EOF 
> set terminal dumb size 120, 30
> set autoscale 
> unset label
> set title "Histogram of % missing data per individual"
> set ylabel "Number of Occurrences"
> set xlabel "% of missing data"
> #set yr [0:100000]
> binwidth=0.01
> bin(x,width)=width*floor(x/width) + binwidth/2.0
> plot 'totalmissing' using (bin($1,binwidth)):(1.0) smooth freq with boxes
> pause -1
> EOF

                                         Histogram of % missing data per individual
  Number of Occurrences
      3 ++----------+-----------+-----------+-----------+------------+---***-----+-----------+-----------+----------++
        +           +           +           +           +       'totalmissing' using (bin($1,binwidth)):(1.0) ****** +
        |                                                                * *                                         |
        |                                                                * *                                         |
        |                                                                * *                                         |
        |                                                                * *                                         |
    2.5 ++                                                               * *                                        ++
        |                                                                * *                                         |
        |                                                                * *                                         |
        |                                                                * *                                         |
        |                                                                * *                                         |
        |                                                                * *                                         |
      2 ++                                                       **      * * ***  ******    ** ****   ****          ++
        |                                                        **      * * * *  * *  *    ** ** *   *  *           |
        |                                                        **      * * * *  * *  *    ** ** *   *  *           |
        |                                                        **      * * * *  * *  *    ** ** *   *  *           |
        |                                                        **      * * * *  * *  *    ** ** *   *  *           |
        |                                                        **      * * * *  * *  *    ** ** *   *  *           |
    1.5 ++                                                       **      * * * *  * *  *    ** ** *   *  *          ++
        |                                                        **      * * * *  * *  *    ** ** *   *  *           |
        |                                                        **      * * * *  * *  *    ** ** *   *  *           |
        |                                                        **      * * * *  * *  *    ** ** *   *  *           |
        |                                                        **      * * * *  * *  *    ** ** *   *  *           |
        +           +           +           +           +        **  +   * * * * +* *  *    ** ** *   *  *           +
      1 *********************************************************************************************************---++
       0.1         0.2         0.3         0.4         0.5          0.6         0.7         0.8         0.9          1
                                                      % of missing data

mawk '$5 > 0.5' out.imiss | cut -f1 > lowDP.indv

--vcf raw5.g5mac3dp3.recode.vcf --remove lowDP.indv --recode --recode-INFO-all --out raw.g5mac3dplm

VCFtools - 0.1.14
(C) Adam Auton and Anthony Marcketta 2009

Parameters as interpreted:
	--vcf raw5.g5mac3dp3.recode.vcf
	--exclude lowDP.indv
	--recode-INFO-all
	--out raw.g5mac3dplm
	--recode

Excluding individuals in 'exclude' list
After filtering, kept 5 out of 40 Individuals
Outputting VCF file...
After filtering, kept 99853 out of a possible 99853 Sites
Run Time = 10.00 seconds