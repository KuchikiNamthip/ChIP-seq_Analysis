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

## Software
1. [SAMtools](https://www.htslib.org/doc/samtools-view.html)

### References
- [nf-core/chipseq version 2.1.0](https://nf-co.re/chipseq/2.1.0) 


2. reads that are marked as duplicates (SAMtools)
3. reads that are not marked as primary alignments (SAMtools)
4. reads that are unmapped (SAMtools)
5. reads that map to multiple locations (SAMtools)

6. reads containing > 4 mismatches (BAMTools)
7. reads that have an insert size > 2kb (BAMTools; paired-end only)

1. reads mapping to blacklisted regions (BEDTools)

8. reads that map to different chromosomes (Pysam; paired-end only)
9. reads that arent in FR orientation (Pysam; paired-end only)
10. reads where only one read of the pair fails the above criteria (Pysam; paired-end only)