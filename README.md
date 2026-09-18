# hpa_gastric_hpylori

Gastric protein expression in healthy stomach tissue vs. *H. pylori* infection —
8 genes, 2 conditions, built from Human Protein Atlas data. *H. pylori* is the most
common cause of chronic gastritis and stomach ulcers.

> ⚠️ **The `nTPM` values in the H_pylori rows are constructed, not measured.**
> They are HPA healthy-stomach nTPM scaled by fold changes measured separately in GSE60427.
> Only `log2FC_vs_healthy` is an observed quantity. No study measured nTPM in infected tissue.

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

| Direction in infection | Genes |
|---|---|
| Up — inflammatory response | LCN2, CXCL8, ANGPTL4 |
| Up in gastritis, down at metaplasia | ATP4B |
| Down — mucosal / glandular | MUC5AC, PGC |
| Unchanged | GKN1, TFF1 |

## Next step

Replace the estimated fold changes with observed values from an H. pylori gastritis series
(e.g. GEO **GSE60427**, **GSE27411**) and the analysis becomes a real comparison.

## Data source

[Human Protein Atlas](https://www.proteinatlas.org/) (proteinatlas.org), CC BY-SA 4.0.
