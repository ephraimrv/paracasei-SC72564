# SPAdes `--isolate -s` Assembly

SPAdes v4.2.0 run with the `--isolate` flag and single-library `-s` input.
**This is the definitive assembly** used for all downstream annotation, functional
profiling, and safety analysis in this repository, unless a subdirectory README
states otherwise.

Assembly summary: 41 contigs; N50 = 404,174 bp.

## Provenance

| File | Contents |
|---|---|
| `run_spades.sh` | Exact command used to produce this assembly |
| `run_spades.yaml` | SPAdes run configuration |
| `params.txt` | Full parameter record written by SPAdes |
| `spades.log` | Complete run log |
| `input_dataset.yaml`, `dataset.info` | Input library description |

## Primary outputs

| File | Contents |
|---|---|
| `contigs.fasta` | Assembled contigs |
| `scaffolds.fasta` | Assembled scaffolds |
| `contigs.paths`, `scaffolds.paths` | Assembly graph paths for the above |
| `assembly_graph.fastg` | Assembly graph (FASTG) |
| `assembly_graph_with_scaffolds.gfa` | Assembly graph with scaffold information (GFA) |
| `assembly_graph_after_simplification.gfa` | Simplified assembly graph (GFA) |
| `misc/broken_scaffolds.fasta` | Scaffolds split at gaps |

## Intermediate directories

`K21/`, `K33/`, `K55/`, `K77/` hold per-k-mer intermediate graphs and SPAdes'
own configuration templates; `pipeline_state/` records stage completion markers.
These are retained as produced by SPAdes and are not required to reproduce or
interpret the assembly — `run_spades.sh` and `params.txt` are sufficient for that.

## Downstream filtering

Contigs shorter than 200 bp were removed prior to annotation using
[`../remove-200bp.sh`](../remove-200bp.sh). Downstream analyses operate on the
filtered assembly.
