# Intergenic Transcription Manuscript

Repository of the code to reproduce analysis and figures for ["Intergenic RNA mainly derives from nascent transcripts of known genes". bioRxiv, 2020](https://www.biorxiv.org/content/10.1101/2020.01.08.898478v1).

## Requirements

- stringtie
- igvtools
- gffcompare
- R

**R packages requirements:**

- GenomicFeatures
- rtracklayer
- data.table
- ggplot2
- ggpubr
- cowplot
- ggthemes
- ggsci
- ggforce
- ggExtra
- ggrepel
- scales
- DT
- circlize
- BSgenome.Hsapiens.UCSC.hg38
- ggbio
- phastCons100way.UCSC.hg38
- GenomicAlignments
- genomation
- VennDiagram
- viridis

## Preliminary steps

### RNA-seq (and NET-seq) datasets

Pre-processing, alignment to the human reference genome and generation of the individual transcriptome assemblies for each dataset have been performed with the [RNA-seq-pipeline](https://github.com/luslab/RNA-seq-pipeline); the Supplementary Table 1 contains all the accession codes of the datasets used for annotation and validation.

_The output files obtained with this procedure should be placed in the following folders:_
- _stringtie: GTF files produced by stringtie;_
- _counts: QoRTs folders (containing the QC.geneCounts.detailed.txt.gz and QC.summary.txt files) and StrandCheck.out.tab files;_
- _RNAseq_bw: stranded (plus and minus) CPM normalised bigWig files;_
- _RNAseq_bam: BAM files (post-deduplication)._

### Reference annotation

Parsing of the Gencode v27 reference annotaion and generation of the R objects used in this analysis have been performed with the [R_Gencode_Reference](https://github.com/fagostini/R_Gencode_Reference) processing scripts.

_The R objects obtained with this procedure should be placed in the GencodeReference folder (default); otherwise, change the annotationFolder path using their location on the current machine._

## Running the analysis

The main code is in R markdown format (Rmd), which can be opened and executed via R studio or other compatible editors, and it is subdivided into multiple 'chunks', thus providing the ability to execute the different tasks step-by-step. 

## Final annotation files (BED format)

### All identified TUs

1. [Gencode v27 + Intergenic TUs (all)](Gencode27_and_Intergenic_TUs_all.bed)
    - UCSC Genome Browser Track (<a href="GenomeBrowser/Gencode27_and_Intergenic_TUs_all.bed" download>Bed</a> or <a href="GenomeBrowser/Gencode27_and_Intergenic_TUs_all.bb" download>BigBed</a>) <!-- [open in Genome Browser](http://genome.ucsc.edu/cgi-bin/hgTracks?db=hg38&position=chr4:173369000-173480000&hgct_customText=track%20type=bigBed%20name=%22Gencode27%20and%20Intergenic%20TUs%20(all)%22%20description=%22Gencode%20version%2027%20and%20Intergenic%20TUs%20(all)%22%20visibility=full%20itemRgb=%22On%22bigDataUrl=https://github.com/fagostini/IntergenicTranscriptionManuscript/blob/master/GenomeBrowser/Gencode27_and_Intergenic_TUs_all.bb) -->

### TUs expressed in HeLa cells

2. [Gencode v27 + Intergenic TUs (HeLa)](Gencode27_and_Intergenic_TUs_HeLa.bed) 
   - UCSC Genome Browser Track (<a href="GenomeBrowser/Gencode27_and_Intergenic_TUs_HeLa.bed" download>Bed</a> or <a href="GenomeBrowser/Gencode27_and_Intergenic_TUs_HeLa.bb" download>BigBed</a>) <!--[open in Genome Browser](http://genome.ucsc.edu/cgi-bin/hgTracks?db=hg38&position=chr1:1058728-1071581&hgct_customText=track%20type=bigBed%20name=%22Gencode27%20and%20Intergenic%20TUs%20(all)%22%20description=%22Gencode%20version%2027%20and%20Intergenic%20TUs%20(all)%22%20visibility=full%20itemRgb=%22On%22bigDataUrl=https://github.com/fagostini/IntergenicTranscriptionManuscript/blob/master/GenomeBrowser/Gencode27_and_Intergenic_TUs_HeLa.bb) -->

### TUs selected for metaprofile analysis

3. [Metaprofiles Proximal TUs](Metaprofile_Proximal_TUs_selected.bed)
   - UCSC Genome Browser Track (<a href="GenomeBrowser/Metaprofile_Proximal_TUs_selected.bed" download>Bed</a> or <a href="GenomeBrowser/Metaprofile_Proximal_TUs_selected.bb" download>BigBed</a>) <!--[open in Genome Browser](http://genome.ucsc.edu/cgi-bin/hgTracks?db=hg38&position=chr19:46855000-47010000&hgct_customText=track%20type=bigBed%20name=%22Gencode27%20and%20Intergenic%20TUs%20(all)%22%20description=%22Gencode%20version%2027%20and%20Intergenic%20TUs%20(all)%22%20visibility=full%20itemRgb=%22On%22bigDataUrl=https://github.com/fagostini/IntergenicTranscriptionManuscript/blob/master/GenomeBrowser/Metaprofile_Proximal_TUs_selected.bb) -->
  
4. [Metaprofiles Linker TUs](Metaprofile_Linker_TUs_selected.bed) 
    - UCSC Genome Browser Track (<a href="GenomeBrowser/Metaprofile_Linker_TUs_selected.bed" download>Bed</a> or <a href="GenomeBrowser/Metaprofile_Linker_TUs_selected.bb" download>BigBed</a>) <!--[open in Genome Browser](http://genome.ucsc.edu/cgi-bin/hgTracks?db=hg38&position=chr12:20346000-20778000&hgct_customText=track%20type=bigBed%20name=%22Gencode27%20and%20Intergenic%20TUs%20(all)%22%20description=%22Gencode%20version%2027%20and%20Intergenic%20TUs%20(all)%22%20visibility=full%20itemRgb=%22On%22bigDataUrl=https://github.com/fagostini/IntergenicTranscriptionManuscript/blob/master/GenomeBrowser/Metaprofile_Linker_TUs_selected.bb) -->

5. [Metaprofiles Independent TUs](Metaprofile_Independent_TUs_selected.bed) 
    - UCSC Genome Browser Track (<a href="GenomeBrowser/Metaprofile_Independent_TUs_selected.bed" download>Bed</a> or <a href="GenomeBrowser/Metaprofile_Independent_TUs_selected.bb" download>BigBed</a>) <!--[open in Genome Browser](http://genome.ucsc.edu/cgi-bin/hgTracks?db=hg38&position=chr7:13977809-14080021&hgct_customText=track%20type=bigBed%20name=%22Gencode27%20and%20Intergenic%20TUs%20(all)%22%20description=%22Gencode%20version%2027%20and%20Intergenic%20TUs%20(all)%22%20visibility=full%20itemRgb=%22On%22bigDataUrl=https://github.com/fagostini/IntergenicTranscriptionManuscript/blob/master/GenomeBrowser/Metaprofile_Independent_TUs_selected.bb) -->
