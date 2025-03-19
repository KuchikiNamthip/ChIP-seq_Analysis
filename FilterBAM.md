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

## Software document
1. [SAMtools](https://www.htslib.org/doc/samtools-view.html)
2. [BAMtools](https://raw.githubusercontent.com/wiki/pezmaster31/bamtools/Tutorial_Toolkit_BamTools-1.0.pdf)
3. [BEDtools](https://bedtools.readthedocs.io/en/stable/content/tools/intersect.html)

### References
- [nf-core/chipseq version 2.1.0](https://nf-co.re/chipseq/2.1.0) 

## Filtering steps
    ### Step 1 by `SAMtools`
        2. reads that are marked as duplicates (SAMtools)
        3. reads that are not marked as primary alignments (SAMtools)
        4. reads that are unmapped (SAMtools)
        5. reads that map to multiple locations (SAMtools)

    ### Step 2 by `BAMtools`
        6. reads containing > 4 mismatches (BAMTools)
        7. reads that have an insert size > 2kb (BAMTools; paired-end only)

    ### Step 3 by `BEDtools`
        1. reads mapping to blacklisted regions (BEDTools)

    ### Step 4 by `Pysam`
        8. reads that map to different chromosomes (Pysam; paired-end only)
        9. reads that arent in FR orientation (Pysam; paired-end only)
        10. reads where only one read of the pair fails the above criteria (Pysam; paired-end only)