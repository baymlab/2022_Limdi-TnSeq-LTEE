# 2022_Limdi-TnSeq-LTEE

## About

Code corresponding to the following paper:

Parallel changes in gene essentiality over 50,000 generations of evolution
Anurag Limdi, Sian V. Owen, Cristina Herren, Richard E. Lenski and Michael Baym
(add link to biorxiv here)

In this project, we performed transposon sequencing of the ancestors and evolved clones after 50,000 generations of evolution to identify how the distribution of fitness effects and gene essentiality changes over evolution. 

## Organization

This repository is organized as follows:

### Data

This folder is empty: please download the data from https://doi.org/10.5281/zenodo.6547536. This data is generated using the scripts in Part 1: Data to Trajectories, and is required for final figure generation and analysis. 

The data was uploaded to Zenodo as a single file ltee-tnseq-processed-data.zip. Please unzip this file, and move the Mutant_Trajectories and WGS_Data directories here. 

### Metadata

This folder contains the relevant metadata for analysis, including gene names, locations, reference genomes, etc. 
It also contains the RNAseq and RiboSeq data from Favate et al that we use in the following section.

### Analysis

This section contains all the scripts required to go from the .fastq sequencing data to generating the final figures and analysis for the paper. It is further sub-divided into three parts:

- Part 1: Data to Trajectories. Here, I process the raw sequencing reads, map them to the reference genome, and compile a final table containing the number of reads mapping to each insertion at every timepoint in the fitness assay
- Part 2: Whole Genome Sequencing Analysis. I analyse the raw WGS data using breseq and samtools, and identify large duplications and deletions
- Part 3: TnSeq Analysis. I calculate fitness effects of insertion mutations and infer gene essentiality from mutant trajectories, and do additional exploratory analysis looking the interplay of gene essentiality with gene expression levels, and presence/absence of homologs. In this section, I also create the final figures and analyses that go into the manuscript.

Other directories:

- Plots_for_Paper: contains all the figure panels that I assemble and annotate to the get the final figures in Illustrator
- Supplementary Tables: contain supporting information for the analyses done in the paper
