# Introduction-to-Script-Programming

Write a script in python, bash, perl or a combination of the three that will perform the
following:
## PART 1

1. Read in a fasta file that contains multiple DNA sequences. These sequences are made up
of upper and lower cases. The upper cases indicate exons, the lower cases indicate
introns. As you might know, only the exons are translated and transcribed to proteins
based on the codon mapping. Each 3 nucleotides map for one amino acid.
Each sequence has its own ID and header starting with “>”. After reading the sequences,
print out the number of sequences in the files.

3. For each sequence compute the number of exons and introns as well as the average
length of the exons and introns. You also need to compute the proportion of each
amino acid, A, C, G, T in the Exon and Intron. As an example, if you have the following
sequence

>Sequence1
ccgtgctgcagctacgcagtcatggACACGTCAGCGTACGacgatcgactgcagACGAGTCGACGTTAGCcac
aaccgctcggc
>
mRNA -> ACA CGU CAG CGU ACG ACG AGU CGA CGU UAG C
protein -> XY
In this sequence there are 2 exons (highlighted in green) and one intron (highlighted in
cyan).
The lower case before the first exon and after that last exon are not considered as
introns but rather upper stream and lower stream sequences.
Your script should print out a table (tab delimited) with proper spacing indicating the
following (CAREFUL WITH THE SPACING)
This table should be written to a file called DNAstats.txt

SequenceID #Exons #Introns AvgExonLength AvgIntronLeng %A in Exon %C In Exon %G In Exon %T In Exon %A in Intron %C In Intron %G In Intron %T In Intron

3. After writing the file you should prompt to the user that the file was created.

4. You then ask the user to enter the ID of a sequence and print out on the terminal all the
statistics for that sequence from the file. You should read it from the file created in step
2 and print it on the terminal. In case the sequence is not there, you prompt the user
that it is not there and ask him/her to enter another one.

5. For the sequence selected, you need to print out the mRNA for it and the peptide
protein sequence that corresponds to it. The mRNA is the combination of all the exons
for that sequence. So you need to combine all the upper case letters in the sequence
and replace all the Ts with Us. The protein sequence is the translation of the codons
(3bases in mRNA code for 1 peptide using the codon table)

6. You need also to print out the RANGE and AVERAGE of melting temperature of the
primers for that sequence. For this you need to consider the lower case letter before the
first exon (highlighted in yellow). You need then to consider a window of 20 bases, and
for each window 20, you compute the melting temperature using the following formula
Tm = ( A + T ) ´ 2°C + ( C + G ) ´ 4°C
So once you compute the Tm for each window of size 20, you print out the Range, minmax,
and the average. In the example above there are 21 lower case characters before
the first exon (yellow), so there are 2 windows of 20 (ccgtgctgcagctacgcagt and
cgtgctgcagctacgcagtg)

## PART 2
Write a reverse transcription function that takes as argument a protein sequence and
generates all the possible mRNA sequences that can lead to this protein.
The function should also compute for each mRNA the %CG content ( how many C and G
are in the sequence compared to the total length).
You should then print out all the mRNA with their %GC content from lowest %GC
content to highest.
Choose the most probable mRNA sequence to be the one with the %GC content closer
to 50 and print it out as well.


map = {"UUU":"F", "UUC":"F", "UUA":"L", "UUG":"L",
"UCU":"S", "UCC":"s", "UCA":"S", "UCG":"S",
"UAU":"Y", "UAC":"Y", "UAA":"STOP", "UAG":"STOP",
"UGU":"C", "UGC":"C", "UGA":"STOP", "UGG":"W",
"CUU":"L", "CUC":"L", "CUA":"L", "CUG":"L",
"CCU":"P", "CCC":"P", "CCA":"P", "CCG":"P",
"CAU":"H", "CAC":"H", "CAA":"Q", "CAG":"Q",
"CGU":"R", "CGC":"R", "CGA":"R", "CGG":"R",
"AUU":"I", "AUC":"I", "AUA":"I", "AUG":"M",
"ACU":"T", "ACC":"T", "ACA":"T", "ACG":"T",
"AAU":"N", "AAC":"N", "AAA":"K", "AAG":"K",
"AGU":"S", "AGC":"S", "AGA":"R", "AGG":"R",
"GUU":"V", "GUC":"V", "GUA":"V", "GUG":"V",
"GCU":"A", "GCC":"A", "GCA":"A", "GCG":"A",
"GAU":"D", "GAC":"D", "GAA":"E", "GAG":"E",
"GGU":"G", "GGC":"G", "GGA":"G", "GGG":"G",}
