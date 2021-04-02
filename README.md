# JUMP-Target

The `JUMP-Target` set of perturbations comprises three lists of perturbations

1. `JUMP-Target-Compound` – a list of compounds with diverse targets.
1. `JUMP-Target-ORF` – a list of ORF sequences corresponding to genes that are targets of compounds from `JUMP-Target-Compound`.
1. `JUMP-Target-CRISPR` – a list of sgRNA sequences corresponding to genes that are targets of compounds from `JUMP-Target-Compound`.

Both `JUMP-Target-ORF` and `JUMP-Target-CRISPR` have sgRNAs and ORFs corresponding to a set of 160 genes, each of which are targets of compounds in `JUMP-Target-Compound`. `JUMP-Target-ORF` has perturbations for an additional set of 15 genes that serve as negative controls (below).

Each of the 3 lists fit on a single 384-well plate; the suggested plate layouts are provided (below).

The target annotations were obtained from https://clue.io/repurposing.

This resource was created through the [JUMP-Cell Painting Consortium](https://jump-cellpainting.broadinstitute.org/).

**Versioning**
- There's a single version for the `JUMP-Target-CRISPR` and `JUMP-Target-CRISPR` plates  (`JUMP-Target-1-CRISPR` and `JUMP-Target-1-CRISPR` respectively)
- There are two versions os `JUMP-Target-Compound` (`JUMP-Target-Compound-1` and `JUMP-Target-Compound-2`). Both have the same set of compounds, but have different Broad sample IDs and different layouts.

-----

- [JUMP-Target-Compound](#jump-target-compound)
  * [Files](#files)
  * [Broad internal notes](#broad-internal-notes)
- [JUMP-Target-CRISPR](#jump-target-crispr)
  * [Files](#files-1)
- [JUMP-Target-ORF](#jump-target-orf)
  * [Files](#files-2)

<small><i><a href='http://ecotrust-canada.github.io/markdown-toc/'>Table of contents generated with markdown-toc</a></i></small>

## JUMP-Target-Compound

There are 306 compounds in total, of which 46 are included as controls serving different goals

1. `poscon_orf`: compounds that correlate strongly with (overexpressed) genes in previous Cell Painting experiments. There are 6 such compounds, and their corresponding genes are included in `JUMP-Target-ORF` and `JUMP-Target-CRISPR`
1. `poscon_cp`: compounds with a strong association with the genes that they target, according to [ChemicalProbes.org](https://www.chemicalprobes.org/). There are 26 such compounds, and their corresponding genes are included in `JUMP-Target-ORF` and `JUMP-Target-CRISPR`.
1. `poscon_diverse`: pairs of compounds that are strongly correlated to each other, and weakly correlated to other `poscon_diverse` pairs, in previous Cell Painting experiments. There are 7 such pairs, so 14 compounds in total.
1. `negcon`: [DMSO](https://pubchem.ncbi.nlm.nih.gov/compound/Dimethyl-sulfoxide) is the negative control.

The recommended concentration for these compounds is `5 uM`.

There are
- n=2 replicate wells for each of 14 `poscon_diverse` compounds
- n=64 DMSO wells
- n=1 well for the remaining compounds

### Files

[`JUMP-Target-1a_compound_metadata.tsv`](JUMP-Target-1a_compound_metadata.tsv)
[`JUMP-Target-1b_compound_metadata.tsv`](JUMP-Target-1b_compound_metadata.tsv)

| Column | Description |
| :----- | :---------- |
| InChIKey | [International Chemical Identifier](https://en.wikipedia.org/wiki/International_Chemical_Identifier) |
| pert_iname | Compound name |
| pubchem_cid    | PubChem ID e.g. [`72716071`](https://pubchem.ncbi.nlm.nih.gov/compound/72716071) |
| target | Gene target |
| pert_type | Perturbation type – `trt`: treatment, `control`: one of the 3 controls |
| control_type | Control type – `poscon_orf`, `poscon_cp`, or `poscon_diverse` |
| smiles | Simplified molecular-input line-entry system ([SMILES](https://en.wikipedia.org/wiki/Simplified_molecular-input_line-entry_system)) string |

[`JUMP-Target-1a_compound_platemap.tsv`](JUMP-Target-1a_compound_metadata.tsv)
[`JUMP-Target-1b_compound_platemap.tsv`](JUMP-Target-1b_compound_metadata.tsv)

| Column | Description |
| :----- | :---------- |
| well_position | Well position |
| broad_sample | Compound ID in Broad Institute's compound management database |
| solvent | Solvent (always DMSO) |


### Broad internal notes
- 306 compounds
- `JUMP-Target-1a_Compound`: 
  - Compound Request Number: CR-12417 - placed by Niranj Chandrasekaran - $10,404
  - 5 milliMolar 13.75 uL total volume (5 uL dead volume)
- `JUMP-Target-1b_Compound`: 
  - Compound Request Number: CR-12908 - placed by Niranj Chandrasekaran - $???
  - 5 milliMolar 13.75 uL total volume (5 uL dead volume)

## JUMP-Target-CRISPR

There are 335 sgRNAs (corresponding to 175 genes) in total, of which 88 sgRNAs are included as controls serving different goals

1. `poscon_orf`: the corresponding genes targets of the `poscon_orf` compounds. Total: 3 genes x 2 sgRNAs per gene (except for one gene which has a single sgRNA) = 5 sgRNAs.
1. `poscon_cp`: the corresponding genes targets of the `poscon_cp` compounds. Total: 13 genes x 2 sgRNAs per gene (except for one gene which has a single sgRNA) = 25 sgRNAs.
1. `poscon_diverse`: the corresponding genes targets of the `poscon_diverse` compounds. Total: 14 genes x 2 sgRNAs per gene = 28 sgRNAs.
1. `negcon`: 30 unique sgRNAs that serve as negative controls because they are either non-targeting (`NO_SITE`) or target intergenic region (`ONE_INTERGENIC_SITE`). `negcon` sgRNAs have an additional annotation e.g. `NO_SITE (5 zeros)`. The number of zeros indicates how deep into the ["threat matrix"](https://portals.broadinstitute.org/gpp/public/software/sgrna-scoring-help#spec) a particular sgRNA makes it before a single match is found. An sgRNA `negcon` with higher number of zeros is less likely to have off-target effects and therefore may be a better negative control.

There are
- n=2 replicate wells for each of `negcon`s, as well as for 1 `poscon_cp` sgRNA, 1 `poscon_orf` sgRNA, and 13 other sgRNAs
- n=1 well for each remaining sgRNAs
- n=4 empty wells

### Files

[`JUMP-Target-1_crispr_metadata.tsv`](JUMP-Target-1_crispr_metadata.tsv)

| Column | Description |
| :----- | :---------- |
| broad_sample | sgRNA id in Broad Institute's Genetic Perturbation Platform [database](https://portals.broadinstitute.org/gpp/public/) |
| gene | Gene targeted by the sgRNA |
| pert_type | Perturbation type – `trt`: treatment, `control`: one of the 4 controls |
| control_type | Control type – `negcon`, `poscon_orf`, `poscon_cp`, or `poscon_diverse` |
| target_sequence | sgRNA sequence |
| negcon_control_type | Negative control type – `NO_SITE` or `ONE_INTERGENIC_SITE` |

[`JUMP-Target-1_crispr_platemap.tsv`](JUMP-Target-1_crispr_metadata.tsv)

| Column | Description |
| :----- | :---------- |
| well_position | Well position |
| broad_sample | sgRNA id in Broad Institute's Genetic Perturbation Platform database |


## JUMP-Target-ORF

There are 175 ORFs (corresponding to 175 genes) in total, of which 45 ORFs (corresponding to 45 genes) are included as controls serving different goals and 130 genes are represented in duplicate on the plate.

All genes have a single corresponding ORF

1. `poscon_orf`: the corresponding genes targets of the `poscon_orf` compounds. Total: 3 genes.
1. `poscon_cp`: the corresponding genes targets of the `poscon_cp` compounds. Total: 13 genes.
1. `poscon_diverse`: the corresponding genes targets of the `poscon_diverse` compounds. Total: 14 genes.
1. `negcon`: genes that have had weak signatures in previous Cell Painting overexpression experiments. Total: 15 genes.

There are
- n=2 replicate wells for each of the 30 poscons
- n=4 replicate wells for each of the 15 negcons
- n=2 wells for each remaining ORF (130 of them)
- n=4 empty wells
- For a total of 384 wells

### Files

[`JUMP-Target-1_orf_metadata.tsv`](JUMP-Target-1_orf_metadata.tsv)

| Column | Description |
| :----- | :---------- |
| broad_sample | ORF id in Broad Institute's Genetic Perturbation Platform [database](https://portals.broadinstitute.org/gpp/public/) |
| gene | Gene overexpressed by the ORF |
| pert_type | Perturbation type – `trt`: treatment, `control`: one of the 4 controls |
| control_type | Control type – `negcon`, `poscon_orf`, `poscon_cp`, or `poscon_diverse` |

[`JUMP-Target-1_orf_platemap.tsv`](JUMP-Target-1_orf_platemap.tsv)

| Column | Description |
| :----- | :---------- |
| well_position | Well position |
| broad_sample | ORF id in Broad Institute's Genetic Perturbation Platform database |
