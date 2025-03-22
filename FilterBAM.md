# WHAT WE SHOULD FILTER OUT FROM .BAM file
1. reads mapping to blacklisted regions (SAMtools, BEDTools)
2. reads that are marked as duplicates (SAMtools)
3. reads that are not marked as primary alignments (SAMtools)
4. reads that are unmapped (SAMtools)
5. reads that map to multiple locations (SAMtools)
6. reads containing > 4 mismatches (BAMTools)
7. reads that have an insert size > 2kb (BAMTools; paired-end only)
8. reads that map to different chromosomes (Pysam; paired-end only)
9. reads that arent in FR orientation (Pysam; paired-end only)
10. reads where only one read of the pair fails the above criteria (Pysam; paired-end only)

# Software document
1. [SAMtools](https://www.htslib.org/doc/samtools-view.html)
2. [BAMtools](https://raw.githubusercontent.com/wiki/pezmaster31/bamtools/Tutorial_Toolkit_BamTools-1.0.pdf)
3. [BEDtools](https://bedtools.readthedocs.io/en/stable/content/tools/intersect.html)

# References
- [nf-core/chipseq version 2.1.0](https://nf-co.re/chipseq/2.1.0) 
- [ENCODE4 Histone ChIP-seq Data Standards and Processing Pipeline](https://github.com/ENCODE-DCC/chip-seq-pipeline2/blob/master/scripts/download_genome_data.sh)

# nf-core/chipseq ver 2.1.0

    ### Step 1 by `SAMtools`
        2. reads that are marked as duplicates (SAMtools)
        3. reads that are not marked as primary alignments (SAMtools)
        4. reads that are unmapped (SAMtools)
        5. reads that map to multiple locations (SAMtools)
   
            -F 0x004 # Filtering Unmapped Reads\
            -F 0x0400 # Filtering Secondary Alignments (Duplicate)\
            -q 1 # Filtering Low Mapping Quality\
            -@ 20 # threads 

    ### Step 2 by `BAMtools`
        6. reads containing > 4 mismatches (BAMTools)
        7. reads that have an insert size > 2kb (BAMTools; paired-end only)

    ### Step 3 by `BEDtools`
        8. reads mapping to blacklisted regions (BEDTools)

    ### Step 4 by `Pysam`
        9.  reads that map to different chromosomes (Pysam; paired-end only)
        10. reads that arent in FR orientation (Pysam; paired-end only)
        11. reads where only one read of the pair fails the above criteria (Pysam; paired-end only)

# ENCODE4 Paired-End ChIP-seq parameters version(ENCODE-DCC chip-seq-pipeline2 version 2.2.2)
    - Remove reads unmapped, mate unmapped, not primary alignment, reads failing platform, duplicates (-F 1804).
    - Retain properly paired reads -f 2
    - Remove multi-mapped reads (i.e. those with MAPQ < 30, using -q in SAMtools)
    - Remove PCR duplicates (using Picard’s MarkDuplicates or FixSeq)

# NAMTHIP adapt for single end
    ## Overview
      - Remove reads unmapped, mate unmapped, not primary alignment, reads failing platform, duplicates (-F 1804).
      - Retain properly paired reads -f 2
      - Remove multi-mapped reads (i.e. those with MAPQ < 30, using -q 30 in SAMtools)
      - Remove PCR duplicates (using Picard’s MarkDuplicates)
      - reads mapping to blacklisted regions (BEDTools)
      - remove reads map to blacklisted-regions
    ## Steps
        1. Create `~/ref_genome/Black-Listed_Region/v3.0/hg38_genome.include_regions.nochr.bed` (This was created ) 

# Note for meaning of each filtering 
    1. Mate Mapping
        Mate mapping refers to the process of aligning paired-end reads to a reference genome, ensuring that both ends of the pair are correctly oriented and positioned relative to each other. This is crucial for various sequencing applications, including mate-pair sequencing, which involves sequencing the ends of long DNA fragments to gather long-range genomic information

    2. Reads Failing Platform
        The term "reads failing platform" is not a standard term in sequencing or bioinformatics. However, it might refer to issues where sequencing reads fail to meet certain quality or mapping criteria, such as:
           - Quality Checks: Reads may fail quality checks due to low base quality scores, adapter contamination, or other issues.
           - Mapping Failures: Reads might not map correctly to the reference genome, which can happen due to sequencing errors, repetitive regions, or poor library preparation.
