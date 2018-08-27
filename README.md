# Exploring the Differential Effects of Sequencing Resolution on Semi-Automated Genome Annotations
A project from Summer 2018 that compared the utility of newer ChIP methods ChIP-exo and ChIP-nexus on its effects on Segway's ability to generate annotations from this data of higher signal to noise ratio and near single base pair resolution.

## Pipeline
1. Data Cleaning
    - Download raw data from ENCODE project and NCBI SRA
    - Convert to bedgraph and sort data based on threshold cut off
    - QC with PhantomPeakQualTools + peak calling with MACS2 to generate bedgraphs
    - Store data in genomedata archive
2. Run Segway
    - Set minibatch training of 10 round on 1% of the genome
    - Try with 5 different resolutions: 100bp, 1bp, 2bp, 30bp, 50bp
3. Analyze Results
    - Recolour segway annotations with 10 different colours for visualization in genome browser
    - Run stable marriage Hungarian algorithm on annotations
    - Graph heatmaps and bipartite graphs in R. Account for negative/NaNs by adding pseudocount (LOD/2) to all data points prior to normalizing
