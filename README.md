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

#Homework09
/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/StephG/data/VCF
salloc
enable_lmod
module load dDocent
#second half run
/cm/shared/apps/vcftools/0.1.12b/bin/vcftools --vcf mergedfastq_HEAAstrangiaAssembly_subset.vcf --max-missing 0.5 --mac 3 --minQ 30 --minDP 10 --max-alleles 2 --maf 0.015 --remove-indels --recode --recode-INFO-all --out 1578_mergedfastq_HEAAstrangiaAssembly_subset_HEAFilters

VCFtools - v0.1.12b
(C) Adam Auton and Anthony Marcketta 2009

Parameters as interpreted:
	--vcf mergedfastq_HEAAstrangiaAssembly_subset.vcf
	--recode-INFO-all
	--mac 3
	--maf 0.015
	--max-alleles 2
	--minDP 10
	--minQ 30
	--max-missing 0.5
	--out 1578_mergedfastq_HEAAstrangiaAssembly_subset_HEAFilters
	--recode
	--remove-indels

After filtering, kept 40 out of 40 Individuals
Outputting VCF file...
After filtering, kept 1578 out of a possible 432676 Sites
Run Time = 6.00 seconds

2.  grep '#CHROM' mergedfastq_HEAAstrangiaAssembly_subset.vcf > sampleIDs.txt
sed 's/\s\+/\n/g' sampleIDs.txt > sampleIDs1.txt
scp spere004@turing.hpc.odu.edu:/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/StephG/data/VCF/sampleIDs1.txt .
#Added the second column via excel and uploaded the file to the cluster again
scp sampleIDs1.txt spere004@turing.hpc.odu.edu:/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/StephG/data/VCF/sampleIDs2.txt
cp sampleIDs2.txt genepop.txt

3. /cm/shared/courses/dbarshis/21AdvGenomics/scripts/vcftogenepop_advbioinf.py 1578_mergedfastq_HEAAstrangiaAssembly_subset_HEAFilters.recode.vcf genepop.txt
Indivs with genotypes in vcf file: RI_W_06_merged	RI_W_07_merged	VA_B_03_merged	RI_W_02_merged	RI_W_04_merged	VA_W_09_SNP_clipped	RI_B_08_SNP_clipped	VA_W_08_SNP_clipped	VA_B_08_SNP_clipped	VA_W_02_merged	VA_B_07_merged	RI_B_05_merged	VA_W_06_merged	VA_W_04_merged	VA_W_01_merged	VA_B_10_SNP_clipped	VA_B_06_merged	VA_W_05_merged	RI_B_09_SNP_clipped	VA_W_10_SNP_clipped	RI_W_08_SNP_clipped	RI_B_06_merged	RI_W_10_SNP_clipped	RI_B_04_merged	VA_W_03_merged	RI_B_07_merged	RI_W_05_merged	RI_W_09_SNP_clipped	VA_B_01_merged	VA_B_09_SNP_clipped	RI_B_10_SNP_clipped	RI_W_01_merged	RI_B_01_merged	VA_B_04_merged	RI_B_02_merged	RI_W_03_merged	VA_B_02_merged	VA_W_07_merged	VA_B_05_merged	RI_B_03_merged
44 1578 1578 1578 1578 40

4. scp spere004@turing.hpc.odu.edu:/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/StephG/data/VCF/1578_mergedfastq_HEAAstrangiaAssembly_subset_HEAFilters.recode_genepop.gen .

5. #Working on RStudio. Code below is r commands from day09 R script
> sum(is.na(datafile$tab))
[1] 35966

> datafile #shows info
/// GENIND OBJECT /////////

 // 40 individuals; 1,578 loci; 3,156 alleles; size: 1.4 Mb

 // Basic content
   @tab:  40 x 3156 matrix of allele counts
   @loc.n.all: number of alleles per locus (range: 2-2)
   @loc.fac: locus factor for the 3156 columns of @tab
   @all.names: list of allele names for each locus
   @ploidy: ploidy of each individual  (range: 2-2)
   @type:  codom
   @call: read.genepop(file = "1578_mergedfastq_HEAAstrangiaAssembly_subset_HEAFilters.recode_genepop.gen", 
    ncode = 2)

 // Optional content
   @pop: population of each individual (group size range: 40-40)
> YOURdata<-scaleGen(datafile, NA.method='mean')
Warning message:
In .local(x, ...) : Some scaling values are null.
 Corresponding alleles are removed.
> X<-YOURdata
> Y<-as.factor(substring(pop(datafile),1,4))
> pca1 <- dudi.pca(X,cent=F, scale=F, scannf=F, nf=3)
> s.label(pca1$li)
> s.class(pca1$li, pop(datafile))
> col <- c("blue","red", "green", "black")
> s.class(pca1$li, Y,xax=1,yax=2, col=transp(col,.6), axesell=F, cstar=0, cpoint=3, grid=FALSE, addaxes=TRUE)
> add.scatter.eig(pca1$eig[1:3], 3,1,2, posi="topright")
> title("PCA of DJB_data\naxes 1-2")
> a.clust<-snapclust(datafile, k = 2)
> class(a.clust)
[1] "snapclust" "list"     
> names(a.clust)
[1] "group"     "ll"        "proba"     "converged" "n.iter"    "n.param"  
> a.tab <- table(pop(datafile), a.clust$group)
> table.value(a.tab, col.labels = 1:2)
> compoplot(a.clust)

#plots were created and save on computer

#Homework10

1. #Following code is R scrip ran on 2 files in day10 folder. Figures are saved on local computer.

library("ape")
library("pegas")
library("seqinr")
library("ggplot2")
library("adegenet")
setwd("/Users/stephanieperez/Documents/Data_analysis_class/21sp_advgenomics")
datafile<-read.genepop("coral_66_cloneremoved_highoutliers.filtered1SNPper_genepop.gen", ncode=2)
datafile2<-read.genepop("coral_279_cloneremoved_neutral.filtered1SNPper_genepop.gen", ncode=2)

sum(is.na(datafile$tab))
datafile #shows info

sum(is.na(datafile2$tab))
datafile2

YOURdata<-scaleGen(datafile, NA.method='mean')
X<-YOURdata
Y<-as.factor(substring(pop(datafile),1,4))
pca1 <- dudi.pca(X,cent=F, scale=F, scannf=F, nf=3)

YOUR2data<-scaleGen(datafile2, NA.method='mean')
X2<-YOUR2data
Y2<-as.factor(substring(pop(datafile2),1,4))
pca12 <- dudi.pca(X2,cent=F, scale=F, scannf=F, nf=3)
#### PCAs ####
# individual labels
s.label(pca1$li)
s.label(pca12$li)
# population elipses
s.class(pca1$li, pop(datafile))
s.class(pca12$li, pop(datafile2))

#color symbols, pop names
#pdf("YOURINITIALS_ColorPCA1v2.pdf")
col <- c("blue","red", "green", "black")
s.class(pca1$li, Y,xax=1,yax=2, col=transp(col,.6), axesell=F, cstar=0, cpoint=3, grid=FALSE, addaxes=TRUE)
add.scatter.eig(pca1$eig[1:3], 3,1,2, posi="topright")
title("PCA of DJB_data\naxes 1-2")
dev.off()

col <- c("blue","red", "green", "black")
s.class(pca12$li, Y2,xax=1,yax=2, col=transp(col,.6), axesell=F, cstar=0, cpoint=3, grid=FALSE, addaxes=TRUE)
add.scatter.eig(pca12$eig[1:3], 3,1,2, posi="topright")
title("PCA of DJB_data\naxes 1-2")
dev.off()
#### Snapclust ####
a.clust<-snapclust(datafile, k = 2)
class(a.clust)
names(a.clust)
a.tab <- table(pop(datafile), a.clust$group)
table.value(a.tab, col.labels = 1:2)
compoplot(a.clust)

a.clust1<-snapclust(datafile2, k = 2)
class(a.clust1)
names(a.clust1)
a.tab <- table(pop(datafile2), a.clust$group)
table.value(a.tab, col.labels = 1:2)
compoplot(a.clust1)

2. cd /cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/StephG/data/SAMs
nano countexpression.sh
#!/bin/bash -l

#SBATCH -o countexpression.txt
#SBATCH -n 1         
#SBATCH --mail-user=spere004@odu.edu
#SBATCH --mail-type=END
#SBATCH --job-name=countexpression

/cm/shared/courses/dbarshis/21AdvGenomics/scripts/countxpression_SB_advbioinf.py *.sam

sbatch countexpression.sh

3. salloc
salloc: Pending job allocation 9280866
salloc: job 9280866 queued and waiting for resources
salloc: job 9280866 has been allocated resources
salloc: Granted job allocation 9280866

mv match_counts.txt countsoutput.txt

/cm/shared/courses/dbarshis/21AdvGenomics/scripts/ParseExpression2BigTable_advbioinf.py /cm/shared/courses/dbarshis/21AdvGenomics/classdata/Astrangia_poculata/host_genelist.txt StephFullCounts_summed.txt NoMatch *_counts.txt
Hits not matchedmatch_counts.txt=13381	RI_B_05_18_clippedtrimmed.fastq_counts.txt=1698	RI_B_05_22_clippedtrimmed.fastq_counts.txt=1698	RI_B_06_14_clippedtrimmed.fastq_counts.txt=1698	RI_B_06_22_clippedtrimmed.fastq_counts.txt=1698	RI_W_05_18_clippedtrimmed.fastq_counts.txt=1698	RI_W_05_22_clippedtrimmed.fastq_counts.txt=1698	RI_W_06_14_clippedtrimmed.fastq_counts.txt=1698	RI_W_06_22_clippedtrimmed.fastq_counts.txt=1698	VA_B_05_18_clippedtrimmed.fastq_counts.txt=1698	VA_B_05_22_clippedtrimmed.fastq_counts.txt=1698	VA_B_06_14_clippedtrimmed.fastq_counts.txt=1698	VA_B_06_22_clippedtrimmed.fastq_counts.txt=1698	VA_W_05_18_clippedtrimmed.fastq_counts.txt=1698	VA_W_05_22_clippedtrimmed.fastq_counts.txt=1698	VA_W_06_14_clippedtrimmed.fastq_counts.txt=1698	VA_W_06_22_clippedtrimmed.fastq_counts.txt=1698

4. scp spere004@turing.hpc.odu.edu:/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/StephG/data/SAMs/StephFullCounts_summed.txt .
spere004@turing.hpc.odu.edu's password: 
StephFullCounts_summed.txt                                                                100%  860KB   5.2MB/s   00:00

5. sed 's/_clippedtrimmed.fastq_counts.txt_UniqueTotReads//g' StephFullCounts_summed.txt > NewStephfullcount_summed.txt


##HOMEWORKDAY11

> setwd("/Users/stephanieperez/Documents/Data_analysis_class/21sp_advgenomics")
> getwd()
[1] "/Users/stephanieperez/Documents/Data_analysis_class/21sp_advgenomics"
> countsTable <- read.delim('djbFullCounts_summed.txt', header=TRUE, stringsAsFactors=TRUE, row.names=1)
> head(countsTable)
                       RI_B_01_14 RI_B_01_18 RI_B_01_22 RI_B_02_14 RI_B_02_18 RI_B_02_22
TR10054|c0_g1_i1_coral          0          0          0          0          0          0
TR10054|c0_g2_i1_coral          0          1          6          0          0          0
TR10083|c0_g2_i1_coral          0          1          2          0          1          2
TR10090|c0_g1_i1_coral          0          3          1          0          4          0
TR10090|c0_g2_i1_coral          0          4          2          1          0          0
TR10103|c0_g1_i1_coral          0          1          4          0          0          4
                       RI_B_03_14 RI_B_03_18 RI_B_03_22 RI_B_04_14 RI_B_04_18 RI_B_04_22
> dim(countsTable)
[1] 13381    84
> colSums(countsTable)
RI_B_01_14 RI_B_01_18 RI_B_01_22 RI_B_02_14 RI_B_02_18 RI_B_02_22 RI_B_03_14 RI_B_03_18 
     97406     207372     173843      47481      58036      84501     170330       5972 
RI_B_03_22 RI_B_04_14 RI_B_04_18 RI_B_04_22 RI_B_05_14 RI_B_05_18 RI_B_05_22 RI_B_06_14 
    199204     357124     544267      71600     630609     227313     225639      37012 
> colSums(countsTable)[order(colSums(countsTable))]
VA_W_02_22 VA_W_01_22 RI_B_03_18 RI_W_04_22 RI_B_07_22 RI_B_06_14 RI_W_04_14 RI_W_01_14 
       134        313       5972      10848      25369      37012      37579      39419 
RI_B_02_14 RI_W_02_14 RI_B_02_18 RI_B_04_22 RI_B_06_22 VA_B_02_14 RI_B_02_22 VA_B_02_22 
     47481      54184      58036      71600      72254      79276      84501      85224 

> LowCounts<-c("VA_W_02_22","VA_W_01_22","RI_B_03_18")
> names(countsTable)%in%LowCounts
 [1] FALSE FALSE FALSE FALSE FALSE FALSE FALSE  TRUE FALSE FALSE FALSE FALSE FALSE FALSE
[15] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
[29] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
[43] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
[57] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE  TRUE FALSE FALSE  TRUE FALSE
[71] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE

> !(names(countsTable)%in%LowCounts)
 [1]  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE FALSE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
[15]  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
[29]  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
[43]  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
[57]  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE FALSE  TRUE  TRUE FALSE  TRUE
[71]  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
> countsTable<-countsTable[,!(names(countsTable)%in%LowCounts)]
> dim(countsTable)
[1] 13381    81

conds<-data.frame("Sample"=names(countsTable))
> conds$Origin<-factor(substring(conds$Sample,1,2))
> conds$SymState<-factor(substring(conds$Sample,4,4))
> conds$Temp<-factor(substring(conds$Sample,9,10))
> conds$Origin_SymState<-factor(paste(conds$Origin,conds$SymState, sep="_"))
> conds$Origin_SymState_Temp<-factor(paste(conds$Origin,conds$SymState,conds$Temp, sep="_"))
> 
> conds
       Sample Origin SymState Temp Origin_SymState Origin_SymState_Temp
1  RI_B_01_14     RI        B   14            RI_B              RI_B_14
2  RI_B_01_18     RI        B   18            RI_B              RI_B_18
3  RI_B_01_22     RI        B   22            RI_B              RI_B_22
4  RI_B_02_14     RI        B   14            RI_B              RI_B_14

> prop.null <- apply(countsTable, 2, function(x) 100*mean(x==0))
> barplot(prop.null, main="Percentage of null counts per sample", 
+         horiz=TRUE, cex.names=0.5, las=1, 
+         col=conds$Origin_SymState_Temp, ylab='Samples', xlab='% of null counts')
> pdf(file="OverallNullCounts.pdf",14, 14)
> barplot(prop.null, main="Percentage of null counts per sample", 
+         horiz=TRUE, cex.names=0.5, las=1, 
+         col=conds$Origin_SymState_Temp, ylab='Samples', xlab='% of null counts')
> dev.off()
RStudioGD 
        2 

> means = apply(countsTable, 1, mean)
> table(means>=3)

FALSE  TRUE 
 5838  7543 
> countsTable<-countsTable[means>=3,]
> dim(countsTable)
[1] 7543   81
> prop.nullv2 <- apply(countsTable, 2, function(x) 100*mean(x==0))
> pdf(file="Mean3NullCounts.pdf",14, 14)
> barplot(prop.nullv2, main="Percentage of null counts per sample", 
+         horiz=TRUE, cex.names=0.5, las=1, 
+         col=conds$Origin_SymState_Temp, ylab='Samples', xlab='% of null counts')
> dev.off()
RStudioGD 
        2 

> dds <- DESeqDataSetFromMatrix(countData=countsTable, colData=conds, design=~ Origin_SymState_Temp)
> dds <- DESeq(dds)
estimating size factors
estimating dispersions
gene-wise dispersion estimates
mean-dispersion relationship
final dispersion estimates
fitting model and testing
-- replacing outliers and refitting for 8 genes
-- DESeq argument 'minReplicatesForReplace' = 7 
-- original counts are preserved in counts(dds)
estimating dispersions
fitting model and testing
> vstCounts<-varianceStabilizingTransformation(dds)
> dists<-dist(t(assay(vstCounts)))
> plot(hclust(dists))
plotPCA(vstCounts, intgroup="Origin")
> plotPCA(vstCounts, intgroup="SymState")
> plotPCA(vstCounts, intgroup="Temp")
> plotPCA(vstCounts, intgroup="Origin_SymState")
> plotPCA(vstCounts, intgroup="Origin_SymState_Temp")
> resultsNames(dds)
 [1] "Intercept"                               "Origin_SymState_Temp_RI_B_18_vs_RI_B_14"
 [3] "Origin_SymState_Temp_RI_B_22_vs_RI_B_14" "Origin_SymState_Temp_RI_W_14_vs_RI_B_14"
 [5] "Origin_SymState_Temp_RI_W_18_vs_RI_B_14" "Origin_SymState_Temp_RI_W_22_vs_RI_B_14"
 [7] "Origin_SymState_Temp_VA_B_14_vs_RI_B_14" "Origin_SymState_Temp_VA_B_18_vs_RI_B_14"
 [9] "Origin_SymState_Temp_VA_B_22_vs_RI_B_14" "Origin_SymState_Temp_VA_W_14_vs_RI_B_14"
[11] "Origin_SymState_Temp_VA_W_18_vs_RI_B_14" "Origin_SymState_Temp_VA_W_22_vs_RI_B_14"
> dim(dds)
[1] 7543   81
> res <- results(dds, contrast=c("Origin_SymState_Temp", "RI_B_18", "VA_B_18"))
> head(res)
log2 fold change (MLE): Origin_SymState_Temp RI_B_18 vs VA_B_18 
Wald test p-value: Origin_SymState_Temp RI_B_18 vs VA_B_18 
DataFrame with 6 rows and 6 columns
                               baseMean     log2FoldChange             lfcSE
                              <numeric>          <numeric>         <numeric>
TR10083|c0_g2_i1_coral 5.92149226796624 -0.124351582570554 0.881723031266384
TR10090|c0_g1_i1_coral   2.414668728522  0.403769276033225 0.959279168358701
TR10090|c0_g2_i1_coral 3.75861468695046  -0.83542301411573  0.86523878852701
TR10103|c0_g1_i1_coral 2.98376089398939 -0.801464007457239 0.848307534238223
TR10108|c0_g1_i1_coral 5.73440284734055 -0.526701449017958 0.837420233249731
TR10132|c0_g1_i1_coral 8.52629945810969   1.07157187389725  1.16012842796493
                                     stat            pvalue              padj
                                <numeric>         <numeric>         <numeric>
TR10083|c0_g2_i1_coral -0.141032476368405 0.887844286314782 0.996374898818957
TR10090|c0_g1_i1_coral  0.420909042280218 0.673821502118031 0.990719409569674
TR10090|c0_g2_i1_coral -0.965540409414564 0.334274206188308 0.964875734525325
TR10103|c0_g1_i1_coral -0.944780017988347 0.344771195342852 0.967913215005047
TR10108|c0_g1_i1_coral -0.628957156879308 0.529377105037453 0.987728806338776
TR10132|c0_g1_i1_coral  0.923666594203699 0.355659929898546 0.967913215005047
> summary(res)

out of 7542 with nonzero total read count
adjusted p-value < 0.1
LFC > 0 (up)       : 3, 0.04%
LFC < 0 (down)     : 5, 0.066%
outliers [1]       : 4, 0.053%
low counts [2]     : 1, 0.013%
(mean count < 1)
[1] see 'cooksCutoff' argument of ?results
[2] see 'independentFiltering' argument of ?results

> res <- results(dds, contrast=c("Origin_SymState_Temp", "RI_W_18", "VA_W_18"))
> summary(res)

out of 7542 with nonzero total read count
adjusted p-value < 0.1
LFC > 0 (up)       : 22, 0.29%
LFC < 0 (down)     : 38, 0.5%
outliers [1]       : 4, 0.053%
low counts [2]     : 3801, 50%
(mean count < 6)
[1] see 'cooksCutoff' argument of ?results
[2] see 'independentFiltering' argument of ?results

> res <- results(dds, contrast=c("Origin_SymState_Temp", "RI_B_14", "VA_B_14"))
> summary(res)

out of 7542 with nonzero total read count
adjusted p-value < 0.1
LFC > 0 (up)       : 8, 0.11%
LFC < 0 (down)     : 4, 0.053%
outliers [1]       : 4, 0.053%
low counts [2]     : 1, 0.013%
(mean count < 1)
[1] see 'cooksCutoff' argument of ?results
[2] see 'independentFiltering' argument of ?results
> res <- results(dds, contrast=c("Origin_SymState_Temp", "RI_W_14", "VA_W_14"))
> summary(res)

out of 7542 with nonzero total read count
adjusted p-value < 0.1
LFC > 0 (up)       : 10, 0.13%
LFC < 0 (down)     : 3, 0.04%
outliers [1]       : 4, 0.053%
low counts [2]     : 5263, 70%
(mean count < 8)
[1] see 'cooksCutoff' argument of ?results
[2] see 'independentFiltering' argument of ?results
> res <- results(dds, contrast=c("Origin_SymState_Temp", "RI_B_22", "VA_B_22"))
> summary(res)

out of 7542 with nonzero total read count
adjusted p-value < 0.1
LFC > 0 (up)       : 8, 0.11%
LFC < 0 (down)     : 2, 0.027%
outliers [1]       : 4, 0.053%
low counts [2]     : 1, 0.013%
(mean count < 1)
[1] see 'cooksCutoff' argument of ?results
[2] see 'independentFiltering' argument of ?results

> res <- results(dds, contrast=c("Origin_SymState_Temp", "RI_W_22", "VA_W_22"))
> summary(res)

out of 7542 with nonzero total read count
adjusted p-value < 0.1
LFC > 0 (up)       : 11, 0.15%
LFC < 0 (down)     : 5, 0.066%
outliers [1]       : 4, 0.053%
low counts [2]     : 146, 1.9%
(mean count < 2)
[1] see 'cooksCutoff' argument of ?results
[2] see 'independentFiltering' argument of ?results
> head(res[order(res$padj),])
log2 fold change (MLE): Origin_SymState_Temp RI_W_22 vs VA_W_22 
Wald test p-value: Origin_SymState_Temp RI_W_22 vs VA_W_22 
DataFrame with 6 rows and 6 columns
                               baseMean    log2FoldChange             lfcSE
                              <numeric>         <numeric>         <numeric>
TR42879|c0_g2_i1_coral  15.410578527665  17.0575331642567  3.13747844493701
TR13286|c1_g1_i1_coral 32.6102567902141 -3.38044295663573 0.648393226272248
TR47617|c0_g1_i1_coral  3.7465555529336  19.7261549909787  3.83515887756262
TR8327|c0_g3_i1_coral  8.73276616692518  19.7338447748926  4.06385316874438
TR29560|c0_g1_i1_coral 12.7955647888331  2.74246489048391 0.651667601875444
TR58072|c1_g1_i1_coral 53.8558310969574   1.3803927876847 0.330572470141824
                                    stat               pvalue                 padj
                               <numeric>            <numeric>            <numeric>
TR42879|c0_g2_i1_coral  5.43670130763213 5.42760110313753e-08 0.000401262549554957
TR13286|c1_g1_i1_coral -5.21356920409335 1.85241378350407e-07 0.000664534402813938
TR47617|c0_g1_i1_coral  5.14350399050882 2.69660923636117e-07 0.000664534402813938
TR8327|c0_g3_i1_coral   4.85594433545684  1.1981435873852e-06  0.00221446888538469
TR29560|c0_g1_i1_coral  4.20837998174426 2.57208081930306e-05   0.0365937404208763
TR58072|c1_g1_i1_coral  4.17576450662234 2.96986937001566e-05   0.0365937404208763
> plotCounts(dds, "TR2367|c0_g1_i1_coral", intgroup="Origin_SymState_Temp")
> plotCounts(dds, "TR2367|c0_g1_i1_coral", intgroup="Origin_SymState_Temp")
> sum(res$padj < 0.3, na.rm =T)
[1] 30
> sum(res$padj < 0.2, na.rm =T)
[1] 20
> sum(res$padj < 0.1, na.rm =T)
[1] 16
> sum(res$pvalue < 0.05, na.rm =T)
[1] 343
> scaledcounts = counts(dds, normalized=T)
> head(scaledcounts)
                       RI_B_01_14 RI_B_01_18 RI_B_01_22 RI_B_02_14 RI_B_02_18 RI_B_02_22
TR10083|c0_g2_i1_coral          0    0.84279   2.292953   0.000000   3.273656   4.312157
TR10090|c0_g1_i1_coral          0    2.52837   1.146477   0.000000  13.094624   0.000000
TR10090|c0_g2_i1_coral          0    3.37116   2.292953   3.553607   0.000000   0.000000
TR10103|c0_g1_i1_coral          0    0.84279   4.585907   0.000000   0.000000   8.624315...
> genes4heatmap<-res[res$pvalue <0.05 & !is.na(res$pvalue),]
> names(genes4heatmap)
[1] "baseMean"       "log2FoldChange" "lfcSE"          "stat"           "pvalue"        
[6] "padj"          
> head(genes4heatmap)
log2 fold change (MLE): Origin_SymState_Temp RI_W_22 vs VA_W_22 
Wald test p-value: Origin_SymState_Temp RI_W_22 vs VA_W_22 
DataFrame with 6 rows and 6 columns
                               baseMean    log2FoldChange             lfcSE
                              <numeric>         <numeric>         <numeric>
TR10090|c0_g1_i1_coral   2.414668728522  -2.1602364606262  1.06658202772732
TR10450|c0_g1_i1_coral 3.06295343830589 -3.43890734797067  1.35815909767837
TR10768|c0_g1_i1_coral 4.11391026506041  1.64720448435771   0.8163169025316
TR10773|c0_g1_i1_coral 2.74299826965667  3.89664910540304  1.28628276466641
TR11771|c0_g1_i1_coral 2.86558169571988  2.26910497576441 0.996533942762988
TR11938|c0_g1_i2_coral 3.17991201457045  1.92891473796097  0.93224992931647
                                    stat              pvalue              padj
                               <numeric>           <numeric>         <numeric>
TR10090|c0_g1_i1_coral -2.02538239391605   0.042828113882863 0.996984539439689
TR10450|c0_g1_i1_coral -2.53203571941545   0.011340243841624 0.882509712853964
TR10768|c0_g1_i1_coral  2.01784929265745  0.0436069594078913 0.996984539439689
TR10773|c0_g1_i1_coral  3.02938763733929 0.00245050039091153 0.437812432964705
TR11771|c0_g1_i1_coral  2.27699717831296  0.0227863941200996 0.989064009775494
TR11938|c0_g1_i2_coral  2.06909614825636  0.0385370651149041 0.996984539439689
> dim(genes4heatmap)
[1] 343   6
> data4heatmap<-scaledcounts[row.names(scaledcounts)%in%row.names(genes4heatmap),]
> dim(data4heatmap)
[1] 343  81
> head(data4heatmap)
                       RI_B_01_14 RI_B_01_18 RI_B_01_22 RI_B_02_14 RI_B_02_18 RI_B_02_22
TR10090|c0_g1_i1_coral    0.00000    2.52837   1.146477   0.000000   13.09462   0.000000
TR10450|c0_g1_i1_coral    0.00000    2.52837   0.000000   0.000000    0.00000   6.468236
TR10768|c0_g1_i1_coral   10.84813    4.21395   4.585907   7.107215    0.00000   8.624315
TR10773|c0_g1_i1_coral    0.00000    5.89953   2.292953   3.553607    0.00000   0.000000
TR11771|c0_g1_i1_coral    0.00000    2.52837   3.439430   0.000000    0.00000   0.000000
TR11938|c0_g1_i2_coral    0.00000    2.52837   0.000000   0.000000    0.00000   4.312157...
> temp = as.matrix(rowMeans(data4heatmap))
> head(temp)
                           [,1]
TR10090|c0_g1_i1_coral 2.414669
TR10450|c0_g1_i1_coral 3.062953
TR10768|c0_g1_i1_coral 4.113910
TR10773|c0_g1_i1_coral 2.742998
TR11771|c0_g1_i1_coral 2.865582
TR11938|c0_g1_i2_coral 3.179912
> scaledmatrix<-matrix(data=temp, nrow=nrow(data4heatmap), ncol=ncol(data4heatmap), byrow=FALSE)
> data4heatmapscaled = data4heatmap/scaledmatrix
> head(data4heatmapscaled)
                       RI_B_01_14 RI_B_01_18 RI_B_01_22 RI_B_02_14 RI_B_02_18 RI_B_02_22
TR10090|c0_g1_i1_coral   0.000000  1.0470877  0.4747967   0.000000   5.422948   0.000000
TR10450|c0_g1_i1_coral   0.000000  0.8254680  0.0000000   0.000000   0.000000   2.111764
TR10768|c0_g1_i1_coral   2.636938  1.0243174  1.1147318   1.727606   0.000000   2.096379
TR10773|c0_g1_i1_coral   0.000000  2.1507597  0.8359295   1.295519   0.000000   0.000000
TR11771|c0_g1_i1_coral   0.000000  0.8823235  1.2002554   0.000000   0.000000   0.000000
TR11938|c0_g1_i2_coral   0.000000  0.7951069  0.0000000   0.000000   0.000000   1.356062...
> dim(data4heatmapscaled)
[1] 343  81

> pairs.breaks <- seq(0, 3.0, by=0.1)
> length(pairs.breaks)
[1] 31
> mycol <- colorpanel(n=30, low="black", high="yellow")
> pdf(file="SGdata_byrow.pdf",14,7)
> heatmap.2(data.matrix(data4heatmapscaled), Rowv=T, Colv=F, dendrogram = c("row"), scale="none", keysize=1, breaks=pairs.breaks, col=mycol, trace = "none", symkey = F, density.info = "density", colsep=c(24), sepcolor=c("white"), sepwidth=c(.1,.1), margins=c(10,10), labRow=F)
> dev.off()
RStudioGD 
        2 
> pdf(file="SGdata_bycolumn.pdf",14,7)
> heatmap.2(data.matrix(data4heatmapscaled), Rowv=T, Colv=T, dendrogram = c("col"), scale="none", keysize=1, breaks=pairs.breaks, col=mycol, trace = "none", symkey = F, density.info = "density", colsep=c(24), sepcolor=c("white"), sepwidth=c(.1,.1), margins=c(10,10), labRow=F)
> dev.off()
RStudioGD 
        2 
> plotPCA(vstCounts[rownames(vstCounts)%in%row.names(genes4heatmap),], intgroup="Origin")
> prop.nullv3 <- apply(countsTable[rownames(countsTable)%in%row.names(genes4heatmap),], 2, function(x) 100*mean(x==0))
> pdf(file="ResNullCounts.pdf",14, 14)
> barplot(prop.nullv3, main="Percentage of null counts per sample", 
+         horiz=TRUE, cex.names=0.5, las=1, 
+         col=conds$Origin_SymState_Temp, ylab='Samples', xlab='% of null counts')
> dev.off()
RStudioGD 
        2 

#Homeworkday12

_B_03_14 RI_B_05_18 VA_W_07_14 VA_B_06_14 VA_W_07_22 VA_B_07_18 VA_W_02_18 VA_B_03_18 
    226784     227313     228792     232578     233899     234465     241804     251696 
RI_B_07_14 VA_W_04_22 VA_B_01_14 VA_B_04_18 VA_B_04_22 VA_B_03_22 VA_W_03_14 VA_W_04_18 
    257730     261344     261824     264192     268290     271959     278000     280007 
RI_W_03_14 VA_B_05_18 VA_W_04_14 RI_W_01_18 VA_W_03_22 RI_B_06_18 RI_W_04_18 VA_W_01_18 
    281297     288121     292041     292612     295382     296071     300578     321900 
VA_B_05_14 VA_B_01_22 RI_W_07_14 RI_B_04_14 RI_W_03_22 VA_B_06_22 VA_W_05_18 RI_W_05_14 
    323715     328198     342795     357124     359053     362054     388532     392818 
RI_W_03_18 RI_B_04_18 VA_B_01_18 RI_B_05_14 
    428532     544267     548448     630609 
> 
> table(substring(names(countsTable),1,2))

RI VA 
42 42 
> table(substring(names(countsTable),4,4))

 B  W 
42 42 
> table(substring(names(countsTable),9,10))

14 18 22 
28 28 28 
> table(paste(substring(names(countsTable),1,2),substring(names(countsTable),4,4), sep="_"))

RI_B RI_W VA_B VA_W 
  21   21   21   21 
> table(paste(substring(names(countsTable),1,2),substring(names(countsTable),4,4), substring(names(countsTable),9,10), sep="_"))

RI_B_14 RI_B_18 RI_B_22 RI_W_14 RI_W_18 RI_W_22 VA_B_14 VA_B_18 VA_B_22 VA_W_14 VA_W_18 
      7       7       7       7       7       7       7       7       7       7       7 
VA_W_22 
      7 
> 
> LowCounts<-c("VA_W_02_22","VA_W_01_22","RI_B_03_18", "RI_W_01_14", "RI_W_04_22", "VA_W_03_18")
> names(countsTable)%in%LowCounts
 [1] FALSE FALSE FALSE FALSE FALSE FALSE FALSE  TRUE FALSE FALSE FALSE FALSE FALSE FALSE
[15] FALSE FALSE FALSE FALSE FALSE FALSE FALSE  TRUE FALSE FALSE FALSE FALSE FALSE FALSE
[29] FALSE FALSE FALSE FALSE  TRUE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
[43] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
[57] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE  TRUE FALSE FALSE  TRUE FALSE
[71]  TRUE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
> !(names(countsTable)%in%LowCounts)
 [1]  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE FALSE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
[15]  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE FALSE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
[29]  TRUE  TRUE  TRUE  TRUE FALSE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
[43]  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
[57]  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE FALSE  TRUE  TRUE FALSE  TRUE
[71] FALSE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
> countsTable<-countsTable[,!(names(countsTable)%in%LowCounts)]
> dim(countsTable)
[1] 13381    78
> 
> #make a table with conditions of each individual (e.g. "VA" and "RI")  There should be the same number of conditions described as there are samples in your data file, and in the same order.
> #NOTE: It is absolutely critical that the columns of the count matrix and the rows of the column data (information about samples) are in the same order. DESeq2 will not make guesses as to which column of the count matrix belongs to which row of the column data, these must be provided to DESeq2 already in consistent order.
> #Here's an example
> # Sample		Origin	SymState	Temp  Origin_SymState Origin_SymState_Temp
> # RI_B_06_18		RI	B	18  RI_B  RI_B_18
> # VA_B_07_14		VA	B	14  VA_B  VA_B_14
> # VA_W_07_22		VA	W	22  VA_W  VA_W_22
> # safest way to do this is in R
> 
> conds<-data.frame("Sample"=names(countsTable))
> conds$Origin<-factor(substring(conds$Sample,1,2))
> conds$SymState<-factor(substring(conds$Sample,4,4))
> conds$Temp<-factor(substring(conds$Sample,9,10))
> conds$Origin_SymState<-factor(paste(conds$Origin,conds$SymState, sep="_"))
> conds$Origin_SymState_Temp<-factor(paste(conds$Origin,conds$SymState,conds$Temp, sep="_"))
> 
> ##Check null counts per sample
> prop.null <- apply(countsTable, 2, function(x) 100*mean(x==0))
> 
> barplot(prop.null, main="Percentage of null counts per sample", 
+         horiz=TRUE, cex.names=0.5, las=1, 
+         col=conds$Origin_SymState_Temp, ylab='Samples', xlab='% of null counts')
> 
> pdf(file="OverallNullCountsv2.pdf",14, 14)
> barplot(prop.null, main="Percentage of null counts per sample", 
+         horiz=TRUE, cex.names=0.5, las=1, 
+         col=conds$Origin_SymState_Temp, ylab='Samples', xlab='% of null counts')
> dev.off()
RStudioGD 
        2 
> 
> # how many genes have mean count >=3 
> means = apply(countsTable, 1, mean)
> table(means>=3)

FALSE  TRUE 
 5721  7660 
> 
> countsTable<-countsTable[means>=3,]
> dim(countsTable)
[1] 7660   78
> 
> prop.nullv2 <- apply(countsTable, 2, function(x) 100*mean(x==0))
> 
> barplot(prop.nullv2, main="Percentage of null counts per sample", 
+         horiz=TRUE, cex.names=0.5, las=1, 
+         col=conds$Origin_SymState_Temp, ylab='Samples', xlab='% of null counts')
> 
> pdf(file="Mean3NullCountsv2.pdf",14, 14)
> barplot(prop.nullv2, main="Percentage of null counts per sample", 
+         horiz=TRUE, cex.names=0.5, las=1, 
+         col=conds$Origin_SymState_Temp, ylab='Samples', xlab='% of null counts')
> dev.off()
RStudioGD 
        2 
> 
> #make count data sets
> dds <- DESeqDataSetFromMatrix(countData=countsTable, colData=conds, design=~ Origin + SymState + Temp + Origin:SymState)
> 
> dds <- DESeq(dds)
estimating size factors
estimating dispersions
gene-wise dispersion estimates
mean-dispersion relationship
final dispersion estimates
fitting model and testing
-- replacing outliers and refitting for 14 genes
-- DESeq argument 'minReplicatesForReplace' = 7 
-- original counts are preserved in counts(dds)
estimating dispersions
fitting model and testing
> 
> dim(dds)
[1] 7660   78
> 
> #transform counts to variance stablized counts
> vstCounts<-varianceStabilizingTransformation(dds)
> 
> #plot cluster dendrogram across samples
> dists<-dist(t(assay(vstCounts)))
> plot(hclust(dists))
> heatmap.2(as.matrix(dists), key=F, trace="none",
+           col=colorpanel(100, "black", "white"),
+           margin=c(10, 10))
> 
> ###Figure out which contrast you want to examine (i.e. which two groups do you want to compare)
> resultsNames(dds)
[1] "Intercept"          "Origin_VA_vs_RI"    "SymState_W_vs_B"    "Temp_18_vs_14"     
[5] "Temp_22_vs_14"      "OriginVA.SymStateW"
> 
> res <- results(dds)
> head(res)
log2 fold change (MLE): OriginVA.SymStateW 
Wald test p-value: OriginVA.SymStateW 
DataFrame with 6 rows and 6 columns
                               baseMean     log2FoldChange             lfcSE
                              <numeric>          <numeric>         <numeric>
TR10083|c0_g2_i1_coral   5.366479327573  0.107690151743452  0.64464619766983
TR10090|c0_g1_i1_coral 2.70436251126018 -0.247209127175208 0.831370968745152
TR10090|c0_g2_i1_coral 3.65756460141883 -0.976996511249959 0.654110304614643
TR10103|c0_g1_i1_coral  2.9127886212765 -0.172219518994785 0.641025633753981
TR10108|c0_g1_i1_coral 6.31144026709945  0.366046450639525 0.664400660631174
TR10132|c0_g1_i1_coral  9.2673703948612 -0.589356834713084 0.975809166670876
                                     stat            pvalue              padj
                                <numeric>         <numeric>         <numeric>
TR10083|c0_g2_i1_coral   0.16705310933767 0.867328260788591 0.999364127033592
TR10090|c0_g1_i1_coral -0.297351166289025 0.766198422057453  0.99520853313718
TR10090|c0_g2_i1_coral  -1.49362654029054  0.13527325854353 0.958806816980756
TR10103|c0_g1_i1_coral -0.268662452679515 0.788189448150222  0.99520853313718
TR10108|c0_g1_i1_coral  0.550942333940163 0.581673205867577 0.991106673557066
TR10132|c0_g1_i1_coral -0.603967307177248 0.545865378089277 0.990476522025752
> summary(res)

out of 7659 with nonzero total read count
adjusted p-value < 0.1
LFC > 0 (up)       : 2, 0.026%
LFC < 0 (down)     : 9, 0.12%
outliers [1]       : 10, 0.13%
low counts [2]     : 1, 0.013%
(mean count < 1)
[1] see 'cooksCutoff' argument of ?results
[2] see 'independentFiltering' argument of ?results

> 
> resSymState <- results(dds, contrast=c("SymState", "B", "W"))
> head(resSymState)
log2 fold change (MLE): SymState B vs W 
Wald test p-value: SymState B vs W 
DataFrame with 6 rows and 6 columns
                               baseMean     log2FoldChange             lfcSE
                              <numeric>          <numeric>         <numeric>
TR10083|c0_g2_i1_coral   5.366479327573  0.304875236273871 0.463587635582715
TR10090|c0_g1_i1_coral 2.70436251126018 -0.340213618854429 0.624844624315529
TR10090|c0_g2_i1_coral 3.65756460141883   -1.0442719434015 0.488672538582417
TR10103|c0_g1_i1_coral  2.9127886212765 -0.316210568092073 0.469122505416545
TR10108|c0_g1_i1_coral 6.31144026709945   0.25797411425412 0.481341478797278
TR10132|c0_g1_i1_coral  9.2673703948612 -0.604956612553455 0.692218264872669
                                     stat             pvalue              padj
                                <numeric>          <numeric>         <numeric>
TR10083|c0_g2_i1_coral  0.657643157136089  0.510767456004599 0.986343106634585
TR10090|c0_g1_i1_coral -0.544477147782311  0.586113169806799 0.995961170585915
TR10090|c0_g2_i1_coral  -2.13695647074996 0.0326015322469065 0.816269739453607
TR10103|c0_g1_i1_coral -0.674046894875149  0.500281500123105 0.986343106634585
TR10108|c0_g1_i1_coral  0.535948231385995   0.59199432935739 0.995961170585915
TR10132|c0_g1_i1_coral -0.873939107435622  0.382151415850855 0.986343106634585
> summary(resSymState)

out of 7659 with nonzero total read count
adjusted p-value < 0.1
LFC > 0 (up)       : 6, 0.078%
LFC < 0 (down)     : 6, 0.078%
outliers [1]       : 10, 0.13%
low counts [2]     : 1, 0.013%
(mean count < 1)
[1] see 'cooksCutoff' argument of ?results
[2] see 'independentFiltering' argument of ?results

> 
> resOrigin <- results(dds, contrast=c("Origin", "VA", "RI"))
> head(resOrigin)
log2 fold change (MLE): Origin VA vs RI 
Wald test p-value: Origin VA vs RI 
DataFrame with 6 rows and 6 columns
                               baseMean      log2FoldChange             lfcSE
                              <numeric>           <numeric>         <numeric>
TR10083|c0_g2_i1_coral   5.366479327573  -0.271242746289843 0.446224512750353
TR10090|c0_g1_i1_coral 2.70436251126018    1.11251170496561 0.589306266446119
TR10090|c0_g2_i1_coral 3.65756460141883   0.943134641716211 0.474719393211504
TR10103|c0_g1_i1_coral  2.9127886212765  0.0386642676540012 0.456719612483097
TR10108|c0_g1_i1_coral 6.31144026709945 -0.0179009694277555 0.461957599914831
TR10132|c0_g1_i1_coral  9.2673703948612  -0.264990306479184 0.677607561801266
                                      stat             pvalue              padj
                                 <numeric>          <numeric>         <numeric>
TR10083|c0_g2_i1_coral  -0.607861600022842  0.543279269700006 0.865660813784253
TR10090|c0_g1_i1_coral    1.88783281005095 0.0590483989759312                NA
TR10090|c0_g2_i1_coral    1.98672027139201 0.0469534041233123 0.418043000342497
TR10103|c0_g1_i1_coral  0.0846564644854882  0.932534507970102 0.984590265229257
TR10108|c0_g1_i1_coral -0.0387502433795997  0.969089515041603 0.992149683420423
TR10132|c0_g1_i1_coral  -0.391067516682912  0.695747330435347 0.921516804624192
> summary(resOrigin)

out of 7659 with nonzero total read count
adjusted p-value < 0.1
LFC > 0 (up)       : 73, 0.95%
LFC < 0 (down)     : 104, 1.4%
outliers [1]       : 10, 0.13%
low counts [2]     : 594, 7.8%
(mean count < 3)
[1] see 'cooksCutoff' argument of ?results
[2] see 'independentFiltering' argument of ?results

> 
> res14v18 <- results(dds, contrast=c("Temp", "14", "18"))
> head(res14v18)
log2 fold change (MLE): Temp 14 vs 18 
Wald test p-value: Temp 14 vs 18 
DataFrame with 6 rows and 6 columns
                               baseMean     log2FoldChange             lfcSE
                              <numeric>          <numeric>         <numeric>
TR10083|c0_g2_i1_coral   5.366479327573 0.0134105654377919 0.389675116366814
TR10090|c0_g1_i1_coral 2.70436251126018 -0.750040304511369 0.493719609600886
TR10090|c0_g2_i1_coral 3.65756460141883 -0.527849679316855 0.385227211070661
TR10103|c0_g1_i1_coral  2.9127886212765  0.144899722334601 0.377623543666657
TR10108|c0_g1_i1_coral 6.31144026709945 -0.117131615020316 0.401865058532759
TR10132|c0_g1_i1_coral  9.2673703948612  -1.16667257299433 0.592603491023266
                                     stat             pvalue              padj
                                <numeric>          <numeric>         <numeric>
TR10083|c0_g2_i1_coral 0.0344147339014795  0.972546434477265 0.994762640063651
TR10090|c0_g1_i1_coral  -1.51916247587915   0.12872160398251                NA
TR10090|c0_g2_i1_coral  -1.37022947535249   0.17061528001709                NA
TR10103|c0_g1_i1_coral  0.383714746510905  0.701189881652785                NA
TR10108|c0_g1_i1_coral -0.291470015950062  0.770691872645245 0.956296438232868
TR10132|c0_g1_i1_coral  -1.96872375992892 0.0489848213296003 0.440134464115494
> summary(res14v18)

out of 7659 with nonzero total read count
adjusted p-value < 0.1
LFC > 0 (up)       : 31, 0.4%
LFC < 0 (down)     : 111, 1.4%
outliers [1]       : 10, 0.13%
low counts [2]     : 2671, 35%
(mean count < 4)
[1] see 'cooksCutoff' argument of ?results
[2] see 'independentFiltering' argument of ?results

> 
> res14v22 <- results(dds, contrast=c("Temp", "14", "22"))
> head(res14v22)
log2 fold change (MLE): Temp 14 vs 22 
Wald test p-value: Temp 14 vs 22 
DataFrame with 6 rows and 6 columns
                               baseMean     log2FoldChange             lfcSE
                              <numeric>          <numeric>         <numeric>
TR10083|c0_g2_i1_coral   5.366479327573 -0.381080048190283 0.396906053114453
TR10090|c0_g1_i1_coral 2.70436251126018 -0.420390942831918 0.517099767325245
TR10090|c0_g2_i1_coral 3.65756460141883 -0.149468056890158 0.407435526480227
TR10103|c0_g1_i1_coral  2.9127886212765  0.327505589102544 0.400037906787554
TR10108|c0_g1_i1_coral 6.31144026709945 -0.504680765262664 0.409220095704197
TR10132|c0_g1_i1_coral  9.2673703948612   -1.2400583742243 0.602190057747409
                                     stat             pvalue              padj
                                <numeric>          <numeric>         <numeric>
TR10083|c0_g2_i1_coral  -0.96012657201878  0.336991516539358  0.79600966973284
TR10090|c0_g1_i1_coral -0.812978402613553  0.416230440926914                NA
TR10090|c0_g2_i1_coral -0.366850819763779  0.713730297691035                NA
TR10103|c0_g1_i1_coral  0.818686388328871  0.412965364593821                NA
TR10108|c0_g1_i1_coral  -1.23327463768414  0.217473316972006 0.699820201183028
TR10132|c0_g1_i1_coral  -2.05924750545192 0.0394705344365933 0.387444149379081
> summary(res14v22)

out of 7659 with nonzero total read count
adjusted p-value < 0.1
LFC > 0 (up)       : 64, 0.84%
LFC < 0 (down)     : 97, 1.3%
outliers [1]       : 10, 0.13%
low counts [2]     : 2226, 29%
(mean count < 4)
[1] see 'cooksCutoff' argument of ?results
[2] see 'independentFiltering' argument of ?results

> 
> res18v22 <- results(dds, contrast=c("Temp", "18", "22"))
> head(res18v22)
log2 fold change (MLE): Temp 18 vs 22 
Wald test p-value: Temp 18 vs 22 
DataFrame with 6 rows and 6 columns
                               baseMean      log2FoldChange             lfcSE
                              <numeric>           <numeric>         <numeric>
TR10083|c0_g2_i1_coral   5.366479327573  -0.394490613628075 0.395010013602601
TR10090|c0_g1_i1_coral 2.70436251126018   0.329649361679451 0.503429809209276
TR10090|c0_g2_i1_coral 3.65756460141883   0.378381622426696 0.396934638805837
TR10103|c0_g1_i1_coral  2.9127886212765   0.182605866767943 0.399213811730964
TR10108|c0_g1_i1_coral 6.31144026709945  -0.387549150242348 0.406735578634103
TR10132|c0_g1_i1_coral  9.2673703948612 -0.0733858012299701 0.596241474936225
                                     stat            pvalue              padj
                                <numeric>         <numeric>         <numeric>
TR10083|c0_g2_i1_coral -0.998685096689603 0.317947262436469 0.838585264651832
TR10090|c0_g1_i1_coral  0.654806997220173 0.512592024969438                NA
TR10090|c0_g2_i1_coral  0.953259265971454 0.340458724704261 0.847758501629442
TR10103|c0_g1_i1_coral  0.457413700132709  0.64737371896663                NA
TR10108|c0_g1_i1_coral -0.952828251572713 0.340677097558174 0.847758501629442
TR10132|c0_g1_i1_coral -0.123080671699029 0.902043216645959 0.991572144643207
> summary(res18v22)

out of 7659 with nonzero total read count
adjusted p-value < 0.1
LFC > 0 (up)       : 34, 0.44%
LFC < 0 (down)     : 10, 0.13%
outliers [1]       : 10, 0.13%
low counts [2]     : 1337, 17%
(mean count < 3)
[1] see 'cooksCutoff' argument of ?results
[2] see 'independentFiltering' argument of ?results

> sum(resOrigin$padj < 0.1, na.rm =T)
[1] 177
> sum(resOrigin$pvalue < 0.05, na.rm =T)
[1] 866
> scaledcounts = counts(dds, normalize=T)
> head(scaledcounts)
                       RI_B_01_14 RI_B_01_18 RI_B_01_22 RI_B_02_14 RI_B_02_18 RI_B_02_22
TR10083|c0_g2_i1_coral          0  0.8671827   2.447866   0.000000   3.455170   4.432653
TR10090|c0_g1_i1_coral          0  2.6015481   1.223933   0.000000  13.820681   0.000000
TR10090|c0_g2_i1_coral          0  3.4687308   2.447866   3.772786   0.000000   0.000000
TR10103|c0_g1_i1_coral          0  0.8671827   4.895733   0.000000   0.000000   8.865306
TR10108|c0_g1_i1_coral          0  1.7343654   4.895733   0.000000   6.910341   0.000000
TR10132|c0_g1_i1_coral          0  6.0702789   1.223933  18.863931  51.827555   0.000000
                       RI_B_03_14 RI_B_03_22 RI_B_04_14 RI_B_04_18 RI_B_04_22 RI_B_05_14
TR10083|c0_g2_i1_coral  12.871970   1.272998  12.424473  8.1878079   0.000000   4.563408
TR10090|c0_g1_i1_coral   0.000000   0.000000   2.003947  4.0939039   6.765958   0.570426
TR10090|c0_g2_i1_coral   0.000000   3.818995   4.809473  3.6845136   0.000000   0.570426
TR10103|c0_g1_i1_coral   1.287197   3.818995   6.011842  3.2751232   0.000000   5.133834
TR10108|c0_g1_i1_coral  14.159167  15.275980   2.805526  4.9126847  16.914895   5.989473
TR10132|c0_g1_i1_coral   6.435985   2.545997   0.000000  0.8187808   3.382979   1.426065
                       RI_B_05_18 RI_B_05_22 RI_B_06_14 RI_B_06_18 RI_B_06_22 RI_B_07_14
TR10083|c0_g2_i1_coral          0  2.4538305   19.55961   3.448566   18.78455  1.4936671
TR10090|c0_g1_i1_coral          0  0.0000000    0.00000   2.069140    0.00000  0.7468335
TR10090|c0_g2_i1_coral          0  2.4538305    0.00000   4.827992    0.00000  3.7341677
TR10103|c0_g1_i1_coral          0  4.0897176    0.00000   3.448566    0.00000  2.2405006
TR10108|c0_g1_i1_coral          0  0.8179435    6.51987  10.345698   40.69986  3.7341677
TR10132|c0_g1_i1_coral          0  1.6358870    0.00000   1.379426    0.00000  8.9620025
                       RI_B_07_18 RI_B_07_22 RI_W_01_18 RI_W_01_22 RI_W_02_14 RI_W_02_18
TR10083|c0_g2_i1_coral   8.070182   36.85316  10.815190   4.646396   0.000000  4.9947759
TR10090|c0_g1_i1_coral   2.017545    0.00000  12.257216   1.548799   0.000000  1.9979104
TR10090|c0_g2_i1_coral   1.008773    0.00000  12.257216   7.743994   4.651361  4.9947759
TR10103|c0_g1_i1_coral   2.017545    0.00000   7.931140   0.000000   0.000000  0.9989552
TR10108|c0_g1_i1_coral   1.008773    0.00000   2.884051   1.548799   9.302721  6.9926863
TR10132|c0_g1_i1_coral  44.386000   27.63987   1.442025   0.000000   0.000000  5.9937311
                       RI_W_02_22 RI_W_03_14 RI_W_03_18 RI_W_03_22 RI_W_04_14 RI_W_04_18
TR10083|c0_g2_i1_coral   3.615216   8.525621   5.407467   4.745758   12.82564  2.9768406
TR10090|c0_g1_i1_coral   0.000000   4.262810   1.081493   1.581919    0.00000  3.4729807
TR10090|c0_g2_i1_coral   4.820288   3.044865   3.244480   1.581919    0.00000  7.4421015
TR10103|c0_g1_i1_coral   3.615216   3.044865   3.244480   1.054613    0.00000  0.9922802
TR10108|c0_g1_i1_coral   2.410144   2.435892   4.686471   2.109226   21.37607 12.8996426
TR10132|c0_g1_i1_coral  44.587667   1.217946   1.081493   1.054613   29.92650  7.9382416
                       RI_W_05_14 RI_W_05_18 RI_W_05_22 RI_W_06_14 RI_W_06_18 RI_W_06_22
TR10083|c0_g2_i1_coral  3.1630643   1.010704   5.526636   1.044347   1.336966   5.564881
TR10090|c0_g1_i1_coral  0.9037326   8.085630   0.000000   0.000000   0.000000   4.451904
TR10090|c0_g2_i1_coral  3.6149306  10.107037   1.381659   3.133041   1.336966   7.790833
TR10103|c0_g1_i1_coral  4.0667969   2.021407   2.763318  10.443469   1.336966   2.225952
TR10108|c0_g1_i1_coral  5.4223959   2.021407   6.908296  11.487816   0.000000   5.564881
TR10132|c0_g1_i1_coral  1.8074653  10.107037  27.633182   5.221735   1.336966  42.293092
                       RI_W_07_14 RI_W_07_18 RI_W_07_22 VA_B_01_14 VA_B_01_18 VA_B_01_22
TR10083|c0_g2_i1_coral   4.124636   5.593017   6.900578   2.551157   1.731769   2.845097
TR10090|c0_g1_i1_coral   0.000000   0.000000   0.000000   7.653472   9.091789   1.707058
TR10090|c0_g2_i1_coral   2.062318   1.118603   5.520462  10.204629   5.628251   5.690194
TR10103|c0_g1_i1_coral   5.499514  13.423242   1.380116   3.826736   2.597654   2.845097
TR10108|c0_g1_i1_coral   0.000000   1.118603   5.520462   3.826736   9.091789   2.845097
TR10132|c0_g1_i1_coral   1.374879   2.237207  86.947282   1.275579   1.298827   0.000000
                       VA_B_02_14 VA_B_02_18 VA_B_02_22 VA_B_03_14 VA_B_03_18 VA_B_03_22
TR10083|c0_g2_i1_coral          0    14.2516  19.312637  16.029307  14.339493   7.833217
TR10090|c0_g1_i1_coral          0     0.0000   0.000000   5.828839   2.150924   7.833217
TR10090|c0_g2_i1_coral          0     0.0000   0.000000  10.929073   4.301848   3.560553
TR10103|c0_g1_i1_coral          0     0.0000   2.145849   2.185815   4.301848   3.560553
TR10108|c0_g1_i1_coral          0     0.0000   0.000000  14.572098  18.641340  21.363318
TR10132|c0_g1_i1_coral          0     0.0000   8.583394   9.471863  30.829909   8.545327
                       VA_B_04_14 VA_B_04_18 VA_B_04_22 VA_B_05_14 VA_B_05_18 VA_B_05_22
TR10083|c0_g2_i1_coral   0.000000  0.9006809   6.731616   2.098865  3.3173156   1.813677
TR10090|c0_g1_i1_coral   0.000000  4.5034046   3.624716   4.897352  1.1057719   7.254707
TR10090|c0_g2_i1_coral   7.108517  3.1523832   0.000000   1.399244  0.5528859   5.441030
TR10103|c0_g1_i1_coral   4.442823  0.0000000   0.000000   0.000000  3.3173156   0.000000
TR10108|c0_g1_i1_coral   2.665694  4.9537450   3.624716   9.095083  5.5288593   0.000000
TR10132|c0_g1_i1_coral   0.000000  2.7020428   0.000000   0.000000  4.9759734   5.441030
                       VA_B_06_14 VA_B_06_18 VA_B_06_22 VA_B_07_14 VA_B_07_18 VA_B_07_22
TR10083|c0_g2_i1_coral   1.383946   0.000000  5.9098781   3.728534  0.7405861   2.098499
TR10090|c0_g1_i1_coral   8.303676   0.000000  0.4924898   0.000000  3.7029304   2.098499
TR10090|c0_g2_i1_coral   0.000000   4.206352  1.4774695   1.491414 15.5523076   6.295498
TR10103|c0_g1_i1_coral   5.535784   6.730163  3.9399187   1.491414  8.1464468   4.196999
TR10108|c0_g1_i1_coral  11.763540   4.206352  3.4474289   2.237121  2.2217582   5.246248
TR10132|c0_g1_i1_coral  18.683270   2.523811 14.2822054   8.948482 17.0334798   2.098499
                       VA_W_01_14 VA_W_01_18 VA_W_02_14 VA_W_02_18 VA_W_03_14 VA_W_03_22
TR10083|c0_g2_i1_coral   6.699293   7.732656   0.000000  4.5789684  3.1096023   6.888125
TR10090|c0_g1_i1_coral   3.828167   1.104665   6.978382  0.6541383  5.4418040   9.392897
TR10090|c0_g2_i1_coral   0.000000   3.866328   4.361489 13.0827667  6.9966052   3.130966
TR10103|c0_g1_i1_coral   0.000000   3.866328   5.233787  0.6541383  6.9966052   2.504773
TR10108|c0_g1_i1_coral   1.914084   4.418660   0.000000  9.1579367  3.1096023   3.757159
TR10132|c0_g1_i1_coral   0.000000  10.494319   2.616893 13.0827667  0.7774006  13.150056
                       VA_W_04_14 VA_W_04_18 VA_W_04_22 VA_W_05_14 VA_W_05_18 VA_W_05_22
TR10083|c0_g2_i1_coral   1.026752   4.334366   6.410680  0.0000000   3.848517  12.379823
TR10090|c0_g1_i1_coral   2.566880   5.779155   3.945034  0.0000000   1.099576  12.379823
TR10090|c0_g2_i1_coral   2.053504   7.705540  10.848842  0.0000000   2.748941   7.427894
TR10103|c0_g1_i1_coral   3.593631   3.852770   2.958775  0.8118702   3.298729   2.475965
TR10108|c0_g1_i1_coral   6.673887  20.227043   8.383196  1.6237403   5.497882  38.377452
TR10132|c0_g1_i1_coral   2.566880   0.000000   0.000000  2.4356105   8.796611   2.475965
                       VA_W_06_14 VA_W_06_18 VA_W_06_22 VA_W_07_14 VA_W_07_18 VA_W_07_22
TR10083|c0_g2_i1_coral   5.042735  2.5895188   0.000000 10.2466895   1.127608  0.9473408
TR10090|c0_g1_i1_coral   0.000000  0.8631729   1.764014  1.5764138   1.127608  6.6313859
TR10090|c0_g2_i1_coral   3.025641  0.8631729   0.000000  5.5174482   3.382824  2.8420225
TR10103|c0_g1_i1_coral   8.068376  2.5895188   4.410036  4.7292413   0.000000  1.8946817
TR10108|c0_g1_i1_coral   4.034188  6.9053834   5.292043  3.1528275   1.127608  1.8946817
TR10132|c0_g1_i1_coral   9.076923 29.3478796  26.460214  0.7882069   6.765648  8.5260676
> head(scaledcounts)
                       RI_B_01_14 RI_B_01_18 RI_B_01_22 RI_B_02_14 RI_B_02_18 RI_B_02_22
TR10083|c0_g2_i1_coral          0  0.8671827   2.447866   0.000000   3.455170   4.432653
TR10090|c0_g1_i1_coral          0  2.6015481   1.223933   0.000000  13.820681   0.000000
TR10090|c0_g2_i1_coral          0  3.4687308   2.447866   3.772786   0.000000   0.000000
TR10103|c0_g1_i1_coral          0  0.8671827   4.895733   0.000000   0.000000   8.865306
TR10108|c0_g1_i1_coral          0  1.7343654   4.895733   0.000000   6.910341   0.000000
TR10132|c0_g1_i1_coral          0  6.0702789   1.223933  18.863931  51.827555   0.000000
                       RI_B_03_14 RI_B_03_22 RI_B_04_14 RI_B_04_18 RI_B_04_22 RI_B_05_14
TR10083|c0_g2_i1_coral  12.871970   1.272998  12.424473  8.1878079   0.000000   4.563408
TR10090|c0_g1_i1_coral   0.000000   0.000000   2.003947  4.0939039   6.765958   0.570426
TR10090|c0_g2_i1_coral   0.000000   3.818995   4.809473  3.6845136   0.000000   0.570426
TR10103|c0_g1_i1_coral   1.287197   3.818995   6.011842  3.2751232   0.000000   5.133834
TR10108|c0_g1_i1_coral  14.159167  15.275980   2.805526  4.9126847  16.914895   5.989473
TR10132|c0_g1_i1_coral   6.435985   2.545997   0.000000  0.8187808   3.382979   1.426065
                       RI_B_05_18 RI_B_05_22 RI_B_06_14 RI_B_06_18 RI_B_06_22 RI_B_07_14
TR10083|c0_g2_i1_coral          0  2.4538305   19.55961   3.448566   18.78455  1.4936671
TR10090|c0_g1_i1_coral          0  0.0000000    0.00000   2.069140    0.00000  0.7468335
TR10090|c0_g2_i1_coral          0  2.4538305    0.00000   4.827992    0.00000  3.7341677
TR10103|c0_g1_i1_coral          0  4.0897176    0.00000   3.448566    0.00000  2.2405006
TR10108|c0_g1_i1_coral          0  0.8179435    6.51987  10.345698   40.69986  3.7341677
TR10132|c0_g1_i1_coral          0  1.6358870    0.00000   1.379426    0.00000  8.9620025
                       RI_B_07_18 RI_B_07_22 RI_W_01_18 RI_W_01_22 RI_W_02_14 RI_W_02_18
TR10083|c0_g2_i1_coral   8.070182   36.85316  10.815190   4.646396   0.000000  4.9947759
TR10090|c0_g1_i1_coral   2.017545    0.00000  12.257216   1.548799   0.000000  1.9979104
TR10090|c0_g2_i1_coral   1.008773    0.00000  12.257216   7.743994   4.651361  4.9947759
TR10103|c0_g1_i1_coral   2.017545    0.00000   7.931140   0.000000   0.000000  0.9989552
TR10108|c0_g1_i1_coral   1.008773    0.00000   2.884051   1.548799   9.302721  6.9926863
TR10132|c0_g1_i1_coral  44.386000   27.63987   1.442025   0.000000   0.000000  5.9937311
                       RI_W_02_22 RI_W_03_14 RI_W_03_18 RI_W_03_22 RI_W_04_14 RI_W_04_18
TR10083|c0_g2_i1_coral   3.615216   8.525621   5.407467   4.745758   12.82564  2.9768406
TR10090|c0_g1_i1_coral   0.000000   4.262810   1.081493   1.581919    0.00000  3.4729807
TR10090|c0_g2_i1_coral   4.820288   3.044865   3.244480   1.581919    0.00000  7.4421015
TR10103|c0_g1_i1_coral   3.615216   3.044865   3.244480   1.054613    0.00000  0.9922802
TR10108|c0_g1_i1_coral   2.410144   2.435892   4.686471   2.109226   21.37607 12.8996426
TR10132|c0_g1_i1_coral  44.587667   1.217946   1.081493   1.054613   29.92650  7.9382416
                       RI_W_05_14 RI_W_05_18 RI_W_05_22 RI_W_06_14 RI_W_06_18 RI_W_06_22
TR10083|c0_g2_i1_coral  3.1630643   1.010704   5.526636   1.044347   1.336966   5.564881
TR10090|c0_g1_i1_coral  0.9037326   8.085630   0.000000   0.000000   0.000000   4.451904
TR10090|c0_g2_i1_coral  3.6149306  10.107037   1.381659   3.133041   1.336966   7.790833
TR10103|c0_g1_i1_coral  4.0667969   2.021407   2.763318  10.443469   1.336966   2.225952
TR10108|c0_g1_i1_coral  5.4223959   2.021407   6.908296  11.487816   0.000000   5.564881
TR10132|c0_g1_i1_coral  1.8074653  10.107037  27.633182   5.221735   1.336966  42.293092
                       RI_W_07_14 RI_W_07_18 RI_W_07_22 VA_B_01_14 VA_B_01_18 VA_B_01_22
TR10083|c0_g2_i1_coral   4.124636   5.593017   6.900578   2.551157   1.731769   2.845097
TR10090|c0_g1_i1_coral   0.000000   0.000000   0.000000   7.653472   9.091789   1.707058
TR10090|c0_g2_i1_coral   2.062318   1.118603   5.520462  10.204629   5.628251   5.690194
TR10103|c0_g1_i1_coral   5.499514  13.423242   1.380116   3.826736   2.597654   2.845097
TR10108|c0_g1_i1_coral   0.000000   1.118603   5.520462   3.826736   9.091789   2.845097
TR10132|c0_g1_i1_coral   1.374879   2.237207  86.947282   1.275579   1.298827   0.000000
                       VA_B_02_14 VA_B_02_18 VA_B_02_22 VA_B_03_14 VA_B_03_18 VA_B_03_22
TR10083|c0_g2_i1_coral          0    14.2516  19.312637  16.029307  14.339493   7.833217
TR10090|c0_g1_i1_coral          0     0.0000   0.000000   5.828839   2.150924   7.833217
TR10090|c0_g2_i1_coral          0     0.0000   0.000000  10.929073   4.301848   3.560553
TR10103|c0_g1_i1_coral          0     0.0000   2.145849   2.185815   4.301848   3.560553
TR10108|c0_g1_i1_coral          0     0.0000   0.000000  14.572098  18.641340  21.363318
TR10132|c0_g1_i1_coral          0     0.0000   8.583394   9.471863  30.829909   8.545327
                       VA_B_04_14 VA_B_04_18 VA_B_04_22 VA_B_05_14 VA_B_05_18 VA_B_05_22
TR10083|c0_g2_i1_coral   0.000000  0.9006809   6.731616   2.098865  3.3173156   1.813677
TR10090|c0_g1_i1_coral   0.000000  4.5034046   3.624716   4.897352  1.1057719   7.254707
TR10090|c0_g2_i1_coral   7.108517  3.1523832   0.000000   1.399244  0.5528859   5.441030
TR10103|c0_g1_i1_coral   4.442823  0.0000000   0.000000   0.000000  3.3173156   0.000000
TR10108|c0_g1_i1_coral   2.665694  4.9537450   3.624716   9.095083  5.5288593   0.000000
TR10132|c0_g1_i1_coral   0.000000  2.7020428   0.000000   0.000000  4.9759734   5.441030
                       VA_B_06_14 VA_B_06_18 VA_B_06_22 VA_B_07_14 VA_B_07_18 VA_B_07_22
TR10083|c0_g2_i1_coral   1.383946   0.000000  5.9098781   3.728534  0.7405861   2.098499
TR10090|c0_g1_i1_coral   8.303676   0.000000  0.4924898   0.000000  3.7029304   2.098499
TR10090|c0_g2_i1_coral   0.000000   4.206352  1.4774695   1.491414 15.5523076   6.295498
TR10103|c0_g1_i1_coral   5.535784   6.730163  3.9399187   1.491414  8.1464468   4.196999
TR10108|c0_g1_i1_coral  11.763540   4.206352  3.4474289   2.237121  2.2217582   5.246248
TR10132|c0_g1_i1_coral  18.683270   2.523811 14.2822054   8.948482 17.0334798   2.098499
                       VA_W_01_14 VA_W_01_18 VA_W_02_14 VA_W_02_18 VA_W_03_14 VA_W_03_22
TR10083|c0_g2_i1_coral   6.699293   7.732656   0.000000  4.5789684  3.1096023   6.888125
TR10090|c0_g1_i1_coral   3.828167   1.104665   6.978382  0.6541383  5.4418040   9.392897
TR10090|c0_g2_i1_coral   0.000000   3.866328   4.361489 13.0827667  6.9966052   3.130966
TR10103|c0_g1_i1_coral   0.000000   3.866328   5.233787  0.6541383  6.9966052   2.504773
TR10108|c0_g1_i1_coral   1.914084   4.418660   0.000000  9.1579367  3.1096023   3.757159
TR10132|c0_g1_i1_coral   0.000000  10.494319   2.616893 13.0827667  0.7774006  13.150056
                       VA_W_04_14 VA_W_04_18 VA_W_04_22 VA_W_05_14 VA_W_05_18 VA_W_05_22
TR10083|c0_g2_i1_coral   1.026752   4.334366   6.410680  0.0000000   3.848517  12.379823
TR10090|c0_g1_i1_coral   2.566880   5.779155   3.945034  0.0000000   1.099576  12.379823
TR10090|c0_g2_i1_coral   2.053504   7.705540  10.848842  0.0000000   2.748941   7.427894
TR10103|c0_g1_i1_coral   3.593631   3.852770   2.958775  0.8118702   3.298729   2.475965
TR10108|c0_g1_i1_coral   6.673887  20.227043   8.383196  1.6237403   5.497882  38.377452
TR10132|c0_g1_i1_coral   2.566880   0.000000   0.000000  2.4356105   8.796611   2.475965
                       VA_W_06_14 VA_W_06_18 VA_W_06_22 VA_W_07_14 VA_W_07_18 VA_W_07_22
TR10083|c0_g2_i1_coral   5.042735  2.5895188   0.000000 10.2466895   1.127608  0.9473408
TR10090|c0_g1_i1_coral   0.000000  0.8631729   1.764014  1.5764138   1.127608  6.6313859
TR10090|c0_g2_i1_coral   3.025641  0.8631729   0.000000  5.5174482   3.382824  2.8420225
TR10103|c0_g1_i1_coral   8.068376  2.5895188   4.410036  4.7292413   0.000000  1.8946817
TR10108|c0_g1_i1_coral   4.034188  6.9053834   5.292043  3.1528275   1.127608  1.8946817
TR10132|c0_g1_i1_coral   9.076923 29.3478796  26.460214  0.7882069   6.765648  8.5260676
> genes4heatmap<-resOrigin[resOrigin$pvalue <0.05 & !is.na(resOrigin$pvalue),]
> names(genes4heatmap)
[1] "baseMean"       "log2FoldChange" "lfcSE"          "stat"           "pvalue"        
[6] "padj"          
> head(genes4heatmap)
log2 fold change (MLE): Origin VA vs RI 
Wald test p-value: Origin VA vs RI 
DataFrame with 6 rows and 6 columns
                               baseMean    log2FoldChange             lfcSE
                              <numeric>         <numeric>         <numeric>
TR10090|c0_g2_i1_coral 3.65756460141883 0.943134641716211 0.474719393211504
TR10487|c0_g1_i1_coral 6.57169761658039 0.727122969400975 0.363907404480523
TR1069|c0_g1_i1_coral  4.14205241197446  4.49029083181354  1.98238112955566
TR10748|c0_g1_i1_coral 2.93642320037697  1.78798410821023 0.559059118556594
TR10773|c0_g1_i1_coral 3.02515761016279  1.75847746453697 0.659498298908414
TR10773|c1_g1_i1_coral 2.32875934475272  1.29222344670373 0.632167692638483
                                   stat              pvalue               padj
                              <numeric>           <numeric>          <numeric>
TR10090|c0_g2_i1_coral 1.98672027139201  0.0469534041233123  0.418043000342497
TR10487|c0_g1_i1_coral 1.99809885824924  0.0457059435120877  0.412518610214263
TR1069|c0_g1_i1_coral  2.26509966467448  0.0235065642111382  0.308653252532063
TR10748|c0_g1_i1_coral 3.19820220950252 0.00138287275835452 0.0720091267133405
TR10773|c0_g1_i1_coral 2.66638665702029 0.00766714549040745  0.173395444167676
TR10773|c1_g1_i1_coral 2.04411497416195  0.0409421901910667                 NA
> dim(genes4heatmap)
[1] 866   6
> data4heatmap<-scaledcounts[row.names(scaledcounts)%in%row.names(genes4heatmap),]
> dim(data4heatmap)
[1] 866  78
> head(data4heatmap)
                       RI_B_01_14 RI_B_01_18 RI_B_01_22 RI_B_02_14 RI_B_02_18 RI_B_02_22
TR10090|c0_g2_i1_coral    0.00000   3.468731   2.447866   3.772786    0.00000   0.000000
TR10487|c0_g1_i1_coral   10.94714   5.203096   8.567532   0.000000    0.00000   6.648979
TR1069|c0_g1_i1_coral     0.00000   0.000000   0.000000   7.545573    3.45517   6.648979
TR10748|c0_g1_i1_coral    0.00000   0.000000   2.447866   0.000000    0.00000   0.000000
TR10773|c0_g1_i1_coral    0.00000   6.070279   2.447866   3.772786    0.00000   0.000000
TR10773|c1_g1_i1_coral    0.00000   2.601548   4.895733   0.000000    0.00000   2.216326
                       RI_B_03_14 RI_B_03_22 RI_B_04_14 RI_B_04_18 RI_B_04_22 RI_B_05_14
TR10090|c0_g2_i1_coral   0.000000   3.818995   4.809473  3.6845136          0   0.570426
TR10487|c0_g1_i1_coral   9.010379   5.091993   2.404737  4.5032943          0   9.126817
TR1069|c0_g1_i1_coral    0.000000   0.000000   0.000000  0.0000000          0   0.000000
TR10748|c0_g1_i1_coral   2.574394   0.000000   4.007894  2.8657328          0   1.711278
TR10773|c0_g1_i1_coral   1.287197   0.000000   0.000000  0.4093904          0   0.000000
TR10773|c1_g1_i1_coral   5.148788   1.272998   0.000000  0.0000000          0   0.285213
                       RI_B_05_18 RI_B_05_22 RI_B_06_14 RI_B_06_18 RI_B_06_22 RI_B_07_14
TR10090|c0_g2_i1_coral   0.000000  2.4538305          0   4.827992          0   3.734168
TR10487|c0_g1_i1_coral   5.033716  0.8179435          0   2.758853          0   5.227835
TR1069|c0_g1_i1_coral    0.000000  0.0000000          0   0.000000          0   0.000000
TR10748|c0_g1_i1_coral   0.000000  0.0000000          0   0.000000          0   2.987334
TR10773|c0_g1_i1_coral   0.000000  0.0000000          0   0.000000          0   0.000000
TR10773|c1_g1_i1_coral   0.000000  0.8179435          0   0.000000          0   0.000000
                       RI_B_07_18 RI_B_07_22 RI_W_01_18 RI_W_01_22 RI_W_02_14 RI_W_02_18
TR10090|c0_g2_i1_coral   1.008773          0  12.257216   7.743994   4.651361  4.9947759
TR10487|c0_g1_i1_coral   5.043864          0   8.652152   6.195195  16.279762  2.9968656
TR1069|c0_g1_i1_coral    0.000000          0  10.094178   9.292792   0.000000  0.0000000
TR10748|c0_g1_i1_coral   0.000000          0   0.000000   1.548799   4.651361  0.9989552
TR10773|c0_g1_i1_coral   1.008773          0   7.931140  17.036786   0.000000 14.9843278
TR10773|c1_g1_i1_coral   0.000000          0   5.047089  18.585585   0.000000 10.9885071
                       RI_W_02_22 RI_W_03_14 RI_W_03_18 RI_W_03_22 RI_W_04_14 RI_W_04_18
TR10090|c0_g2_i1_coral   4.820288   3.044865   3.244480   1.581919    0.00000  7.4421015
TR10487|c0_g1_i1_coral   1.205072   7.307675   7.209956  14.237275   17.10086  5.4575411
TR1069|c0_g1_i1_coral    0.000000   0.000000   0.000000   0.000000    0.00000  0.0000000
TR10748|c0_g1_i1_coral   2.410144   2.435892   6.128462   4.218452    0.00000  0.4961401
TR10773|c0_g1_i1_coral   6.025360  23.140971  12.617422  29.001856    0.00000  1.9845604
TR10773|c1_g1_i1_coral   1.205072  10.352540   7.930951   7.382291    0.00000  1.4884203
                       RI_W_05_14 RI_W_05_18 RI_W_05_22 RI_W_06_14 RI_W_06_18 RI_W_06_22
TR10090|c0_g2_i1_coral   3.614931  10.107037   1.381659   3.133041   1.336966   7.790833
TR10487|c0_g1_i1_coral   4.066797   4.042815   0.000000   4.177388  13.369662  10.016785
TR1069|c0_g1_i1_coral    0.000000   0.000000   0.000000   0.000000   0.000000   0.000000
TR10748|c0_g1_i1_coral   2.711198   1.010704   0.000000   3.133041   2.673932   2.225952
TR10773|c0_g1_i1_coral   5.422396   2.021407   0.000000   5.221735   2.673932  10.016785
TR10773|c1_g1_i1_coral   3.614931   3.032111   0.000000   1.044347   2.673932   3.338928
                       RI_W_07_14 RI_W_07_18 RI_W_07_22 VA_B_01_14 VA_B_01_18 VA_B_01_22
TR10090|c0_g2_i1_coral   2.062318   1.118603   5.520462  10.204629   5.628251   5.690194
TR10487|c0_g1_i1_coral   3.437196  13.423242   8.280694  10.204629   6.494135  10.242350
TR1069|c0_g1_i1_coral    0.000000   0.000000   0.000000  33.165045   9.524732  17.639603
TR10748|c0_g1_i1_coral   2.749757   2.237207   0.000000   1.275579   1.298827   5.121175
TR10773|c0_g1_i1_coral   1.374879   2.237207   0.000000   6.377893   4.762366   2.845097
TR10773|c1_g1_i1_coral   2.062318   3.355810   2.760231   8.929051   6.061193   6.259214
                       VA_B_02_14 VA_B_02_18 VA_B_02_22 VA_B_03_14 VA_B_03_18 VA_B_03_22
TR10090|c0_g2_i1_coral   0.000000     0.0000   0.000000  10.929073   4.301848  3.5605530
TR10487|c0_g1_i1_coral   0.000000     0.0000  17.166789  10.929073   7.886721  7.8332166
TR1069|c0_g1_i1_coral   86.631891    44.0504  40.771123   0.000000   0.000000  0.0000000
TR10748|c0_g1_i1_coral  30.575962     0.0000   2.145849   3.643024   7.886721  3.5605530
TR10773|c0_g1_i1_coral   1.698665     0.0000   6.437546   0.000000   1.433949  0.7121106
TR10773|c1_g1_i1_coral   0.000000     2.5912   0.000000   0.000000   3.584873  0.7121106
                       VA_B_04_14 VA_B_04_18 VA_B_04_22 VA_B_05_14 VA_B_05_18 VA_B_05_22
TR10090|c0_g2_i1_coral  7.1085175   3.152383   0.000000   1.399244  0.5528859   5.441030
TR10487|c0_g1_i1_coral 15.1055996   4.053064   8.285065   4.547541 17.1394640  21.764122
TR1069|c0_g1_i1_coral   0.0000000   0.000000   0.000000   0.000000  0.0000000   0.000000
TR10748|c0_g1_i1_coral  2.6656940   0.000000   8.802882   1.049433  1.6586578   3.627354
TR10773|c0_g1_i1_coral  0.0000000   7.205447   8.285065   1.399244  1.1057719   0.000000
TR10773|c1_g1_i1_coral  0.8885647   8.556469   2.589083   0.000000  4.4230875   0.000000
                       VA_B_06_14 VA_B_06_18 VA_B_06_22 VA_B_07_14 VA_B_07_18 VA_B_07_22
TR10090|c0_g2_i1_coral   0.000000   4.206352   1.477470  1.4914137  15.552308   6.295498
TR10487|c0_g1_i1_coral   0.000000   8.412704   2.462449  3.7285342   5.184103   8.393997
TR1069|c0_g1_i1_coral   29.062864  16.825408   8.372327  0.0000000   0.000000   0.000000
TR10748|c0_g1_i1_coral   6.919730   0.000000   2.954939  6.7113616   0.000000   4.196999
TR10773|c0_g1_i1_coral   2.767892   0.000000   5.417388  1.4914137   2.962344   6.295498
TR10773|c1_g1_i1_coral   0.000000   2.523811   2.462449  0.7457068   0.000000   4.196999
                       VA_W_01_14 VA_W_01_18 VA_W_02_14 VA_W_02_18 VA_W_03_14 VA_W_03_22
TR10090|c0_g2_i1_coral   0.000000   3.866328  4.3614889  13.082767  6.9966052   3.130966
TR10487|c0_g1_i1_coral   6.699293   4.970993  1.7445956  13.082767  3.1096023   9.392897
TR1069|c0_g1_i1_coral    0.000000   0.000000  0.0000000   0.000000  0.0000000   0.000000
TR10748|c0_g1_i1_coral   2.871126   2.209330  0.8722978   0.000000  0.7774006   3.757159
TR10773|c0_g1_i1_coral   5.742251   1.104665  0.0000000   3.924830  1.5548011   2.504773
TR10773|c1_g1_i1_coral   0.000000   3.866328  0.0000000   5.233107  0.7774006   2.504773
                       VA_W_04_14 VA_W_04_18 VA_W_04_22 VA_W_05_14 VA_W_05_18 VA_W_05_22
TR10090|c0_g2_i1_coral   2.053504   7.705540 10.8488424    0.00000   2.748941   7.427894
TR10487|c0_g1_i1_coral   3.593631  13.003099  1.4793876    0.00000   8.246822   8.665876
TR1069|c0_g1_i1_coral    0.000000   0.000000  0.0000000    0.00000   0.000000   0.000000
TR10748|c0_g1_i1_coral   6.673887   9.150329  7.3969380   14.61366   2.748941   9.903859
TR10773|c0_g1_i1_coral   1.026752   0.000000  0.4931292    0.00000   0.000000   0.000000
TR10773|c1_g1_i1_coral   1.026752   0.000000  0.0000000    0.00000   2.199153   1.237982
                       VA_W_06_14 VA_W_06_18 VA_W_06_22 VA_W_07_14 VA_W_07_18 VA_W_07_22
TR10090|c0_g2_i1_coral   3.025641  0.8631729   0.000000   5.517448   3.382824   2.842023
TR10487|c0_g1_i1_coral  10.085470  1.7263459  11.466093   7.093862   6.765648   3.789363
TR1069|c0_g1_i1_coral    0.000000  0.0000000   0.000000   0.000000   0.000000   0.000000
TR10748|c0_g1_i1_coral   2.017094  6.0422105   4.410036   0.000000   3.382824   1.894682
TR10773|c0_g1_i1_coral   0.000000  1.7263459   0.000000   0.000000   0.000000   0.000000
TR10773|c1_g1_i1_coral   2.017094  0.8631729   5.292043   0.000000   0.000000   0.000000
> temp = as.matrix(rowMeans(data4heatmap))
> head(temp)
                           [,1]
TR10090|c0_g2_i1_coral 3.657565
TR10487|c0_g1_i1_coral 6.571698
TR1069|c0_g1_i1_coral  4.142052
TR10748|c0_g1_i1_coral 2.936423
TR10773|c0_g1_i1_coral 3.025158
TR10773|c1_g1_i1_coral 2.328759
> scaledmatrix<-matrix(data=temp, nrow=nrow(data4heatmap), ncol=ncol(data4heatmap), byrow=FALSE)
> data4heatmapscaled = data4heatmap/scaledmatrix
> head(data4heatmapscaled)
                       RI_B_01_14 RI_B_01_18 RI_B_01_22 RI_B_02_14 RI_B_02_18 RI_B_02_22
TR10090|c0_g2_i1_coral   0.000000  0.9483717  0.6692613   1.031502  0.0000000  0.0000000
TR10487|c0_g1_i1_coral   1.665801  0.7917431  1.3037015   0.000000  0.0000000  1.0117598
TR1069|c0_g1_i1_coral    0.000000  0.0000000  0.0000000   1.821699  0.8341687  1.6052378
TR10748|c0_g1_i1_coral   0.000000  0.0000000  0.8336218   0.000000  0.0000000  0.0000000
TR10773|c0_g1_i1_coral   0.000000  2.0065992  0.8091699   1.247137  0.0000000  0.0000000
TR10773|c1_g1_i1_coral   0.000000  1.1171391  2.1022922   0.000000  0.0000000  0.9517198
                       RI_B_03_14 RI_B_03_22 RI_B_04_14 RI_B_04_18 RI_B_04_22 RI_B_05_14
TR10090|c0_g2_i1_coral  0.0000000  1.0441360  1.3149387  1.0073680          0  0.1559579
TR10487|c0_g1_i1_coral  1.3710885  0.7748368  0.3659232  0.6852559          0  1.3888066
TR1069|c0_g1_i1_coral   0.0000000  0.0000000  0.0000000  0.0000000          0  0.0000000
TR10748|c0_g1_i1_coral  0.8767109  0.0000000  1.3648899  0.9759263          0  0.5827764
TR10773|c0_g1_i1_coral  0.4254975  0.0000000  0.0000000  0.1353286          0  0.0000000
TR10773|c1_g1_i1_coral  2.2109576  0.5466423  0.0000000  0.0000000          0  0.1224742
                       RI_B_05_18 RI_B_05_22 RI_B_06_14 RI_B_06_18 RI_B_06_22 RI_B_07_14
TR10090|c0_g2_i1_coral  0.0000000  0.6708919          0  1.3200019          0  1.0209437
TR10487|c0_g1_i1_coral  0.7659688  0.1244646          0  0.4198082          0  0.7955075
TR1069|c0_g1_i1_coral   0.0000000  0.0000000          0  0.0000000          0  0.0000000
TR10748|c0_g1_i1_coral  0.0000000  0.0000000          0  0.0000000          0  1.0173377
TR10773|c0_g1_i1_coral  0.0000000  0.0000000          0  0.0000000          0  0.0000000
TR10773|c1_g1_i1_coral  0.0000000  0.3512357          0  0.0000000          0  0.0000000
                       RI_B_07_18 RI_B_07_22 RI_W_01_18 RI_W_01_22 RI_W_02_14 RI_W_02_18
TR10090|c0_g2_i1_coral  0.2758045          0   3.351196  2.1172541   1.271710  1.3656016
TR10487|c0_g1_i1_coral  0.7675130          0   1.316578  0.9427084   2.477254  0.4560261
TR1069|c0_g1_i1_coral   0.0000000          0   2.436999  2.2435236   0.000000  0.0000000
TR10748|c0_g1_i1_coral  0.0000000          0   0.000000  0.5274440   1.584023  0.3401946
TR10773|c0_g1_i1_coral  0.3334612          0   2.621728  5.6317019   0.000000  4.9532387
TR10773|c1_g1_i1_coral  0.0000000          0   2.167287  7.9808953   0.000000  4.7186100
                       RI_W_02_22 RI_W_03_14 RI_W_03_18 RI_W_03_22 RI_W_04_14 RI_W_04_18
TR10090|c0_g2_i1_coral  1.3178956  0.8324842  0.8870602  0.4325062   0.000000  2.0347150
TR10487|c0_g1_i1_coral  0.1833730  1.1119920  1.0971223  2.1664531   2.602198  0.8304614
TR1069|c0_g1_i1_coral   0.0000000  0.0000000  0.0000000  0.0000000   0.000000  0.0000000
TR10748|c0_g1_i1_coral  0.8207755  0.8295438  2.0870501  1.4365953   0.000000  0.1689607
TR10773|c0_g1_i1_coral  1.9917509  7.6495091  4.1708314  9.5868908   0.000000  0.6560188
TR10773|c1_g1_i1_coral  0.5174739  4.4455171  3.4056552  3.1700530   0.000000  0.6391473
                       RI_W_05_14 RI_W_05_18 RI_W_05_22 RI_W_06_14 RI_W_06_18 RI_W_06_22
TR10090|c0_g2_i1_coral  0.9883436  2.7633244  0.3777539  0.8565921  0.3655346  2.1300602
TR10487|c0_g1_i1_coral  0.6188351  0.6151858  0.0000000  0.6356634  2.0344306  1.5242310
TR1069|c0_g1_i1_coral   0.0000000  0.0000000  0.0000000  0.0000000  0.0000000  0.0000000
TR10748|c0_g1_i1_coral  0.9232995  0.3441955  0.0000000  1.0669582  0.9106087  0.7580488
TR10773|c0_g1_i1_coral  1.7924342  0.6681991  0.0000000  1.7261033  0.8838986  3.3111614
TR10773|c1_g1_i1_coral  1.5522989  1.3020286  0.0000000  0.4484564  1.1482219  1.4337799
                       RI_W_07_14 RI_W_07_18 RI_W_07_22 VA_B_01_14 VA_B_01_18 VA_B_01_22
TR10090|c0_g2_i1_coral  0.5638500  0.3058329   1.509327  2.7900066  1.5387973   1.555733
TR10487|c0_g1_i1_coral  0.5230302  2.0425836   1.260054  1.5528148  0.9881975   1.558555
TR1069|c0_g1_i1_coral   0.0000000  0.0000000   0.000000  8.0069110  2.2995199   4.258662
TR10748|c0_g1_i1_coral  0.9364308  0.7618816   0.000000  0.4343988  0.4423160   1.744018
TR10773|c0_g1_i1_coral  0.4544816  0.7395340   0.000000  2.1082846  1.5742538   0.940479
TR10773|c1_g1_i1_coral  0.8855865  1.4410293   1.185280  3.8342522  2.6027562   2.687789
                       VA_B_02_14 VA_B_02_18 VA_B_02_22 VA_B_03_14 VA_B_03_18 VA_B_03_22
TR10090|c0_g2_i1_coral  0.0000000   0.000000  0.0000000   2.988074  1.1761509  0.9734764
TR10487|c0_g1_i1_coral  0.0000000   0.000000  2.6122305   1.663052  1.2001041  1.1919624
TR1069|c0_g1_i1_coral  20.9152088  10.634922  9.8432176   0.000000  0.0000000  0.0000000
TR10748|c0_g1_i1_coral 10.4126549   0.000000  0.7307695   1.240633  2.6858257  1.2125476
TR10773|c0_g1_i1_coral  0.5615127   0.000000  2.1280034   0.000000  0.4740081  0.2353962
TR10773|c1_g1_i1_coral  0.0000000   1.112696  0.0000000   0.000000  1.5393918  0.3057897
                       VA_B_04_14 VA_B_04_18 VA_B_04_22 VA_B_05_14 VA_B_05_18 VA_B_05_22
TR10090|c0_g2_i1_coral  1.9435111  0.8618804   0.000000  0.3825615  0.1511623   1.487610
TR10487|c0_g1_i1_coral  2.2985841  0.6167454   1.260719  0.6919888  2.6080725   3.311796
TR1069|c0_g1_i1_coral   0.0000000  0.0000000   0.000000  0.0000000  0.0000000   0.000000
TR10748|c0_g1_i1_coral  0.9078031  0.0000000   2.997825  0.3573847  0.5648565   1.235297
TR10773|c0_g1_i1_coral  0.0000000  2.3818420   2.738722  0.4625357  0.3655254   0.000000
TR10773|c1_g1_i1_coral  0.3815614  3.6742606   1.111786  0.0000000  1.8993321   0.000000
                       VA_B_06_14 VA_B_06_18 VA_B_06_22 VA_B_07_14 VA_B_07_18 VA_B_07_22
TR10090|c0_g2_i1_coral  0.0000000   1.150042  0.4039490  0.4077614  4.2520938   1.721227
TR10487|c0_g1_i1_coral  0.0000000   1.280142  0.3747052  0.5673624  0.7888529   1.277295
TR1069|c0_g1_i1_coral   7.0165371   4.062094  2.0212992  0.0000000  0.0000000   0.000000
TR10748|c0_g1_i1_coral  2.3565165   0.000000  1.0063056  2.2855567  0.0000000   1.429289
TR10773|c0_g1_i1_coral  0.9149579   0.000000  1.7907788  0.4930036  0.9792364   2.081048
TR10773|c1_g1_i1_coral  0.0000000   1.083758  1.0574082  0.3202164  0.0000000   1.802247
                       VA_W_01_14 VA_W_01_18 VA_W_02_14 VA_W_02_18 VA_W_03_14 VA_W_03_22
TR10090|c0_g2_i1_coral  0.0000000  1.0570771  1.1924571   3.576907  1.9129136  0.8560247
TR10487|c0_g1_i1_coral  1.0194159  0.7564245  0.2654711   1.990774  0.4731810  1.4292954
TR1069|c0_g1_i1_coral   0.0000000  0.0000000  0.0000000   0.000000  0.0000000  0.0000000
TR10748|c0_g1_i1_coral  0.9777629  0.7523882  0.2970613   0.000000  0.2647441  1.2795019
TR10773|c0_g1_i1_coral  1.8981660  0.3651595  0.0000000   1.297397  0.5139571  0.8279809
TR10773|c1_g1_i1_coral  0.0000000  1.6602522  0.0000000   2.247165  0.3338261  1.0755824
                       VA_W_04_14 VA_W_04_18 VA_W_04_22 VA_W_05_14 VA_W_05_18 VA_W_05_22
TR10090|c0_g2_i1_coral  0.5614402   2.106741  2.9661383   0.000000  0.7515768   2.030831
TR10487|c0_g1_i1_coral  0.5468346   1.978651  0.2251150   0.000000  1.2548999   1.318666
TR1069|c0_g1_i1_coral   0.0000000   0.000000  0.0000000   0.000000  0.0000000   0.000000
TR10748|c0_g1_i1_coral  2.2727947   3.116148  2.5190299   4.976688  0.9361528   3.372763
TR10773|c0_g1_i1_coral  0.3394044   0.000000  0.1630094   0.000000  0.0000000   0.000000
TR10773|c1_g1_i1_coral  0.4409008   0.000000  0.0000000   0.000000  0.9443452   0.531606
                       VA_W_06_14 VA_W_06_18 VA_W_06_22 VA_W_07_14 VA_W_07_18 VA_W_07_22
TR10090|c0_g2_i1_coral  0.8272283  0.2359966   0.000000   1.508503  0.9248843  0.7770259
TR10487|c0_g1_i1_coral  1.5346826  0.2626940   1.744769   1.079457  1.0295131  0.5766186
TR1069|c0_g1_i1_coral   0.0000000  0.0000000   0.000000   0.000000  0.0000000  0.0000000
TR10748|c0_g1_i1_coral  0.6869221  2.0576770   1.501839   0.000000  1.1520220  0.6452345
TR10773|c0_g1_i1_coral  0.0000000  0.5706631   0.000000   0.000000  0.0000000  0.0000000
TR10773|c1_g1_i1_coral  0.8661668  0.3706578   2.272473   0.000000  0.0000000  0.0000000
> dim(data4heatmapscaled)
[1] 866  78
> pairs.breaks <- seq(0, 3.0, by=0.1)
> length(pairs.breaks)
[1] 31
> mycol <- colorpanel(n=30, low="black", high="yellow")
> pdf(file="XXXXXX_byrow.pdf",7,7)
> heatmap.2(data.matrix(data4heatmapscaled), Rowv=T, Colv=F, dendrogram = c("row"), scale="none", keysize=1, breaks=pairs.breaks, col=mycol, trace = "none", symkey = F, density.info = "density", colsep=c(24), sepcolor=c("white"), sepwidth=c(.1,.1), margins=c(10,10), labRow=F)
> dev.off()
RStudioGD 
        2 
> pdf(file="XXXXXX_bycolumn.pdf",7,7)
> heatmap.2(data.matrix(data4heatmapscaled), Rowv=T, Colv=T, dendrogram = c("col"), scale="none", keysize=1, breaks=pairs.breaks, col=mycol, trace = "none", symkey = F, density.info = "density", colsep=c(24), sepcolor=c("white"), sepwidth=c(.1,.1), margins=c(10,10), labRow=F)
> dev.off()
RStudioGD 
        2 
> plotPCA(vstCounts[rownames(vstCounts)%in%row.names(genes4heatmap),], intgroup="Origin")
> plotPCA(vstCounts[rownames(vstCounts)%in%row.names(genes4heatmap),], intgroup="SymState")
> plotPCA(vstCounts[rownames(vstCounts)%in%row.names(genes4heatmap),], intgroup="Temp")
> plotPCA(vstCounts[rownames(vstCounts)%in%row.names(genes4heatmap),], intgroup="Origin_SymState")
> plotPCA(vstCounts[rownames(vstCounts)%in%row.names(genes4heatmap),], intgroup="Origin_SymState_Temp")
> pdf(file="866_RIvsVA_PCAv2.pdf",14, 14)
> plotPCA(vstCounts[rownames(vstCounts)%in%row.names(genes4heatmap),], intgroup="Origin")
> dev.off()
pdf 
  4 
> prop.nullv3 <- apply(countsTable[rownames(countsTable)%in%row.names(genes4heatmap),], 2, function(x) 100*mean(x==0))
> barplot(prop.nullv3, main="Percentage of null counts per sample", 
+         horiz=TRUE, cex.names=0.5, las=1, 
+         col=conds$Origin_SymState_Temp, ylab='Samples', xlab='% of null counts')
> pdf(file="ResNullCountsv2.pdf",14, 14)
> barplot(prop.nullv3, main="Percentage of null counts per sample", 
+         horiz=TRUE, cex.names=0.5, las=1, 
+         col=conds$Origin_SymState_Temp, ylab='Samples', xlab='% of null counts')
> dev.off()
pdf 
  4 
> distsv2<-dist(t(assay(vstCounts[rownames(vstCounts)%in%row.names(genes4heatmap),])))
> plot(hclust(distsv2))
> heatmap.2(as.matrix(distsv2), key=F, trace="none",
+           col=colorpanel(100, "black", "white"),
+           margin=c(10, 10))
> res<-resOrigin
> Annotations<-read.delim("Assembly_GoodCoralSymbiont_suffixed_totalannotated.txt")
> head(res)
log2 fold change (MLE): Origin VA vs RI 
Wald test p-value: Origin VA vs RI 
DataFrame with 6 rows and 6 columns
                               baseMean      log2FoldChange             lfcSE
                              <numeric>           <numeric>         <numeric>
TR10083|c0_g2_i1_coral   5.366479327573  -0.271242746289843 0.446224512750353
TR10090|c0_g1_i1_coral 2.70436251126018    1.11251170496561 0.589306266446119
TR10090|c0_g2_i1_coral 3.65756460141883   0.943134641716211 0.474719393211504
TR10103|c0_g1_i1_coral  2.9127886212765  0.0386642676540012 0.456719612483097
TR10108|c0_g1_i1_coral 6.31144026709945 -0.0179009694277555 0.461957599914831
TR10132|c0_g1_i1_coral  9.2673703948612  -0.264990306479184 0.677607561801266
                                      stat             pvalue              padj
                                 <numeric>          <numeric>         <numeric>
TR10083|c0_g2_i1_coral  -0.607861600022842  0.543279269700006 0.865660813784253
TR10090|c0_g1_i1_coral    1.88783281005095 0.0590483989759312                NA
TR10090|c0_g2_i1_coral    1.98672027139201 0.0469534041233123 0.418043000342497
TR10103|c0_g1_i1_coral  0.0846564644854882  0.932534507970102 0.984590265229257
TR10108|c0_g1_i1_coral -0.0387502433795997  0.969089515041603 0.992149683420423
TR10132|c0_g1_i1_coral  -0.391067516682912  0.695747330435347 0.921516804624192
> sum(res$log2FoldChange!=0)
[1] 7659
> genes<-as.integer(p.adjust(res$pvalue[res$log2FoldChange!=0 & !is.na(res$pvalue)], method="BH")<.05)
> names(genes)<-row.names(res[res$log2FoldChange!=0 & !is.na(res$pvalue),])
> table(genes)
genes
   0    1 
7533  116 
> goterms<-strsplit(as.character(Annotations$GO), split=" // ")
> names(goterms)<-Annotations$ContigName
> pwf<-nullp(genes, bias.data=Annotations[Annotations$ContigName%in%names(genes),"ContigLength"])
Warning message:
In pcls(G) : initial point very close to some inequality constraints
> GOGOGO<-goseq(pwf,gene2cat=goterms)
Using manually entered categories.
Calculating the p-values...
'select()' returned 1:1 mapping between keys and columns
> GOGOGO$padj<-p.adjust(GOGOGO$over_represented_pvalue, method="fdr")
> sum(GOGOGO$padj<0.2, na.rm=T)
[1] 3
> sum(GOGOGO$padj<0.1, na.rm=T)
[1] 2
> sum(GOGOGO$padj<0.05, na.rm=T)
[1] 2
> GOGOGO[GOGOGO$padj<0.05,]
       category over_represented_pvalue under_represented_pvalue numDEInCat numInCat
1326 GO:0006032            3.838364e-08                        1          5        8
74   GO:0000272            8.726516e-07                        1          5       13
                                 term ontology         padj
1326         chitin catabolic process       BP 0.0003557012
74   polysaccharide catabolic process       BP 0.0040434313
> GOTERM[["SOMEGOTERM"]]
NULL
> EnGOS<-GOGOGO$category[p.adjust(GOGOGO$over_represented_pvalue, method="BH")<.05]
> for(go in EnGOS){
+   print(GOTERM[[go]])
+   cat("--------------------------------------\n")}
GOID: GO:0006032
Term: chitin catabolic process
Ontology: BP
Definition: The chemical reactions and pathways resulting in the breakdown of
    chitin, a linear polysaccharide consisting of beta-(1->4)-linked
    N-acetyl-D-glucosamine residues.
Synonym: beta-1,4-linked N-acetylglucosamine catabolic process
Synonym: beta-1,4-linked N-acetylglucosamine catabolism
Synonym: chitin breakdown
Synonym: chitin catabolism
Synonym: chitin degradation
--------------------------------------
GOID: GO:0000272
Term: polysaccharide catabolic process
Ontology: BP
Definition: The chemical reactions and pathways resulting in the breakdown of a
    polysaccharide, a polymer of many (typically more than 10) monosaccharide
    residues linked glycosidically.
Synonym: multicellular organismal polysaccharide catabolic process
Synonym: polysaccharide breakdown
Synonym: polysaccharide catabolism
Synonym: polysaccharide degradation
Synonym: GO:0044244
Secondary: GO:0044244
--------------------------------------
> 
> 
> 
> 
> names(Annotations)
 [1] "ContigName"              "ContigLength"           
 [3] "topnrMatch"              "topnrEvalue"            
 [5] "topnrAlignmentLength"    "topnrPercMatch"         
 [7] "nobadwordnrMatch"        "nobadwordnrEvalue"      
 [9] "nobadwordnrAlignLength"  "nobadwordnrPercentMatch"
[11] "Uniprotmatch"            "X._identity"            
[13] "evalue"                  "ID"                     
[15] "Description"             "KEGG"                   
[17] "KEGGKO"                  "PFAM"                   
[19] "GO"                      "GOCC"                   
[21] "GOBP"                    "GOMF"                   
[23] "Keywords"               
> head(Annotations)
              ContigName ContigLength
1   TR10030|c0_g1_i1_sym          523
2   TR10043|c0_g1_i1_sym          512
3   TR10050|c0_g1_i1_sym          793
4 TR10054|c0_g1_i1_coral          548
5 TR10054|c0_g2_i1_coral          811
6   TR10082|c0_g2_i1_sym         1176
                                                                                                                                                              topnrMatch
1                                                                           gnl|BL_ORD_ID|101380155 OLP92908.1 Sodium/calcium exchanger 1 [Symbiodinium microadriaticum]
2                                                             gnl|BL_ORD_ID|101372287 OLP84974.1 hypothetical protein AK812_SmicGene34099 [Symbiodinium microadriaticum]
3                                                                                                                                                          No_sig_nr_hit
4                                                                                     gnl|BL_ORD_ID|110384373 XP_020612383.1 titin-like isoform X4 [Orbicella faveolata]
5                                                                                     gnl|BL_ORD_ID|110384422 XP_020612382.1 titin-like isoform X3 [Orbicella faveolata]
6 gnl|BL_ORD_ID|14605113 XP_002785881.1 sugar transporter, putative [Perkinsus marinus ATCC 50983] EER17677.1 sugar transporter, putative [Perkinsus marinus ATCC 50983]
    topnrEvalue topnrAlignmentLength topnrPercMatch
1   5.74325e-73                  167           0.74
2   5.42819e-23                   80           0.66
3 No_sig_nr_hit        No_sig_nr_hit  No_sig_nr_hit
4   8.93129e-73                  182           0.90
5   1.31886e-95                  250           0.82
6   1.07378e-49                  289           0.37
                                                                                                                                                        nobadwordnrMatch
1                                                                           gnl|BL_ORD_ID|101380155 OLP92908.1 Sodium/calcium exchanger 1 [Symbiodinium microadriaticum]
2                                                                  gnl|BL_ORD_ID|51120734 XP_012166226.1 E3 ubiquitin-protein ligase RNF146, partial [Bombus terrestris]
3                                                                                                                                                          No_sig_nr_hit
4                                                                                     gnl|BL_ORD_ID|110384373 XP_020612383.1 titin-like isoform X4 [Orbicella faveolata]
5                                                                                     gnl|BL_ORD_ID|110384422 XP_020612382.1 titin-like isoform X3 [Orbicella faveolata]
6 gnl|BL_ORD_ID|14605113 XP_002785881.1 sugar transporter, putative [Perkinsus marinus ATCC 50983] EER17677.1 sugar transporter, putative [Perkinsus marinus ATCC 50983]
  nobadwordnrEvalue nobadwordnrAlignLength nobadwordnrPercentMatch
1       5.74325e-73                    167                    0.74
2        8.8118e-05                     58                    0.38
3     No_sig_nr_hit          No_sig_nr_hit           No_sig_nr_hit
4       8.93129e-73                    182                    0.90
5       1.31886e-95                    250                    0.82
6       1.07378e-49                    289                    0.37
     Uniprotmatch   X._identity    evalue               ID
1      A0A1Q9DCJ4        74.251  3.76e-73 A0A1Q9DCJ4_SYMMI
2          C0HBT3        29.114  3.65e-05      RN146_SALSA
3 No_Uniprotmatch No_%_identity No_evalue            No_ID
4      A0A2B4SVR7        77.473  8.77e-57 A0A2B4SVR7_STYPI
5      A0A2B4SVR7        72.112  5.57e-76 A0A2B4SVR7_STYPI
6          Q02334        21.402  2.12e-05      UGTP1_CAEEL
                                                                          Description
1                            Sodium/calcium exchanger 1 {ECO:0000313|EMBL:OLP92908.1}
2                                                  E3 ubiquitin-protein ligase rnf146
3                                                                      No_Description
4 Golgi-associated plant pathogenesis-related protein 1 {ECO:0000313|EMBL:PFX34774.1}
5 Golgi-associated plant pathogenesis-related protein 1 {ECO:0000313|EMBL:PFX34774.1}
6                                                        UDP-galactose translocator 1
              KEGG    KEGGKO                                  PFAM
1          No_KEGG No_KEGGKO PF00063; Myosin_head,  PF07647; SAM_2
2   sasa:100380617    K15700                          PF02825; WWE
3          No_KEGG No_KEGGKO                               No_PFAM
4          No_KEGG No_KEGGKO                          PF00188; CAP
5          No_KEGG No_KEGGKO                          PF00188; CAP
6 cel:CELE_ZK370.7    K15272               PF04142; Nuc_sug_transp
                                                                                                                                                      GO
1                                                                                     GO:0016021 // GO:0016459 // GO:0005524 // GO:0003774 // GO:0003676
2 GO:0005829 // GO:0005634 // GO:0072572 // GO:0061630 // GO:0004842 // GO:0008270 // GO:0090263 // GO:0051865 // GO:0070936 // GO:0006511 // GO:0016055
3                                                                                                                                                  No_GO
4                                                                                                                                             GO:0005576
5                                                                                                                                             GO:0005576
6                                                         GO:0060473 // GO:0005794 // GO:0005797 // GO:0030173 // GO:0015165 // GO:0015136 // GO:0008643
                                                                                                                                                                                                                                                       GOCC
1                                                                                                                                                                                                                                                   No_GOBP
2 positive regulation of canonical Wnt signaling pathway (GO:0090263);protein autoubiquitination (GO:0051865);protein K48-linked ubiquitination (GO:0070936);ubiquitin-dependent protein catabolic process (GO:0006511);Wnt signaling pathway (GO:0016055);
3                                                                                                                                                                                                                                                   No_GOCC
4                                                                                                                                                                                                                                                   No_GOBP
5                                                                                                                                                                                                                                                   No_GOBP
6                                                                                                                                                                                                                      carbohydrate transport (GO:0008643);
                                                                                                                                                                      GOBP
1                                                                                  ATP binding (GO:0005524);motor activity (GO:0003774);nucleic acid binding (GO:0003676);
2 poly-ADP-D-ribose binding (GO:0072572);ubiquitin protein ligase activity (GO:0061630);ubiquitin-protein transferase activity (GO:0004842);zinc ion binding (GO:0008270);
3                                                                                                                                                                  No_GOBP
4                                                                                                                                                                  No_GOMF
5                                                                                                                                                                  No_GOMF
6                                 pyrimidine nucleotide-sugar transmembrane transporter activity (GO:0015165);sialic acid transmembrane transporter activity (GO:0015136);
                                                                                                                                              GOMF
1                                                                         integral component of membrane (GO:0016021);myosin complex (GO:0016459);
2                                                                                                       cytosol (GO:0005829);nucleus (GO:0005634);
3                                                                                                                                          No_GOMF
4                                                                                                               extracellular region (GO:0005576);
5                                                                                                               extracellular region (GO:0005576);
6 cortical granule (GO:0060473);Golgi apparatus (GO:0005794);Golgi medial cisterna (GO:0005797);integral component of Golgi membrane (GO:0030173);
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                Keywords
1 ATP-binding {ECO:0000256|SAAS:SAAS00875240};Coiled coil {ECO:0000256|SAM:Coils};Membrane {ECO:0000256|SAM:Phobius};Metal-binding {ECO:0000256|PROSITE-ProRule:PRU00175};Motor protein {ECO:0000256|SAAS:SAAS01033784};Myosin {ECO:0000256|SAAS:SAAS01033784};Nucleotide-binding {ECO:0000256|SAAS:SAAS00875240};Transmembrane {ECO:0000256|SAM:Phobius};Transmembrane helix {ECO:0000256|SAM:Phobius};Zinc {ECO:0000256|PROSITE-ProRule:PRU00175};Zinc-finger {ECO:0000256|PROSITE-ProRule:PRU00175}.;
2                                                                                                                                                                                                                                                                                                                                                      Complete proteome;Cytoplasm;Metal-binding;Nucleus;Reference proteome;Transferase;Ubl conjugation pathway;Wnt signaling pathway;Zinc;Zinc-finger.;
3                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            No_keywords
4                                                                                                                                                                                                                                                                                                                                                     Coiled coil {ECO:0000256|SAM:Coils};Complete proteome {ECO:0000313|Proteomes:UP000225706};Reference proteome {ECO:0000313|Proteomes:UP000225706}.;
5                                                                                                                                                                                                                                                                                                                                                     Coiled coil {ECO:0000256|SAM:Coils};Complete proteome {ECO:0000313|Proteomes:UP000225706};Reference proteome {ECO:0000313|Proteomes:UP000225706}.;
6                                                                                                                                                                                                                                                                                                                                                                                            Complete proteome;Membrane;Reference proteome;Sugar transport;Transmembrane;Transmembrane helix;Transport.;
> dim(genes4heatmap)
[1] 866   6
