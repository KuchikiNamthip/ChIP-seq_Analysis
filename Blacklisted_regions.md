# BLACKLISTED-REGIONS

Blacklisted regions represent artifact regions that tend to show artificially high signal (excessive unstructured anomalous reads mapping). These regions are often found at specific types of repeats such as centromeres, telomeres and satellite repeats and typically appear uniquely mappable so simple mappability filters applied above do not remove them. 

The ENCODE and modENCODE consortia have compiled blacklists for various species and genome versions including human, mouse, worm and fly. These blacklisted regions (coordinate files) can be filtered out from our alignment files before proceeding to peak calling.
## Main publication about blacklisted-region 
Amemiya, H.M., Kundaje, A. & Boyle, A.P. The ENCODE Blacklist: Identification of Problematic Regions of the Genome. Sci Rep 9, 9354 (2019). https://doi.org/10.1038/s41598-019-45839-z

## Download blacklisted-region `.bed` file
[ENCODE version 3](https://www.encodeproject.org/files/ENCFF356LFX/) are combined version of previous versions with adding new regions as stated in [the README file of version 3](https://www.encodeproject.org/documents/cbaffa9e-2e42-434e-8b88-f04619c57080/@@download/attachment/README.txt).

```bash
wget -L https://www.encodeproject.org/files/ENCFF356LFX/@@download/ENCFF356LFX.bed.gz && \
    gunzip ENCFF356LFX.bed.gz && \
    mv ENCFF356LFX.bed hg38-blacklist.v3.bed`
```
## NOTE
> [Pipelines and QC: When and how do you remove blacklisted regions? What program do you use?](https://bioinformatics.ccr.cancer.gov/btep/questions/pipelines-and-qc-when-and-how-do-you-remove-blacklisted-regions-what-program-do-you-use)
> --------------------
> There is no single tool to remove blacklisted regions. Genomic coordinates of reference-specific blacklisted regions are used from reliable resources to extract these blacklisted sequences from the genome. A BWA alignment index is created for these blacklisted region sequences and reads are aligned to this index using BWA. Any reads which do align are assumed to be originating from the blacklisted regions and excluded from downstream analysis. The last couple steps are run using SAMTOOLS and BEDTOOLS. - answered by Tovah Markowitz, Paul Schaughency, Vishal Koparde. 