> Structural Variants Hackathon at Baylor College of Medicine, August 27-29, 2025

# Human_Haploblock_Lengths

## Contributors

## Aim

To construct a consensus map of haploblock breakpoints.

desired MVP: jupyter notebook -> graph -> parse -> haploblock lengths -> haploblock clusters

## Introduction

HapMap project, 50-100kb haploblocks not possible -> because of 2MB SVs -> they would disappear
haploblock - minimal unit of inheritance

pangenome graphs, trios data

How to make it simple and fast?

## Methods

Idea: diverse genomes (T2T) + 30 trios -> estimate haploblocks for each recombination hotspot (should be around 150 haploblocks per hotspot?) and compare with trios -> they should be the same

Trios data: https://github.com/genome-in-a-bottle/giab_data_indexes
- HG002
- mother: https://www.ncbi.nlm.nih.gov/datasets/genome/GCA_018852615.3/
- father: https://www.ncbi.nlm.nih.gov/datasets/genome/GCA_018852605.3/

Assemblies:
mother: https://ftp-trace.ncbi.nlm.nih.gov/ReferenceSamples/giab/release/AshkenazimTrio/HG004_NA24143_mother/latest/
father: https://ftp-trace.ncbi.nlm.nih.gov/ReferenceSamples/giab/release/AshkenazimTrio/HG003_NA24149_father/latest/ 

deCODE: https://genome.ucsc.edu/cgi-bin/hgTrackUi?db=hg38&g=recombRate2

Other:
- https://humanpangenome.org/data/
- https://github.com/human-pangenomics/hprc_intermediate_assembly

### Workflow

<img width="287" height="687" alt="workflow_BCMhack25-2" src="https://github.com/user-attachments/assets/ae6cc15c-9909-4f1d-9c2a-74bd1dd8d436" />

#### DNAnexus

## Results

## Use cases

## Future directions

## References

1. https://www.nature.com/articles/s41467-024-50079-5
2. https://pmc.ncbi.nlm.nih.gov/articles/PMC10234299
3. https://pmc.ncbi.nlm.nih.gov/articles/PMC12350169
