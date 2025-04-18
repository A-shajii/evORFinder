Data Acquisition
The following datasets were used in this study to train and benchmark the evORFinder model:

1. Curated Bacterial Genome Dataset from Human Microbiome
This dataset consists of short genomic sequences annotated as coding (smORFs) or non-coding. These sequences come from a variety of bacterial genomes found in the human microbiome. The dataset was augmented with 100 base pairs of upstream and downstream flanking regions for sequence context.

Citation: Sberro, H., Fremin, B. J., Zlitni, S., Edfors, F., Greenfield, N., Snyder, M. P., ... & Bhatt, A. S. (2019). Large-scale analyses of human microbiomes reveal thousands of small, novel genes. Cell, 178(5), 1245-1259. DOI: 10.1016/j.cell.2019.07.019


2. Mycobacterium tuberculosis (Mtb) H37Rv smORF Dataset
This dataset contains bona-fide smORFs derived from the Mtb H37Rv genome. The data was curated from NCBI genome annotations and Ribo-seq data, with a focus on sequences less than 50 codons in length.

Citation: National Center for Biotechnology Information (NCBI). (n.d.). nuccore: 448814763. Retrieved April 9, 2025, from https://www.ncbi.nlm.nih.gov/nuccore/448814763

You can download the Mtb genome sequence directly from NCBI:

Mtb H37Rv Genome Data (NCBI): https://www.ncbi.nlm.nih.gov/nuccore/448814763

3. Ribo-seq Data
The ribosome profiling (Ribo-seq) data was used to validate the active translation of small open reading frames (smORFs). This dataset provides insights into the sequences that are being actively translated within the organism, offering valuable biological evidence for the bona-fide smORFs identified by evORFinder.

https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE129355
