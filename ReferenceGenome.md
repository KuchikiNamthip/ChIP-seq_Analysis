# REFERENCE GENOME FOR ChIP-seq

For ChIP-seq analysis, the most commonly used hg38 reference genome is the primary assembly version from UCSC (University of California, Santa Cruz). Many researchers prefer this version because:

    1. The UCSC hg38/GRCh38 reference genome is widely supported across various bioinformatics tools and pipelines specifically designed for ChIP-seq analysis.
    2. It uses the more familiar "chr1", "chr2", etc. chromosome naming convention (compared to Ensembl's numeric naming), which is preferred by many ChIP-seq analysis tools.
    3. Many public ChIP-seq datasets, including those from ENCODE and other large consortia, were processed using the UCSC reference genome, making it easier to compare your results with published data.
    4. The UCSC Genome Browser, which is frequently used for visualizing ChIP-seq peaks, is built around this reference.

The specific file is typically named hg38.fa or hg38.fasta and can be downloaded from the UCSC Genome Browser Downloads page.
That said, both the UCSC and Ensembl primary assemblies contain essentially the same sequence information - they just differ in how chromosomes are named and some minor details. The Ensembl version you mentioned (Homo_sapiens.GRCh38.dna_sm.primary_assembly.fa.gz) is also perfectly suitable for ChIP-seq analysis.


# ANNOTATION
For ChIP-seq analysis, there isn't as strong a dependency on gene annotations as there is with RNA-seq, since the primary focus is on identifying protein-binding sites across the genome rather than quantifying transcript expression. However, annotations are still important for downstream analysis to associate peaks with genomic features.
The most commonly used annotations for ChIP-seq analysis are:

    1. UCSC Annotations
        - Often preferred for ChIP-seq because many ChIP-seq visualization and analysis tools were developed with UCSC annotations in mind
        - Available as refGene or knownGene tables

    2. GENCODE/Ensembl Annotations
        - gencode.v44.annotation.gtf.gz (or latest version)
        - More comprehensive and include non-coding RNAs
        - Increasingly popular for integrated analyses

    3. RefSeq Annotations
        - More conservative but highly reliable
        - Often used when focusing on well-established protein-coding genes

Many ChIP-seq analysis pipelines and tools like HOMER, ChIPseeker, and GREAT can work with any of these annotation formats, though some might require conversion between formats.
For associating peaks with promoters, enhancers, and other regulatory elements, researchers often supplement these basic gene annotations with:

    - Chromatin state annotations (from projects like Roadmap Epigenomics)
    - DNase hypersensitivity sites
    - Transcription factor binding site databases
    - Custom regulatory element annotations

The choice often depends on the specific biological question and which downstream analysis tools you plan to use.

## Detail about UCSC annotation (RefGene vs KnownGene)
The key differences between `refGene.txt.gz` and `knownGene.txt.gz` are:

**refGene.txt.gz (RefSeq gene annotations)**:
- Contains annotations from NCBI's RefSeq database
- More conservative and highly curated gene set
- Focuses on well-supported transcripts with experimental validation
- Typically has fewer alternative transcripts per gene
- Generally considered more reliable but less comprehensive
- Better for applications where accuracy is more important than coverage

**knownGene.txt.gz (UCSC known genes)**:
- UCSC's own gene prediction set that integrates multiple sources
- More comprehensive, includes more novel and predicted transcripts
- Contains more alternative splice variants
- Includes genes from RefSeq plus additional sources (like GenBank)
- Better for applications where you want broad coverage
- May include more hypothetical genes or transcripts

For ChIP-seq analysis:
- `refGene.txt.gz` is often preferred when you want to focus on well-established genes with high confidence
- `knownGene.txt.gz` might be better when you want to capture more potential regulatory regions or are interested in more comprehensive coverage

Most ChIP-seq analysis tools can work with either annotation set. The choice often depends on your specific research question and how conservative you want to be with gene annotations.

# OTHER REFERENCE FILEs
For ChIP-seq analysis, you may also want to download:

    - wgEncodeRegDnaseClusteredV3.bed.gz - DNase hypersensitive sites
    - cpgIslandExt.txt.gz - CpG islands
    - rmsk.txt.gz - Repeat elements

These annotations can be used with tools like HOMER, BEDTools, or ChIPseeker to annotate your peaks after peak calling.
============================================================================

# NOTE

## Different between full GRCh38 and Primary Assembly

    1. Primary Assembly (Homo_sapiens.GRCh38.dna_sm.primary_assembly.fa.gz):
        - Contains the main chromosomal sequences (chr1-22, X, Y, MT)
        - Includes the primary chromosome sequences only without alternative contigs
        - Represents the "standard" human genome reference
        - Smaller file size and more manageable for many analyses
        - Recommended for most standard analyses including ChIP-seq, RNA-seq

    2. Full hg38/GRCh38 Assembly:
        - Contains the primary assembly PLUS:
            - Alternative haplotypes (alt contigs)
            - Unplaced sequences
            - Unlocalized sequences
            - Patches (fix and novel)
        - Much larger file size
        - Can complicate alignments as reads might map to multiple similar regions
        - Can be useful for specialized analyses focusing on regions with multiple representations

## Note reference genome selection
    - ["Which human reference genome to use?" by HengLi](https://lh3.github.io/2017/11/13/which-human-reference-genome-to-use)
    - from ENCODE pipeline: `https://www.encodeproject.org/files/GRCh38_no_alt_analysis_set_GCA_000001405.15/@@download/GRCh38_no_alt_analysis_set_GCA_000001405.15.fasta.gz`
    - [Different between each source of reference genome by Translational Genomics Research Institute](https://github.com/tgen/jetstream_resources/blob/main/genome_reference_notes.md)