# IDR

## Software
    - [software](https://github.com/kundajelab/idr)

## References mentioned IDR
    1. Practical Guidelines for the Comprehensive Analysis of ChIP-seq Data(2013)
    2. 10.1101/gr.136184.111 ChIP-seq guidelines and practices of the ENCODE and modENCODE consortia (2012)

## Discussions

- From [Rory Stark](https://support.bioconductor.org/p/89517/#89576)
> The ENCODE standards, including IDR, were developed as part of an effort to identify the locations where binding sites and epigenetic marks are. The focus of this type of "mapping" exercise is on identifying the location of binding sites with high confidence. 

> The goals of a differential analysis are different. We are trying to identify genomic intervals where we have confidence that binding levels have changed. A definitive "map" of high-confidence binding sites is not required to accomplish this. The techniques used in DiffBind should be robust to the inclusion of low-confidence binding sites and noise, so long as there are sufficient replicates to properly power the analysis. Only sites that consistently differ in read density across all the replicates in the sample groups should be identified as being differentially bound with high confidence (low FDR). So choosing a "lenient" consensus set, and not worrying too much about getting a perfect set, is fine.

> Secondly, regarding merging of peaks that overlap in multiple samples. We do this so that the consensus peaks are unique in the bases they cover, so we can uniquely assign reads when counting. There are some downsides to this. One is that the peak intervals tend to get wider the more samples there are, and wider peaks can include more background which can compromise the analysis. For "punctate" peaks such as transcription factor binding, we recommend re-centering the peaks using the summits parameter in dba.count(). This will identify a consensus "summit" (point of highest coverage) and replace the peak interval with a new one of consistent width centered on the summit. For example, if you specify summits=200, the peak intervals will all be 400bp (200bp upstream and downstream of the summit). 

> Another disadvantage of merging (and recentering) is that the consensus peaks can be difficult to relate back to the originally called peaks. The idea is that DiffBind helps identify regions on the genome where we have high confidence that the binding changed; there can then be more detailed analysis of what is going on in these regions (which may involve a complex pattern of enrichment).