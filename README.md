# PrecisionProDB_reference

[PrecisionProDB](https://github.com/ATPs/PrecisionProDB) is a Python package for proteogenomics, which can generate a customized protein database for peptide search in mass spectrometry.

[The Genome Aggregation Database (gnomAD) project](https://gnomad.broadinstitute.org/) provides variant allele frequencies in different human opulations based on genomes and exomes of hundreds of thousands of individuals. The population-specific common allele information can be integrated into a protein database. We applied PrecisionProDB to alleles from different populations from the gnomAD (v3.1) data and provided the pre-calculated protein databases here. 

## updates
- 20241213 [Jurkat cell line variant file based on T2T CHM13](https://github.com/ATPs/PrecisionProDB_references/blob/main/cellline/Jurkat.CHM13.RefSeq.vcf.gz) was added!

## Table of contents
- [PrecisionProDB_reference](#precisionprodb_reference)
- [gnomAD3.1](#gnomad31)
  - [Summary of population common alleles based on gnomAD 3.1](#summary-of-population-common-alleles-based-on-gnomad-31)
  - [Common alleles in different populations](#common-alleles-in-different-populations)
- [GENCODE](#gencode)
  - [GENCODE_gnomAD_common.protein_all.fa.gz](#gencode_gnomad_commonprotein_allfagz)
  - [GENCODE_*POPULATION_ABREVIATION*.pergeno.aa_mutations.csv.gz](#gencode_population_abreviationpergenoaa_mutationscsvgz)
  - [GENCODE_gnomAD_all.protein_changed.fa.gz](#gencode_gnomad_allprotein_changedfagz)
  - [Summary of GENCODE variation](#summary-of-gencode-variation)
- [RefSeq](#refseq)
  - [RefSeq_gnomAD_common.protein_all.fa.gz](#refseq_gnomad_commonprotein_allfagz)
  - [RefSeq_*POPULATION_ABREVIATION*.pergeno.aa_mutations.csv.gz](#refseq_population_abreviationpergenoaa_mutationscsvgz)
  - [RefSeq_gnomAD_all.protein_changed.fa.gz](#refseq_gnomad_allprotein_changedfagz)
  - [Summary of RefSeq variation](#summary-of-refseq-variation)
- [Ensembl](#ensembl)
  - [Ensembl_gnomAD_common.protein_all.fa.gz](#ensembl_gnomad_commonprotein_allfagz)
  - [Ensembl_*POPULATION_ABREVIATION*.pergeno.aa_mutations.csv.gz](#ensembl_population_abreviationpergenoaa_mutationscsvgz)
  - [Ensembl_gnomAD_all.protein_changed.fa.gz](#ensembl_gnomad_allprotein_changedfagz)
  - [Summary of Ensembl variation](#summary-of-ensembl-variation)
- [UniProt](#uniprot)
  - [UniProt_gnomAD_common.protein_all.fa.gz](#uniprot_gnomad_commonprotein_allfagz)
  - [UniProt_gnomAD_all.protein_changed.fa.gz](#uniprot_gnomad_allprotein_changedfagz)
  - [Summary of UniProt variation](#summary-of-uniprot-variation)

# gnomAD3.1

## Summary of population common alleles based on gnomAD 3.1


| population               | abreviation | genomes | # `alt` > `ref` |
|-----------               |-------------|---------| --                 |
| African/African American | adj_afr     | 20,744  | 2,334,582          |
| Amish                    | adj_ami     | 456     | 2,435,528          |
| Latino/Admixed American  | adj_amr     |  7,647  | 2,343063          |
| Ashkenazi Jewish         | adj_asj     | 1,736   | 2,375,907          |
| East Asian               | adj_eas     | 2,604   | 2,579,504          |
| Finnish                  | adj_fin     | 5,316   | 2,364,824          |
| Middle Eastern           | adj_mid     | 158     | 2,346,917          |
| Non-Finnish European     | adj_nfe     | 34,029  | 2,369,937          |
| South Asian              | adj_sas     | 2,419   | 2,367,008          |
| Other                    | adj_oth      | 1,047   |  -          |
| **Total**                | adj         | 76,156  | 2,274,088          |

weblink: https://gnomad.broadinstitute.org/faq


\# `alt` > `ref`: count of alleles that the alternative allele have a higher allele frequency (AF) than the allele in the reference genome.

## Common alleles in different populations
Variants from gnomAD 3.1. Only include sites which is "PASS" in quality-control and the allele frequency of `alt` is higher than `ref`.

file names: POPULATION_ABREVIATION.csv.gz

files are in csv format (with `\t` as separator), which looks like:

|   chr |   pos | ref   | alt   |   alt_AF |   ref_AF |
|------:|------:|:------|:------|---------:|---------:|
|     1 | 10146 | AC    | A     |   0.6328 |   0.3672 |
|     1 | 15274 | A     | G     |   0.6311 |   0.0635 |
|     1 | 28563 | A     | G     |   0.6842 |   0.3158 |
|     1 | 49298 | T     | C     |   0.5852 |   0.4148 |
|     1 | 52238 | T     | G     |   0.9013 |   0.0987 |


# GENCODE
GENCODE Release 35 (GRCh38.p13)

https://www.gencodegenes.org/human/release_35.html

## GENCODE_gnomAD_common.protein_all.fa.gz
GENCODE gene models with alleles from gnomAD 3.1 most common alleles from all indiviudals ([adj](#gnomad31)).

## GENCODE_*POPULATION_ABREVIATION*.pergeno.aa_mutations.csv.gz
Amino acid change mutations for different populations. For explanations of the columns, visit the wiki page of [PREFIX.pergeno.aa_mutations.csv](https://github.com/ATPs/PrecisionProDB/wiki/PREFIX.pergeno.aa_mutations.csv).

## GENCODE_gnomAD_all.protein_changed.fa.gz
Combine changed proteins from 10 populations and keep only unique ones. 

This file could be added to current offical protein models to improve protein database search of mass spectrometry.

Proteins are the original names + '__' + populations. For example: `ENSP00000390334.1|ENST00000453855.5|ENSG00000101019.22|OTTHUMG00000032335.13|OTTHUMT00000078865.3|UQCC1-213|UQCC1|126__adj|nfe_adj|fin_adj|mid_adj|ami_adj|asj_adj|eas_adj|amr_adj`, where `ENSP00000390334.1|ENST00000453855.5|ENSG00000101019.22|OTTHUMG00000032335.13|OTTHUMT00000078865.3|UQCC1-213|UQCC1|126` is the original protein_id in GENCODE, `adj|nfe_adj|fin_adj|mid_adj|ami_adj|asj_adj|eas_adj|amr_adj` are the populations with this altered protein.

If the population annotation is `ALLSHARE`, it means that altered protein exists in all ten populations.

## Summary of GENCODE variation

Total number of proteins: **101486**, total number of AA: **38549462**

|         |   stopGain_Pr |   stopLoss_Pr |   frameChange_Pr |   variant_AA |   variant_Pr |   indel_pr |
|:--------|--------------:|--------------:|-----------------:|-------------:|-------------:|-----------:|
| adj     |            90 |            44 |              156 |        14768 |        10728 |        404 |
| afr_adj |            78 |            51 |              131 |        15697 |        11402 |        480 |
| ami_adj |           101 |            50 |              157 |        15441 |        10993 |        432 |
| amr_adj |            95 |            52 |              141 |        14769 |        10705 |        442 |
| asj_adj |            90 |            44 |              158 |        15181 |        10830 |        419 |
| eas_adj |            94 |            41 |              154 |        16524 |        11570 |        500 |
| fin_adj |            92 |            47 |              151 |        15291 |        10881 |        439 |
| mid_adj |           103 |            44 |              166 |        15215 |        10800 |        425 |
| nfe_adj |            94 |            48 |              154 |        15134 |        10747 |        429 |
| sas_adj |            84 |            46 |              147 |        15172 |        10917 |        419 |

- stopGain_Pr: count of proteins with stop-gain
- stopLoss_Pr: count of proteins with stop-loss
- frameChange_Pr: count of proteins with frame change
- variant_AA: total AA substitutions
- variant_Pr: count of proteins with AA substitutions
- indel_pr: count of proteins with insertion or deletion of AAs

# RefSeq
RefSeq GCF_000001405.39

ftp://ftp.ncbi.nlm.nih.gov/genomes/refseq/vertebrate_mammalian/Homo_sapiens/annotation_releases/current

Release version: 109.20200815

## RefSeq_gnomAD_common.protein_all.fa.gz
RefSeq gene models with alleles from gnomAD 3.1 most common alleles from all indiviudals ([adj](#gnomad31)).

## RefSeq_*POPULATION_ABREVIATION*.pergeno.aa_mutations.csv.gz
Amino acid change mutations for different populations.

## RefSeq_gnomAD_all.protein_changed.fa.gz
Combine changed proteins from 10 populations and keep only unique ones. 


## Summary of RefSeq variation

Total number of proteins: **114963**, total number of AA: **76187452**

|         |   stopGain_Pr |   stopLoss_Pr |   frameChange_Pr |   variant_AA |   variant_Pr |   indel_pr |
|:--------|--------------:|--------------:|-----------------:|-------------:|-------------:|-----------:|
| adj     |           104 |             0 |              174 |        28723 |        19298 |        632 |
| afr_adj |            95 |             0 |              214 |        29885 |        20389 |        773 |
| ami_adj |           134 |            15 |              224 |        29865 |        19645 |        697 |
| amr_adj |           125 |            14 |              184 |        28724 |        19241 |        722 |
| asj_adj |           117 |             0 |              176 |        29147 |        19083 |        681 |
| eas_adj |           127 |             0 |              201 |        31791 |        20630 |        805 |
| fin_adj |           113 |             0 |              186 |        29453 |        19233 |        692 |
| mid_adj |           125 |             0 |              179 |        29496 |        19332 |        692 |
| nfe_adj |           113 |             0 |              185 |        29291 |        19020 |        684 |
| sas_adj |           112 |             0 |              165 |        29040 |        19428 |        659 |


# Ensembl
Ensembl Homo_sapiens.GRCh38.101

## Ensembl_gnomAD_common.protein_all.fa.gz
Ensembl gene models with alleles from gnomAD 3.1 most common alleles from all indiviudals ([adj](#gnomad31)).

## Ensembl_*POPULATION_ABREVIATION*.pergeno.aa_mutations.csv.gz
Amino acid change mutations for different populations.

## Ensembl_gnomAD_all.protein_changed.fa.gz
Combine changed proteins from 10 populations and keep only unique ones. 


## Summary of Ensembl variation

Total number of proteins: **112012**, total number of AA: **42584212**

|         |   stopGain_Pr |   stopLoss_Pr |   frameChange_Pr |   variant_AA |   variant_Pr |   indel_pr |
|:--------|--------------:|--------------:|-----------------:|-------------:|-------------:|-----------:|
| adj     |           102 |             1 |              147 |        15136 |        10750 |        401 |
| afr_adj |            89 |             1 |              126 |        16096 |        11426 |        476 |
| ami_adj |           112 |             4 |              151 |        15844 |        11013 |        429 |
| amr_adj |           109 |             5 |              133 |        15131 |        10724 |        441 |
| asj_adj |           103 |             0 |              144 |        15664 |        10851 |        415 |
| eas_adj |           111 |             1 |              143 |        16953 |        11587 |        499 |
| fin_adj |           102 |             1 |              140 |        15706 |        10898 |        436 |
| mid_adj |           115 |             0 |              154 |        15692 |        10820 |        421 |
| nfe_adj |           107 |             0 |              144 |        15558 |        10767 |        425 |
| sas_adj |            98 |             0 |              137 |        15398 |        10940 |        417 |


# UniProt
UniProt reference proteins for proteome, human (12/02/2020).

ftp://ftp.uniprot.org/pub/databases/uniprot/current_release/knowledgebase/reference_proteomes/Eukaryota/UP000005640_9606.fasta.gz
ftp://ftp.uniprot.org/pub/databases/uniprot/current_release/knowledgebase/reference_proteomes/Eukaryota/UP000005640_9606_additional.fasta.gz


## UniProt_gnomAD_common.protein_all.fa.gz
UniProt gene models with alleles from gnomAD 3.1 most common alleles from all indiviudals ([adj](#gnomad31)).

## UniProt_gnomAD_all.protein_changed.fa.gz
Combine changed proteins from 10 populations and keep only unique ones. 

## Summary of UniProt variation
The percentage of changed proteins will be similar to Ensembl, as UniProt information were mostly extracted from Ensembl gene models.

UP000005640_9606: 20609 proteins, 11395683 AA.  
UP000005640_9606_additional: 77157 proteins, 27708325 AA.  
Total: 97766 proteins, 39104008 AA.

