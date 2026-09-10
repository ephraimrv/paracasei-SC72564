# *Lacticaseibacillus paracasei* subsp. *paracasei* SCA72564

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.20723035.svg)](https://doi.org/10.5281/zenodo.20723035)

This repository contains the raw data outputs and analysis files supporting the
*de novo* genome assembly and functional genomic characterization of
*L. paracasei* strain SCA72564, isolated from *Dioscorea esculenta* tubers in
Ilocos Norte, Philippines.

Raw Illumina paired-end sequencing reads are deposited at NCBI SRA under
accession [SRR35991900](https://www.ncbi.nlm.nih.gov/sra/SRR35991900)
(BioProject [PRJNA1293312](https://www.ncbi.nlm.nih.gov/bioproject/PRJNA1293312);
BioSample [SAMN53139918](https://www.ncbi.nlm.nih.gov/biosample/SAMN53139918)).
The assembled genome is accessible under GenBank
[JBSNBU010000000](https://www.ncbi.nlm.nih.gov/nuccore/JBSNBU000000000.1)
(GCA\_053769915.1; RefSeq GCF\_053769915.1).

---

## Repository Structure

| Path | Contents |
|---|---|
| `fastQC/fastQC_output/` | FastQC v0.12.1 quality reports for raw paired-end reads |
| `fastQC/fastqc_trimmed_output/` | FastQC v0.12.1 quality reports for Trimmomatic-trimmed paired reads |
| `spades_careful_output/` | SPAdes v4.2.0 `--careful` assembly (used for the MRA announcement) |
| `spades_isolate_output/` | SPAdes v4.2.0 `--isolate` assembly (41 contigs) |
| `spades--isolate-s-ouput/` | SPAdes v4.2.0 `--isolate -s` assembly — **definitive assembly used for all downstream analyses** (41 contigs; N50 = 404,174 bp) |
| `assembly_validation/quast_output/` | QUAST v5.3.0 structural metrics |
| `assembly_validation/busco_optimized_output/` | BUSCO v6.0.0 completeness assessment (DB: *lactobacillaceae_odb12*) |
| `assembly_validation/checkm2_optimized_output/` | CheckM2 v1.1.0 quality estimates |
| `assembly_validation/ani/` | FastANI v1.34 average nucleotide identity tables for all three assemblies |
| `references/` | Reference genomes used for the ANI comparison |
| `bakta_optimized_output/` | Bakta v1.12.0 structural annotation files (`.gff3`, `.gbff`, `.faa`, `.ffn`, `.fna`, `.tsv`, `.embl`) and circular genome map (`.png`, `.svg`) |
| `functional_analysis/` | eggNOG-mapper COG/KEGG assignments, CAZy subfamily Z-score tables, and ProbioMinServer2 enrichment outputs, in one subdirectory per assembly |
| `safety_analysis/` | Consolidated AMR, virulence, plasmid, prophage and insertion-sequence screening results |
| `remove-200bp.sh` | Bash script for filtering assembled contigs shorter than 200 bp prior to annotation |
| `CITATION.cff` | Machine-readable citation metadata |
| `LICENSE.md` | MIT License |

> **Note on assembly selection:** All results in `assembly_validation/`,
> `bakta_optimized_output/`, `functional_analysis/`, and `safety_analysis/`
> are derived strictly from the SPAdes `--isolate -s` assembly unless
> explicitly stated otherwise within a subdirectory README.

### Subdirectory documentation

Additional READMEs document individual directories: `references/`,
`assembly_validation/ani/`, `spades--isolate-s-ouput/`, `spades_careful_output/`,
`spades_isolate_output/`, `bakta_optimized_output/`, and
`functional_analysis/--isolate-s_assembly/`.

### Functional analysis layout

`functional_analysis/` holds one subdirectory per assembly —
`--careful_assembly/`, `--isolate_assembly/`, and `--isolate-s_assembly/` — each
containing `COG/`, `CAZy/`, and `KEGG pathway/` outputs together with antiSMASH
and gutSMASH archives. The `--isolate-s_assembly/` subdirectory additionally
contains `eggNOG_ELMOCPCJ.tsv` and `FIGURE2.py`, the custom Python script
generating Figure 2 of the manuscript.

### Safety analysis contents

`safety_analysis/` contains `ISEScan_ELMOCPCJ.tsv` (insertion sequence
classification) and `Safety_ELMOCPCJ.xlsx`, which consolidates the results of the
remaining screening tools listed below.

---

## Tools and Database Versions

### Assembly and Quality Control

| Tool | Version | Purpose |
|---|---|---|
| FastQC | v0.12.1 | Read quality assessment (raw and trimmed) |
| Trimmomatic | v0.40 | Adapter removal and quality trimming |
| SPAdes | v4.2.0 | *De novo* genome assembly |
| QUAST | v5.3.0 | Assembly structural metrics |
| BUSCO | v6.0.0 (DB: *lactobacillaceae\_odb12*) | Genome completeness assessment |
| CheckM2 | v1.1.0 | Machine-learning genome quality estimation |
| FastANI | v1.34 | Average Nucleotide Identity |

### Annotation and Functional Profiling

| Tool | Version | Purpose |
|---|---|---|
| Bakta | v1.12.0 | Structural genome annotation and circular map |
| eggNOG-mapper | v2.1.12 (DB: eggNOG v5.0.2, Mar. 2021) | COG and KEGG functional categories |
| ProbioMinServer2 | — | Integrated COG/KEGG/CAZy enrichment pipeline |
| antiSMASH | v8.0.4 | Secondary metabolite biosynthetic gene cluster mining |
| gutSMASH | v2.0.1 | Primary metabolic gene cluster mining |

### Safety and Mobile Genetic Elements

| Tool | Version / Database | Purpose |
|---|---|---|
| RGI | v6.0.3 (DB: CARD v4.0.2, Nov. 2023) | Acquired AMR gene detection |
| ResFinder | v4.6.0 (DB: resfinder\_db, Aug. 2024) | AMR gene detection |
| AMRFinderPlus | v4.0.3 (DB: Oct. 2024) | AMR gene detection |
| BLASTN | v2.16.0 (DB: VFDB, Dec. 2024) | Virulence factor screening |
| VirulenceFinder | v2.0.4 | Virulence factor detection |
| BLASTX | v2.16.0 (DB: PHI-base v4.16, May 2024) | Pathogenic marker detection |
| PlasmidFinder | v2.1.6 (DB: plasmidfinder\_db v2.2.0, Nov. 2024) | Plasmid replicon identification |
| PlasmidHunter | v1.4.5 (DB: May 2024) | Plasmid detection |
| Phigaro | v2.4.0 (DB: Jan. 2024) | Prophage mapping |
| ISEScan | v1.7.2.3 (DB: Apr. 2021) | Insertion sequence classification |

### Visualization

| Tool | Version | Purpose |
|---|---|---|
| Matplotlib | v3.10.9 | Custom enrichment plots (Figure 2; see `functional_analysis/--isolate-s_assembly/FIGURE2.py`) |

---

## Excluded Data

Due to GitHub file size constraints, trimmed reads (Trimmomatic output) are not
hosted here. To reproduce the trimming step, retrieve the raw reads from SRA
([SRR35991900](https://www.ncbi.nlm.nih.gov/sra/SRR35991900)) and apply
standard Trimmomatic paired-end filtering with `SLIDINGWINDOW:4:20` and a
minimum Phred score of 20.

---

## Citation

If you use data or scripts from this repository, please cite:

> Vallente, J.E.R. (2026). *paracasei-SCA72564: Data and analysis files for
> the de novo genome assembly and functional characterization of
> Lacticaseibacillus paracasei SCA72564* (Version 1.0.0). Zenodo.
> https://doi.org/10.5281/zenodo.20723035

Citation metadata is also provided in [`CITATION.cff`](CITATION.cff).

---

## License

This repository is released under the MIT License. See `LICENSE.md` for details.
