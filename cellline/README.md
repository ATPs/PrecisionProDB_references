# Cellline VCF file

## Jurkat.vcf.gz

For Jurkat cell line, RNA-seq data were downloaded from NCBI under BioProject PRJNA193719. Variant calling was performed with the best practice pipeline for RNA-seq germline short variant (https://github.com/gatk-workflows/gatk4-rnaseq-germline-snps-indels) with GATK4 (version 4.1.8.1). Briefly, with STAR (version 2.7.5c), the human GRCh38.p13_release34 genome was indexed with splice junctions from GENCODE release 34 gene annotation supplied to improve the accuracy of mapping, and all RNA-seq reads were mapped. The alignment file in BAM format were preprocessed sequentially with several components of GATK4: MarkDuplicates, SplitNCigarReads, BaseRecalibrator, and ApplyBQSR. Picard BedToIntervalList were used to split the genome to short intervals. Variants were called separately with HaplotypeCaller in each genomic interval using the processed BAM file and merged with MergeVcfs. The file was filtered using VariantFiltration with the suggested settings to generate the final VCF file and only sites with a “PASS” flag were selected for downstream analysis.

# Jurkat vcf file from other resource
Gioia, Louis. (2017). Genomic variant data for the Jurkat cell line [Data set]. Zenodo. https://doi.org/10.5281/zenodo.400615

https://zenodo.org/record/400615#.YWjoIGJBxBC


# Jurkat.CHM13.RefSeq.vcf.gz
liftover by commandline like `CrossMap vcf hg38ToHs1.over.chain.gz Jurkat.vcf.gz chm13v2.0.fa Jurkat.CHM13.RefSeq.vcf`. 

log 
```
2024-11-13 12:49:05 [INFO]  Read the chain file "hg38ToHs1.over.chain.gz"
2024-11-13 12:49:10 [INFO]  Filter out variants [reference_allele == alternative_allele] ...
2024-11-13 12:49:10 [INFO]  Updating contig field ...
2024-11-13 12:49:10 [INFO]  Lifting over ...
2024-11-13 12:49:12 [INFO]  Total entries: 108910
2024-11-13 12:49:12 [INFO]  Failed to map: 28255
```
26,847 of the 28,255 failed sites were due to `Fail(REF==ALT)`, which means that the site were not a mutation based on the new reference genome.
