# ChIP-seq_Analysis
my personal note for ChIP-seq analysis

## Main Chip-seq analysis guideline
- [ChIP-seq guidelines and practices of the ENCODE and modENCODE consortia](https://genome.cshlp.org/content/22/9/1813.full.html)
## Analysis setting for nf-core
- [Effective Genome Size](https://deeptools.readthedocs.io/en/develop/content/feature/effectiveGenomeSize.html#effective-genome-size) parameter required by MACS3 as `--macs_gsize`. Therefore, for read length 50 and ref genome GRCh38, `--macs_gsize = 2701495711`. Please note that the pre-defined read lenght will be used for iGenomes reference.
