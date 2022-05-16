Part 2: Breseq Whole Genome Sequencing Analysis

Breseq is a mutation calling pipeline developed by Jeff Barrick et al, specifically designed for microbial genomes. I used this to call mutations on the WGS data we collected from the clones used for transposon sequencing.

Step 1: Submit breseq jobs for each evolved population

In directory with all the wgs fastq files, make directories corresponding to the names of every clone:
- names='REL606 REL607 REL11330 REL11333 REL11364 REL11336 REL11339 REL11389 REL11392 REL11342 REL11345 REL11348 REL11367 REL11370'

Run submit_breseq_jobs.sh
- for query in $names; do array=`find path_with_wgs_fastqs -name "*$query*"`; cd $query; sbatch ../submit_breseq_job.sh reference_genome $array ; cd .. ; done

In the above command, I iterate over the clone names, find the corresponding set of WGS fastq files, change directory, submit the bash script and then go back to the original directory, and repeat until I have submitted all 14 jobs 

Step 2: Renaming output files

I renamed all the output.gd files as follows:
- for query in $names; do cd $query/output; cp output.gd "$query"_output.gd ; cd .. ; cd .. ; done 

Then I copied all the renamed files to a common directory:
- for query in $names; do cd $query/output; cp "$query"_output.gd target_directory_path; cd .. ; cd .. ; done


Step 3: Samtools for identifying coverage mapping to every site in the E. Coli REL606 reference genome for WGS data from all clones

I use the following command to run samtools on the bam files outputted by breseq, to convert to a coverage text file.
- for query in $names; do cd $query/data; pwd; samtools depth reference.bam > "$query"_depth_unique.txt; cd ..; cd ..; done

Move all the {library_name}_depth_unique.txt files to a common folder

Step 4: Identifying deletions from missing coverage data 

Run the following Jupyter Notebook: deleted_regions_from_WGSdata.ipynb
- input: .gd output files
- output: list of genes and pseudogenes that are lost in each LTEE clone under analysis.

Step 5: Identifying large duplications from normalized coverage data

Run the following Jupyter Notebook: analysis_coverage_WGS.ipynb
- input: .depth_unique.txt files
- output: locations of genes that are duplicated in LTEE clones



