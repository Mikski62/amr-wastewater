
## Dataset Summary

This dataset supports the thesis *"Metagenomic Insights into AMR Gene Prevalence in Municipal Wastewater: A One Health Approach."* It includes processed outputs from metagenomic and 16S rRNA amplicon sequencing of raw influent wastewater samples collected in Summer 2023 and Winter 2024 a wastewater treatment plant (WWTP). The dataset contains antimicrobial resistance (AMR) gene profiles, taxonomic classifications, resistance mechanisms, disease relevance, and seasonal abundance counts. Risk assessment was performed using a modified version of the Zhang framework and an original metric: the Resistance Persistence Index (RPI).

## Languages

English

## Data Instances

A typical data point includes an AMR gene name, its associated host species, resistance mechanism, clinical relevance, and read abundance across seasonal samples.

```json
{
  "gene_name": "mecA",
  "read_species": "Staphylococcus aureus",
  "mechanism": "Beta-lactam resistance",
  "class": "Cell wall synthesis inhibitor",
  "disease": "Skin infections",
  "Influent_WWTP_7_24_23_MH2_S473 (Summer)": 103,
  "Influent_WWTP_1_24_24_MH1_S480 (Winter)": 245
}
```

## Data Fields

- `gene_name`: AMR gene detected via metagenomic sequencing  
- `read_species`: Bacterial host in which gene was detected  
- `mechanism`: Molecular mechanism of resistance  
- `class`: Drug class associated with resistance  
- `disease`: Associated human diseases  
- Sample columns: Seasonal read abundance per wastewater sample  

## Curation Rationale

This dataset enables environmental surveillance of AMR and pathogen prevalence by season, supporting public health monitoring under a One Health framework. Data were curated to evaluate temporal ARG persistence and risk in municipal wastewater.

## Initial Data Collection and Normalization

500 mL influent samples were collected weekly in Summer 2023 and Winter 2024 and processed using Nanotrap particles and the NucleoMag DNA/RNA Water Kit. Sequencing was performed using the Illumina MiSeq platform. Taxonomy and AMR identification used Tourmaline (for 16S) and Chan Zuckerberg ID (CZ ID) pipelines (for metagenomics). Data were normalized by reads per million (RPM), and seasonal persistence was calculated.

## Who are the source data producers?

Environmental microbes and AMR genes from untreated municipal influent collected by a coastal WWTP serving two-thirds of a metropolitan population.

## Annotations

AMR gene metadata include host taxonomy, drug resistance mechanisms, and associated diseases, curated from CARD repository.

## Annotation Process

CZ ID identified genes, hosts, and functional annotations. Additional annotation (e.g., disease relevance, mobility) was added manually. Zhang risk ranks and RPI scores were computed using custom R scripts.

## Who are the annotators?

Annotations were conducted by the dataset Michael Hajowski Jr., a master student at San Francisco State University.


## Social Impact of Dataset

Supports early warning systems for AMR trends and contributes to public health risk assessment through wastewater-based epidemiology. Enhances transparency and reproducibility of environmental AMR monitoring workflows.

## Discussion of Biases

- Sequencing detects DNA presence, not gene expression  
- Reference bias: novel genes may be missed  
- Risk ranks are database-dependent and limited by known pathogen associations  
- Seasonal data are limited to two timepoints (not longitudinal)

## Other Known Limitations

- Only influent samples analyzed (no effluent or replicate site)  
- Metagenomic reads with no match to databases are excluded  
- Assemblies include contigs ≥500 bp only  
- Mobility scores rely on contig-associated plasmid identification, which may underrepresent actual mobility



## Included Datasets

This repository includes three primary datasets from a comparative metagenomic and amplicon-based analysis of municipal wastewater:

1. **Metagenomic AMR Dataset** (`combined_amr_results_seasons.csv`)  
   - Shotgun metagenomic read counts of AMR genes across summer and winter samples  
   - Includes associated host taxonomy, resistance mechanism, and disease relevance  
   - Used to calculate Zhang risk ranks and Resistance Persistence Index (RPI)

2. **Metagenomic Taxonomic Dataset** (`combined_amr_results.csv`)  
   - Shotgun metagenomic taxonomic abundance table by species across all samples  
   - Used to evaluate taxonomic composition from metagenomic sequencing  
   - Enables community-level analysis of microbial dynamics across seasons

3. **16S rRNA Amplicon Dataset** (`taxa_sample_table.csv`)  
   - Genus-level taxonomic abundances derived from 16S rRNA V4-V5 amplicon sequencing  
   - Processed using Tourmaline (QIIME 2 + Snakemake)  
   - Used for alpha and beta diversity comparisons between seasons

These datasets are formatted to support microbial ecology and AMR surveillance analyses in a seasonal wastewater monitoring framework. Refer to file headers for detailed variable definitions.

## Dataset Curators

Michael Hajkowski Jr.
Anand Lab, Biology Department, San Francisco State University

## Citation Information

Hajkowski, M. (2025). Metagenomic Insights into AMR Gene Prevalence in Municipal Wastewater: A One Health Approach. Master’s Thesis, San Francisco State University. Dataset available at:https://github.com/Mikski62/amr-wastewater

## Contributions

Thanks to my PI Dr. Archana Anand PhD, Anand Lab, CZ ID team, and UCSD Genomics Core for support with sequencing.
