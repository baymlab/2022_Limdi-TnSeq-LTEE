# 2022_Limdi-TnSeq-LTEE

## About

Code corresponding to the following paper:

Parallel changes in gene essentiality over 50,000 generations of evolution

Anurag Limdi, Sian V. Owen, Cristina Herren, Richard E. Lenski and Michael Baym
(add link to biorxiv here)

In this project, we performed transposon sequencing of the ancestors and evolved clones after 50,000 generations of evolution to identify how the distribution of fitness effects and gene essentiality changes over evolution. 

### Linked Datasets

- Raw sequencing reads have been deposited in the NCBI BioProject database under accession number PRJNA814281. 
- Processed data are deposited on Zenodo (https://doi.org/10.5281/zenodo.6547536)

## Organization

This repository is organized as follows:

### Data

This folder is empty: please download the data from https://doi.org/10.5281/zenodo.6547536. This processed data is generated using the scripts in Part 1: Data to Trajectories, and is required for final figure generation and analysis. 

The data is contained in a single file _ltee-tnseq-processed-data.zip_. Please unzip this file, and move the Mutant_Trajectories and WGS_Data directories here. 

### Metadata

This folder contains the relevant metadata for analysis, including gene names, locations, reference genomes, etc. 

It contains the following datasets from previously published papers:
- RNAseq an Riboseq for LTEE ancestors and evolved clones at 50,000 generations: from Favate et al. https://www.biorxiv.org/content/10.1101/2021.01.12.426406v1
- TraDIS gene essentiality data: from Goodall et al. https://doi.org/10.1128/mBio.02096-17

### Analysis

This section contains all the scripts required to go from the .fastq sequencing data to generating the final figures and analysis for the paper. It is further sub-divided into three parts:

- Part 1: Data to Trajectories. Here, I process the raw sequencing reads, map them to the reference genome, and compile a final table containing the number of reads mapping to each insertion at every timepoint in the fitness assay. 
- Part 2: Whole Genome Sequencing Analysis. I analyse the raw WGS data using breseq and samtools, and identify large duplications and deletions
- Part 3: TnSeq Analysis. I calculate fitness effects of insertion mutations and infer gene essentiality from mutant trajectories, and do additional exploratory analysis looking the interplay of gene essentiality with gene expression levels, and presence/absence of homologs. In this section, I also create the final figures and analyses that go into the manuscript.

Other directories:

- Plots_for_Paper: Contains all the figure panels that I assemble and annotate to the get the final figures in Illustrator
- Supplementary Tables: Contains supporting information for the analyses done in the paper
