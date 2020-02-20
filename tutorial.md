## __Alignment Tutorial | Bowtie__

--- 

![image](RNAseqWorkflow.png | width=100)

After quality control and optional adapter trimming of our data, alignment is usually the next step. Alignment tools provide us to determine where in the genome the reads originated from. To apply this procedure, we first need a reference genome to map our reads. If your read is spliced such as RNA-seq data, then, spliced transcripts alignment tools such as STAR aligner would be the right choice. 

How does alignment algorithm work?

![image](aln.jpg | width=100)

Reads are aligned to a reference sequence. The alignment process may allow one or more mismatches between each individual read and the reference sequence. The alignment of the reads generates a layout. Based on the majority base call, the layout produces a consensus sequence. 
___

### __Bowtie Syntax__
___
bowtie-build:

    bowtie-build [options]* <reference_in> <ebwt_base>


bowtie:

    bowtie [options]* <ebwt> {-1 <m1> -2 <m2> | --12 <r> | --interleaved <i> | <s>} [<hit>]

___
### __Hands-on__
___

1. Get the tutorial material

        cp -r /cta/users/eekmen/gwsta_alignment_tutorial gwsta_alignment_tutorial
2. Unzip the .gz files in __reads__ directory. 

        gunzip *.gz


3. Creating Index Files in __index__ directory:

       bowtie-build e_coli.fna e_coli

4. Single-end Alignment:

       bowtie index/e_coli reads/CZB152.solexa.fastq e_coli_solexa.map

5. Paired-end Alignment:

       bowtie -p 2 index/e_coli -1 reads/b95edefdb9d82cb2423d97172223bbd4_1.fastq -2 reads/b95edefdb9d82cb2423d97172223bbd4_2.fastq e_coli_paired.map

___

### __Some Links__

1. Pre-built indexes: https://support.illumina.com/sequencing/sequencing_software/igenome.html
___
### __References:__

1. Langmead B, Salzberg S. Fast gapped-read alignment with Bowtie 2. Nature Methods. 2012, 9:357-359.

