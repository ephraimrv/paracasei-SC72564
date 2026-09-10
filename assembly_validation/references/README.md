# Reference Genomes

Reference assemblies used for average nucleotide identity (ANI) comparison against
the *Lacticaseibacillus paracasei* subsp. *paracasei* SCA72564 assemblies.
See [`../assembly_validation/ani/`](../assembly_validation/ani/) for the FastANI
results derived from these references.

All files are unmodified NCBI downloads in FASTA nucleotide (`.fna`) format.

## Contents

| File | Accession (first record) | Strain designation per record header | Records | Total bases |
|---|---|---|---|---|
| `L_paracasei_ATCC334.fna` | `GG670224.1` | *Lactobacillus paracasei* subsp. *paracasei* ATCC 25302, genomic scaffold SCAFFOLD73 | 73 | 2,991,737 |
| `L_paracasei_DSM5622.fna` | `AZGH01000001.1` | *Lacticaseibacillus paracasei* subsp. *paracasei* ATCC 25302 = DSM 5622 = JCM 8130, strain DSM 5622, Scaffold1 | 170 | 2,881,963 |
| `L_paracasei_NBRC15889.fna` | `BJVL01000001.1` | *Lacticaseibacillus paracasei* subsp. *paracasei* NBRC 15889, sequence001 | 130 | 2,872,191 |
| `L_rhamnosus_GG.fna` | `FM179322.1` | *Lactobacillus rhamnosus* GG (ATCC 53103), complete genome | 1 | 3,010,111 |

Record counts and base counts were computed directly from the files in this
directory.

## Strain synonymy

Per the header of `L_paracasei_DSM5622.fna`, the designations **ATCC 25302**,
**DSM 5622** and **JCM 8130** refer to the same type strain. Comparisons against
more than one of these accessions therefore measure identity against the same
organism represented by different assemblies, not against independent strains.

*L. rhamnosus* GG is included as a congeneric outgroup and is not expected to fall
within the species-level ANI threshold.

## Note on file naming

The header of `L_paracasei_ATCC334.fna` identifies the record as **ATCC 25302**,
not ATCC 334. The filename and the record content should be reconciled against
the source accession before this file is cited as an ATCC 334 reference.

## Reference lists used at run time

`../assembly_validation/ani/ref_list.txt` is the reference list passed to FastANI
via `--refList`. It names the files in this directory using repository-relative
paths.
