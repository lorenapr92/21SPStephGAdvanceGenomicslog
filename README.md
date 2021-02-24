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

