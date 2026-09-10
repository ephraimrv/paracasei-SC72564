# Average Nucleotide Identity (FastANI)

FastANI v1.34 comparisons of the three SCA72564 assemblies against
*Lacticaseibacillus paracasei* reference genomes. Reference assemblies are held in
[`../../references/`](../../references/).

## Contents

| File | Query assembly | References compared |
|---|---|---|
| `ref_list.txt` | — | Reference list passed to FastANI via `--refList` |
| `careful-ani-results.txt` | SPAdes `--careful` (`L_paracasei_careful_mra.fna`) | JCM 8130ᵀ, ATCC 334 |
| `isolate-ani-results.txt` | SPAdes `--isolate` (`L_paracasei_isolate_mra.fna`) | ATCC 334, JCM 8130ᵀ |
| `isolate_may_results.txt` | SPAdes `--isolate` (`L_paracasei_isolate_mra.fna`) | ATCC 25302, ATCC 334, JCM 8130ᵀ |

## Output format

FastANI writes tab-separated columns with no header row:

```
query    reference    ANI(%)    bidirectional_fragment_mappings    total_query_fragments
```

## Results

| Query | Reference | ANI (%) | Mapped / total fragments |
|---|---|---|---|
| `--careful` | JCM 8130ᵀ | 98.084 | 858 / 1008 |
| `--careful` | ATCC 334 | 98.0695 | 849 / 1008 |
| `--isolate` | ATCC 334 | 98.0876 | 845 / 1008 |
| `--isolate` | JCM 8130ᵀ | 98.0629 | 856 / 1008 |
| `--isolate` (May run) | ATCC 25302 | 98.2489 | 798 / 1008 |
| `--isolate` (May run) | ATCC 334 | 98.0467 | 847 / 1008 |
| `--isolate` (May run) | JCM 8130ᵀ | 98.0358 | 857 / 1008 |

All values fall above the 95–96% species delineation threshold, supporting
assignment to *L. paracasei* subsp. *paracasei*.

The value reported in the associated Microbiology Resource Announcements
publication — 98.08% ANI against *L. paracasei* subsp. *paracasei* JCM 8130ᵀ —
corresponds to the `--careful` assembly result in `careful-ani-results.txt`.

## Running the comparison

From the repository root:

```bash
fastANI -q <query_assembly.fna> --refList assembly_validation/ani/ref_list.txt -o results.txt
```

## Note on reference naming

The reference filenames recorded inside the result files
(`JCM8130_Type.fna`, `ATCC334_Ref.fna`, `ATCC_25302.fna`) are the working names
used at run time and differ from the filenames now held in
[`../../references/`](../../references/). As noted in that directory's README,
ATCC 25302, DSM 5622 and JCM 8130 designate the same type strain. The mapping
between working names and archived reference files should be confirmed before
these results are reused.
