# JUMP-Target

The `JUMP-Target` set of perturbations comprises three lists of perturbations

1. `JUMP-Target-Compound` – a list of compounds with diverse targets. See also [JUMP-MOA](https://github.com/jump-cellpainting/JUMP-MOA) for a similar compound set.
1. `JUMP-Target-ORF` – a list of ORF sequences corresponding to genes that are targets of compounds from `JUMP-Target-Compound`.
1. `JUMP-Target-CRISPR` – a list of sgRNA sequences corresponding to genes that are targets of compounds from `JUMP-Target-Compound`.

Both `JUMP-Target-ORF` and `JUMP-Target-CRISPR` have sgRNAs and ORFs corresponding to a set of 160 genes, each of which are targets of compounds in `JUMP-Target-Compound`. `JUMP-Target-ORF` has perturbations for an additional set of 15 genes that serve as negative controls (below).

Each of the 3 lists fit on a single 384-well plate; the suggested plate layouts are provided (below).

The target annotations were obtained from https://clue.io/repurposing.

This resource was created through the [JUMP-Cell Painting Consortium](https://jump-cellpainting.broadinstitute.org/).

**Versioning**
- There's a single version for the `JUMP-Target-CRISPR` and `JUMP-Target-ORF` plates  (`JUMP-Target-1-CRISPR` and `JUMP-Target-1-ORF` respectively)
- There are two versions of `JUMP-Target-Compound` (`JUMP-Target-1-Compound` and `JUMP-Target-2-Compound`). Both have the same set of compounds, but have different Broad sample IDs and different layouts. `JUMP-Target-2-Compound`  is used in the production of the [JUMP dataset](https://jump-cellpainting.broadinstitute.org/results). We recommend using this layout because it will remove layout as a potential confounder when matching against the JUMP dataset.

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

There are [301](https://github.com/jump-cellpainting/JUMP-Target/issues/9) compounds in total, of which 46 are included as controls serving different goals

1. `poscon_orf`: compounds that correlate strongly with (overexpressed) genes in previous Cell Painting experiments. There are 6 such compounds, and their corresponding 3 genes are included in `JUMP-Target-ORF` and `JUMP-Target-CRISPR`
1. `poscon_cp`: compounds with a strong association with the genes that they target, according to [ChemicalProbes.org](https://www.chemicalprobes.org/). There are 26 such compounds, and their corresponding 13 genes are included in `JUMP-Target-ORF` and `JUMP-Target-CRISPR`.
1. `poscon_diverse`: pairs of compounds that are strongly correlated to each other, and weakly correlated to other `poscon_diverse` pairs, in previous Cell Painting experiments. There are 7 such pairs, so 14 compounds in total.
1. `negcon`: [DMSO](https://pubchem.ncbi.nlm.nih.gov/compound/Dimethyl-sulfoxide) is the negative control.

The recommended concentration for these compounds is `5 uM`.

There are
- n=2 replicate wells for each of 14 `poscon_diverse` compounds
- n=64 DMSO wells
- n=1 well for the remaining compounds

The company Specs has assembled the compounds for purchase; for info contact tamara.baptist@specs.net

### Files

[`JUMP-Target-1_compound_metadata.tsv`](JUMP-Target-1_compound_metadata.tsv)
[`JUMP-Target-2_compound_metadata.tsv`](JUMP-Target-2_compound_metadata.tsv)

| Column | Description |
| :----- | :---------- |
| pert_iname | Compound name |
| pubchem_cid    | PubChem ID e.g. [`72716071`](https://pubchem.ncbi.nlm.nih.gov/compound/72716071) |
| target | Gene target |
| pert_type | Perturbation type – `trt`: treatment, `control`: one of the 3 controls |
| control_type | Control type – `poscon_orf`, `poscon_cp`, or `poscon_diverse` |
| smiles | Simplified molecular-input line-entry system ([SMILES](https://en.wikipedia.org/wiki/Simplified_molecular-input_line-entry_system)) string |
| InChI | [International Chemical Identifier](https://en.wikipedia.org/wiki/International_Chemical_Identifier) corresponding to `smiles`|
| InChIKey | InChIKey generated from `InChI` |

`smiles` was standardized using [JUMP-CP Standardizer](https://github.com/broadinstitute/monorepo/blob/912315df698cc0f3e9daadcd6ef994a7af94fbdd/libs/smiles/src/smiles/standardize_smiles.py).
See https://github.com/jump-cellpainting/JUMP-Target/pull/34 for details about the standardization.

[`JUMP-Target-1_compound_platemap.tsv`](JUMP-Target-1_compound_platemap.tsv)
[`JUMP-Target-2_compound_platemap.tsv`](JUMP-Target-2_compound_platemap.tsv)

| Column | Description |
| :----- | :---------- |
| well_position | Well position |
| broad_sample | Compound ID in Broad Institute's compound management database |
| solvent | Solvent (always DMSO) |


### Broad internal notes
- [301](https://github.com/jump-cellpainting/JUMP-Target/issues/9) compounds
- `JUMP-Target-1_Compound`: 
  - Compound Request Number: CR-12417 - placed by Niranj Chandrasekaran - $10,404
  - 5 milliMolar 13.75 uL total volume (5 uL dead volume)
- `JUMP-Target-2_Compound`:
  - Compound Request Number: CR-12908 - placed by Niranj Chandrasekaran - $???
  - 5 milliMolar 13.75 uL total volume (5 uL dead volume)
  - This plate was created because CDoT was unable to create plates with the same plate map as `JUMP-Target-1` for 
    the production experiments. Thus, the compounds in `JUMP-Target-2` are identical to the compounds in `JUMP-Target-1` but the plate maps are different. The `broad sample` IDs of some compounds are also different.
    - To map the compounds in `JUMP-Target-1` to `JUMP-Target-2` use `InChIKey` for "joining".

## JUMP-Target-CRISPR

There are 335 sgRNAs (corresponding to 175 genes) in total, of which 88 sgRNAs are included as controls serving different goals

1. `poscon_orf`: the corresponding genes targets of the `poscon_orf` compounds. Total: 3 genes, where 2 genes have 2 sgRNAs each and 1 gene has 1 sgRNA = 5 sgRNAs total.
1. `poscon_cp`: the corresponding genes targets of the `poscon_cp` compounds. Total: 13 genes, where 12 genes have 2 sgRNAs each and 1 gene has 1 sgRNA = 25 sgRNAs total.
1. `poscon_diverse`: the corresponding genes targets of the `poscon_diverse` compounds. Total: 14 genes x 2 sgRNAs per gene = 28 sgRNAs.
1. `negcon`: 30 unique sgRNAs that serve as negative controls because they are either non-targeting (`NO_SITE`) or target intergenic region (`ONE_INTERGENIC_SITE`). `negcon` sgRNAs have an additional annotation e.g. `NO_SITE (5 zeros)`. The number of zeros indicates how deep into the ["threat matrix"](https://portals.broadinstitute.org/gpp/public/software/sgrna-scoring-help#spec) a particular sgRNA makes it before a single match is found. An sgRNA `negcon` with higher number of zeros is less likely to have off-target effects and therefore may be a better negative control.

For the remaining treatment genes (non-controls):
- 117 genes have 2 sgRNAs each
- 13 genes have 1 sgRNA each

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

[`JUMP-Target-1_crispr_platemap.tsv`](JUMP-Target-1_crispr_platemap.tsv)

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

## Compound and gene selection

The list of compounds were derived from [Broad's Drug Repurposing Hub](https://clue.io/repurposing) dataset, a curated and annotated collection of FDA-approved drugs, clinical trial drugs, and pre-clinical tool compounds. The genes perturbed by genetic perturbations were chosen because they are the annotated targets of the compounds. The Repurposing Hub compounds were filtered using the following criteria:

1. The compounds should target genes that belong to diverse gene families. This is because the ideal methods would work well for many different biological pathways, not just a few that are well-characterized and/or easy to predict.
2. Each gene should be targeted by at least two compounds so that gene-compound matching and compound-compound matching can both be performed using the dataset.
3. The constraint that each compound should target only a single gene, was considered. However, this criterion is difficult to achieve due to polypharmacology, which is the property for compounds to bind and impact many different gene products in the cell; this is especially common for protein kinase inhibitors in the dataset. Instead, only the so-called “historical compounds” listed in the [Chemical Probes Portal](https://www.chemicalprobes.org/browse_probes), comprising compounds that are known to be quite non-selective (or not sufficiently potent) compared with other available chemical probes, were filtered out.
4. Three types of positive control compounds and the genes that they target were selected. ([Compound positive controls](https://github.com/jump-cellpainting/JUMP-Target#jump-target-compound), [CRISPR positive controls](https://github.com/jump-cellpainting/JUMP-Target#jump-target-crispr), and [ORF positive controls](https://github.com/jump-cellpainting/JUMP-Target#jump-target-orf)).
5. To ensure that the compounds and genes selected were available for performing experiments, compounds that were unavailable for purchase from at least one of four compound vendors (Sigma, SelleckChem, Tocris, and MedChemEx) and genes for which genetic reagents were unavailable from [Broad's GPP portal](https://portals.broadinstitute.org/gpp/public/) were filtered out.
6. Compounds that belong to DEA's list of controlled substances or OPCW's list of chemical weapons precursors were also excluded.

--- 

## Positive control compounds

Based on our experiments with the Target-1 compounds plates, we have identified a list of eight compounds (and also a subset of four compounds) with maximally diverse phenotypes. 

| pert_iname    | InChIKey                    | Vendor URL                                             | clue.io URL                                          | 
| ------------- | --------------------------- | ------------------------------------------------------ | ---------------------------------------------------- | 
| **AMG900**    | IVUGFMLRJOCGAS-UHFFFAOYSA-N | https://www.selleckchem.com/products/amg-900.html      | https://clue.io/repurposing-app?q=Name:AMG900        | 
| NVS-PAK1-1    | OINGHOPGNMYCAB-INIZCTEOSA-N | https://www.medchemexpress.com/NVS-PAK1-1.html         | https://clue.io/repurposing-app?q=Name:NVS-PAK1-1    | 
| dexamethasone | UREBDLICKHMUKA-CXSFZGCWSA-N | https://www.tocris.com/products/dexamethasone_1126     | https://clue.io/repurposing-app?q=Name:dexamethasone | 
| **LY2109761** | IHLVSLOZUHKNMQ-UHFFFAOYSA-N | https://www.selleckchem.com/products/ly2109761.html    | https://clue.io/repurposing-app?q=Name:LY2109761     | 
| FK-866        | KPBNHDGDUADAGP-VAWYXSNFSA-N | https://www.selleckchem.com/products/apo866-fk866.html | https://clue.io/repurposing-app?q=Name:FK-866        |
| **quinidine** | LOUPRKONTZGTKE-LHHVKLHASA-N | https://www.medchemexpress.com/Quinidine.html          | https://clue.io/repurposing-app?q=Name:quinidine     |
| **TC-S-7004** | CQKBSRPVZZLCJE-UHFFFAOYSA-N | https://www.tocris.com/products/tc-s-7004_5088         | https://clue.io/repurposing-app?q=Name:TC-S-7004     |
| aloxistatin   | SRVFFFJZQVENJC-IHRRRGAJSA-N | https://www.medchemexpress.com/Aloxistatin.html        | https://clue.io/repurposing-app?q=Name:aloxistatin   |

Compound names in **bold** is the subset of four compounds. 

### Layout
Our recommendation is to have at least four replicates of the eight (or four) compounds spread across the plate. If such a layout is not possible, then we recommend the following for a 384-well plate.

| pert_iname    | well_position    |
| ------------- | ---------------- |
| **AMG900**    | B1, J1, F24, N24 |
| NVS-PAK1-1    | F1, N1, B24, J24 |
| dexamethasone | C1, K1, G24, O24 |
| **LY2109761** | E1, M1, A24, I24 |
| FK-866        | D1, L1, H24, P24 |
| **quinidine** | G1, O1, C24, K24 |
| **TC-S-7004** | H1, P1, D24, L24 |
| aloxistatin   | A1, I1, E24, M24 |

For a 1536-well plate, the layout is similar, but in four quadrants.

## Control mappings


### poscon_diverse

| ID                     |   pair | target_gene   | InChIKey       | broad_compound_id      | broad_orf_id       | broad_crispr_id_1   | broad_crispr_id_2   |
|:-----------------------|-------:|:--------------|:---------------|:-----------------------|:-------------------|:--------------------|:--------------------|
| poscon_diverse-pair0-1 |      0 | RET           | XKFTZKGMDDZMJI | BRD-K07881437-001-03-8 | ccsbBroad304_14827 | BRDN0001058343      | BRDN0001058011      |
| poscon_diverse-pair0-2 |      0 | TUBB          | MTJHLONVHHPNSI | BRD-K23363278-001-02-1 | ccsbBroad304_05206 | BRDN0001489809      | BRDN0001488241      |
| poscon_diverse-pair1-1 |      1 | HSP90AA1      | RVAQIUULWULRNW | BRD-K38852836-001-04-9 | ccsbBroad304_06412 | BRDN0001488886      | BRDN0001483257      |
| poscon_diverse-pair1-2 |      1 | PIK3CG        | CWHUFRVAEUJCEF | BRD-K42191735-001-08-7 | ccsbBroad304_14762 | BRDN0001065162      | BRDN0001065152      |
| poscon_diverse-pair2-1 |      2 | NAMPT         | KPBNHDGDUADAGP | BRD-K58550667-001-08-7 | ccsbBroad304_07557 | BRDN0001484730      | BRDN0001481327      |
| poscon_diverse-pair2-2 |      2 | AKT1          | AFJRDFWMXUECEW | BRD-K25412176-001-01-9 | ccsbBroad304_14538 | BRDN0001054985      | BRDN0000562836      |
| poscon_diverse-pair3-1 |      3 | KRAS          | DHMTURDWPRKSOA | BRD-K41599323-001-02-3 | ccsbBroad304_16173 | BRDN0001054815      | BRDN0000563627      |
| poscon_diverse-pair3-2 |      3 | PAK4          | AYCPARAPKDAOEN | BRD-K37764012-001-03-3 | ccsbBroad304_02392 | BRDN0001145608      | BRDN0001147629      |
| poscon_diverse-pair4-1 |      4 | DNMT3A        | NMUSYJAQQFHJEW | BRD-K03406345-001-21-1 | ccsbBroad304_00454 | BRDN0001066838      | BRDN0001066751      |
| poscon_diverse-pair4-2 |      4 | IMPDH1        | WYWHKKSPHMUBEB | BRD-K49350383-001-13-7 | ccsbBroad304_06451 | BRDN0001489452      | BRDN0001488805      |
| poscon_diverse-pair5-1 |      5 | CDK7          | HUXYBQXJVXOMKX | BRD-K64800655-001-09-0 | ccsbBroad304_00280 | BRDN0001162216      | BRDN0001147450      |
| poscon_diverse-pair5-2 |      5 | PLK1          | XQVVPGYIWAGRNI | BRD-K64890080-001-02-1 | ccsbBroad304_14770 | BRDN0001144995      | BRDN0001054037      |
| poscon_diverse-pair6-1 |      6 | CHEK2         | IAYGCINLNONXHY | BRD-K86525559-001-07-8 | ccsbBroad304_14989 | BRDN0000585854      | BRDN0001145610      |
| poscon_diverse-pair6-2 |      6 | GABRB2        | ALBKMJDFBZVHAK | BRD-K33882852-003-02-8 | ccsbBroad304_00607 | BRDN0001486784      | BRDN0001482741      |

### Other poscons

| ID            | target_gene   | broad_compound_id_1    | broad_compound_id_2    | broad_orf_id       | broad_crispr_id_1   | broad_crispr_id_2   |
|:--------------|:--------------|:-----------------------|:-----------------------|:-------------------|:--------------------|:--------------------|
| poscon_cp-00  | AURKB         | BRD-K21728777-001-02-3 | BRD-K55966568-001-09-6 | ccsbBroad304_14932 | BRDN0001054845      | BRDN0000562944      |
| poscon_cp-01  | BRD4          | BRD-K13094524-001-04-2 | BRD-K12502280-001-11-4 | ccsbBroad304_11738 | BRDN0000733514      | BRDN0001146786      |
| poscon_cp-02  | CLK1          | BRD-K66430217-001-03-8 | BRD-K97072811-001-11-4 | ccsbBroad304_00326 | BRDN0001147209      | BRDN0001146512      |
| poscon_cp-03  | DYRK1B        | BRD-K89517477-001-01-4 | BRD-K80935598-001-01-1 | ccsbBroad304_14931 | BRDN0001149482      | BRDN0001149418      |
| poscon_cp-04  | ERBB2         | BRD-K76908866-001-07-6 | BRD-K61642990-001-01-0 | ccsbBroad304_14631 | BRDN0001148320      | BRDN0000579738      |
| poscon_cp-05  | EZH2          | BRD-K91535048-001-01-2 | BRD-K26989966-001-04-3 | ccsbBroad304_00526 | BRDN0001057455      |                     |
| poscon_cp-06  | FLT3          | BRD-K90747162-001-01-4 | BRD-K91283740-003-01-6 | ccsbBroad304_14644 | BRDN0001145324      | BRDN0001149376      |
| poscon_cp-07  | HDAC3         | BRD-K61688984-001-02-9 | BRD-K61397605-001-01-8 | ccsbBroad304_07311 | BRDN0000582721      | BRDN0000733096      |
| poscon_cp-08  | IGF1R         | BRD-K15179513-001-04-2 | BRD-K24696047-001-02-3 | ccsbBroad304_14671 | BRDN0001065819      | BRDN0001065728      |
| poscon_cp-09  | JAK1          | BRD-K16803204-001-01-6 | BRD-K53972329-001-01-3 | ccsbBroad304_14679 | BRDN0001065674      | BRDN0001065858      |
| poscon_cp-10  | MET           | BRD-K73319509-001-08-0 | BRD-K19477839-001-07-6 | ccsbBroad304_14696 | BRDN0000734703      | BRDN0001065558      |
| poscon_cp-11  | PAK1          | BRD-K19333160-001-01-3 | BRD-K28132190-001-02-0 | ccsbBroad304_01144 | BRDN0001145958      | BRDN0001147867      |
| poscon_cp-12  | USP1          | BRD-K93942811-001-01-3 | BRD-K81197548-003-01-4 | ccsbBroad304_01760 | BRDN0001487607      | BRDN0001484218      |
| poscon_orf-00 | BRAF          | BRD-K73789395-001-09-9 | BRD-K62810658-001-11-4 | ccsbBroad304_16175 | BRDN0001054801      | BRDN0000562882      |
| poscon_orf-01 | CDK2          | BRD-K50836978-001-03-3 | BRD-K07762753-001-05-1 | ccsbBroad304_14572 | BRDN0001147786      | BRDN0001148950      |
| poscon_orf-02 | MAPK14        | BRD-K54330070-001-19-6 | BRD-A37704979-001-12-3 | ccsbBroad304_00371 | BRDN0001148417      |                     |
