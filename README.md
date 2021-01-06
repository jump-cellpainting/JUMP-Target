# JUMP-Target

The `JUMP-Target` set of perturbations comprises three lists of perturbations

1. `JUMP-Target-Compound` – a list of compounds with diverse targets that fit on a single 384-well plate.
1. `JUMP-Target-ORF` – a list of cDNA sequences corresponding to genes that are targets of compounds from `JUMP-Target-Compound`.
1. `JUMP-Target-CRISPR` – a list of sgRNA sequences corresponding to genes that are targets of compounds from `JUMP-Target-Compound`.


## JUMP-Target-Compound

There are 306 compounds in total, of which 40 are included as controls serving different goals

1. `poscon_orf`: compounds that correlate strongly with (overexpressed) genes in previous Cell Painting experiments. There are 6 such compounds, and their corresponding genes are included in `JUMP-Target-ORF` and `JUMP-Target-CRISPR`
1. `poscon_cp`: compounds with a strong association with the genes that they target, according to [ChemicalProbes.org](https://www.chemicalprobes.org/). There are 26 such compounds, and their corresponding genes are included in `JUMP-Target-ORF` and `JUMP-Target-CRISPR`.
1. `poscon_diverse`: pairs of compounds that are strongly correlated to each other, and weakly correlated to other `poscon_diverse` pairs, in previous Cell Painting experiments. There are 7 such pairs, so 14 compounds in total.

The recommended concentration for these compounds is `5 uM`.

There are
- n=2 replicate wells for each of 14 `poscon_diverse` compounds
- n=64 DMSO wells
- n=1 well for the remaining compounds


### Files

[`JUMP-Target_compound_metadata.tsv`](JUMP-Target_compound_metadata.tsv)

| Column | Description |
| :----- | :---------- |
| InChIKey | [International Chemical Identifier](https://en.wikipedia.org/wiki/International_Chemical_Identifier) |
| pert_iname | Compound name |
| pubchem_cid    | PubChem ID e.g. [`72716071`](https://pubchem.ncbi.nlm.nih.gov/compound/72716071) |
| target | Gene target |
| pert_type | Perturbation type – `trt`: treatment, `control`: one of the 3 controls |
| control_type | Control type – `poscon_orf`, `poscon_cp`, or `poscon_diverse` |
| smiles | Simplified molecular-input line-entry system ([SMILES](https://en.wikipedia.org/wiki/Simplified_molecular-input_line-entry_system)) string |

[`JUMP-Target_compound_platemap.tsv`](JUMP-Target_compound_metadata.tsv)

| Column | Description |
| :----- | :---------- |
| well_position | Well position |
| broad_sample | Compound ID in Broad Institute's compound management database |
| solvent | Solvent (always DMSO) |


## JUMP-Target-CRISPR

There are 335 sgRNAs (corresponding to 160 genes) in total, of which 88 sgRNAs are included as controls serving different goals

1. `poscon_orf`: the corresponding genes targets of the `poscon_orf` compounds. Total: 3 genes x 2 sgRNAs per gene (except for one gene which has a single sgRNA) = 5 sgRNAs.
1. `poscon_cp`: the corresponding genes targets of the `poscon_cp` compounds. Total: 13 genes x 2 sgRNAs per gene (except for one gene which has a single sgRNA) = 25 sgRNAs.
1. `poscon_diverse`: the corresponding genes targets of the `poscon_diverse` compounds. Total: 14 genes x 2 sgRNAs per gene = 28 sgRNAs.
1. `negcon`: genes that have had weak signatures in previous Cell Painting overexpression experiments (15 genes x 2 sgRNAs per gene = 30 sgRNAs)

There are
- n=2 replicate wells for each of `negcon`s, as well as for 1 `poscon_cp` sgRNA, 1 `poscon_orf` sgRNA, and 13 other sgRNAs
- n=1 well for each remaining sgRNAs
- n=4 empty wells

### Files

[`JUMP-Target_crispr_metadata.tsv`](JUMP-Target_crispr_metadata.tsv)

| Column | Description |
| :----- | :---------- |
| broad_sample | sgRNA id in Broad Institute's Genetic Perturbation Platform database |
| gene | Gene targeted by the sgRNA |
| pert_type | Perturbation type – `trt`: treatment, `control`: one of the 3 controls |
| control_type | Control type – `poscon_orf`, `poscon_cp`, or `poscon_diverse` |
| target_sequence | sgRNA sequence |

[`JUMP-Target_crispr_platemap.tsv`](JUMP-Target_crispr_metadata.tsv)

| Column | Description |
| :----- | :---------- |
| well_position | Well position |
| broad_sample | sgRNA id in Broad Institute's Genetic Perturbation Platform database |


## JUMP-Target-ORF

There are 175 ORFs (corresponding to 175 genes) in total, of which 45 ORFs (corresponding to 45 genes) are included as controls serving different goals

All genes have a single corresponding ORF

1. `poscon_orf`: the corresponding genes targets of the `poscon_orf` compounds. Total: 3 genes.
1. `poscon_cp`: the corresponding genes targets of the `poscon_cp` compounds. Total: 13 genes.
1. `poscon_diverse`: the corresponding genes targets of the `poscon_diverse` compounds. Total: 14 genes.
1. `negcon`: genes that have had weak signatures in previous Cell Painting overexpression experiments. Total: 15 genes.

There are
- n=2 replicate wells for each of the 45 controls
- n=1 well for each remaining sgRNAs
- n=4 empty wells

### Files

[`JUMP-Target_orf_metadata.tsv`](JUMP-Target_orf_metadata.tsv)

| Column | Description |
| :----- | :---------- |
| broad_sample | ORF id in Broad Institute's Genetic Perturbation Platform database |
| gene | Gene overexpressed by the ORF |
| pert_type | Perturbation type – `trt`: treatment, `control`: one of the 3 controls |
| control_type | Control type – `poscon_orf`, `poscon_cp`, or `poscon_diverse` |

[`JUMP-Target_crispr_platemap.tsv`](JUMP-Target_crispr_metadata.tsv)

| Column | Description |
| :----- | :---------- |
| well_position | Well position |
| broad_sample | ORF id in Broad Institute's Genetic Perturbation Platform database |



