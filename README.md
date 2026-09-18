# hpa_gastric_hpylori
Analysis of protein expression differences in stomach tissue between healthy and H. pylori (which is the common cause of stomachache)conditions, using Human Protein Atlas data
# hpa_gastric_hpylori

Gastric protein expression in healthy stomach tissue vs. *H. pylori* infection —
8 genes, 2 conditions, built from Human Protein Atlas data.

> ⚠️ **Read this before using the numbers.**
> Only the **Healthy** column is measured data (HPA consensus stomach nTPM, pulled live from
> the HPA API). The **H_pylori** column is *derived*: it is the healthy baseline scaled by
> literature-reported fold changes (`H_pylori = Healthy × 2^log2FC`). No infected-patient
> samples were measured here. The `source` column in the CSV labels every row accordingly.
> Treat the H. pylori values as a hypothesis to test against real data, not as results.

## Genes

| Direction in infection | Genes |
|---|---|
| Down — mucosal protection / glandular loss | GKN1, TFF1, PGC, ATP4B, MUC5AC |
| Up — inflammatory response | ANGPTL4, CXCL8, LCN2 |

## Files

- `hpa_gastric_hpylori.ipynb` — Colab notebook: fetches HPA, builds the CSV, plots the comparison
- `hpa_gastric_hpylori.csv` — 16 rows (8 genes × 2 conditions), long format

CSV columns: `gene`, `ensembl`, `description`, `condition`, `nTPM`, `log2FC_vs_healthy`, `source`

## Reproduce

Open the notebook in Colab and Run all — it re-queries the HPA API, so it needs no local
setup and no data files. To use your own differential expression results, edit the `LOG2FC`
dict in the first cell; nothing else changes.

## Finding

The largest shifts are inflammatory induction (CXCL8 +700%, LCN2 +359%) against loss of the
gastric protection program (GKN1 −82%, TFF1 −65%, ATP4B −57%, PGC −50%). The two arms matter
differently for diagnosis: the inflammatory markers report active infection and resolve after
eradication, while GKN1/TFF1/ATP4B/PGC loss tracks glandular atrophy, which carries the gastric
cancer risk. Serum pepsinogen (PGC) is already a clinical atrophy screen.

## Next step

Replace the estimated fold changes with observed values from an H. pylori gastritis series
(e.g. GEO **GSE60427**, **GSE27411**) and the analysis becomes a real comparison.

## Data source

[Human Protein Atlas](https://www.proteinatlas.org/) (proteinatlas.org), CC BY-SA 4.0.
