# PrecisionProDB_reference
protein databases based on gnomAD 3.1([the Genome Aggregation Database (gnomAD) project](https://gnomad.broadinstitute.org/)) and [PrecisionProDB](https://github.com/ATPs/PrecisionProDB) for humans

[PrecisionProDB](https://github.com/ATPs/PrecisionProDB) is a Python package for proteogenomics, which can generate a customized protein database for peptide search in mass spectrometry. 


- [PrecisionProDB_reference](#precisionprodb_reference)
- [gnomAD3.1](#gnomad31)
  - [summary of population common alleles based on gnomAD 3.1](#summary-of-population-common-alleles-based-on-gnomad-31)
  - [Common alleles in different population](#common-alleles-in-different-population)
- [GENCODE](#gencode)
  - [GENCODE_gnomAD_common.protein_all.fa.gz](#gencode_gnomad_commonprotein_allfagz)
  - [GENCODE_*POPULATION_ABREVIATION*.pergeno.aa_mutations.csv.gz](#gencode_population_abreviationpergenoaa_mutationscsvgz)
  - [GENCODE_gnomAD_all.protein_changed.fa.gz](#gencode_gnomad_allprotein_changedfagz)
- [RefSeq](#refseq)
  - [RefSeq_gnomAD_common.protein_all.fa.gz](#refseq_gnomad_commonprotein_allfagz)
  - [RefSeq_*POPULATION_ABREVIATION*.pergeno.aa_mutations.csv.gz](#refseq_population_abreviationpergenoaa_mutationscsvgz)
  - [RefSeq_gnomAD_all.protein_changed.fa.gz](#refseq_gnomad_allprotein_changedfagz)
- [Ensembl](#ensembl)
  - [Ensembl_gnomAD_common.protein_all.fa.gz](#ensembl_gnomad_commonprotein_allfagz)
  - [Ensembl_*POPULATION_ABREVIATION*.pergeno.aa_mutations.csv.gz](#ensembl_population_abreviationpergenoaa_mutationscsvgz)
  - [Ensembl_gnomAD_all.protein_changed.fa.gz](#ensembl_gnomad_allprotein_changedfagz)
- [UniProt](#uniprot)
  - [UniProt_gnomAD_common.protein_all.fa.gz](#uniprot_gnomad_commonprotein_allfagz)
  - [UniProt_gnomAD_all.protein_changed.fa.gz](#uniprot_gnomad_allprotein_changedfagz)

# gnomAD3.1

## summary of population common alleles based on gnomAD 3.1

Several population go
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


\# `alt` > `ref`: count of alleles that the alternative allele have a higher allele frequency (AF) greater than alleles in the reference genome.

## Common alleles in different population
Variants from gnomAD 3.1. Only include sites which is "PASS" in quality-control and allele frequency (AF) of `alt` is greater than `ref`.

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

# Ensembl
Ensembl Homo_sapiens.GRCh38.101

## Ensembl_gnomAD_common.protein_all.fa.gz
Ensembl gene models with alleles from gnomAD 3.1 most common alleles from all indiviudals ([adj](#gnomad31)).

## Ensembl_*POPULATION_ABREVIATION*.pergeno.aa_mutations.csv.gz
Amino acid change mutations for different populations.

## Ensembl_gnomAD_all.protein_changed.fa.gz
Combine changed proteins from 10 populations and keep only unique ones. 


# UniProt
UniProt reference proteins for proteome, human (12/02/2020).

ftp://ftp.uniprot.org/pub/databases/uniprot/current_release/knowledgebase/reference_proteomes/Eukaryota/UP000005640_9606.fasta.gz
ftp://ftp.uniprot.org/pub/databases/uniprot/current_release/knowledgebase/reference_proteomes/Eukaryota/UP000005640_9606_additional.fasta.gz


## UniProt_gnomAD_common.protein_all.fa.gz
UniProt gene models with alleles from gnomAD 3.1 most common alleles from all indiviudals ([adj](#gnomad31)).

## UniProt_gnomAD_all.protein_changed.fa.gz
Combine changed proteins from 10 populations and keep only unique ones. 
