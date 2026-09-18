# hpa_gastric_hpylori

Gastric protein expression in healthy stomach tissue vs. *H. pylori* infection —
8 genes, 2 conditions, built from Human Protein Atlas data. *H. pylori* is the most
common cause of chronic gastritis and stomach ulcers.

> ⚠️ **The `nTPM` values in the H_pylori rows are constructed, not measured.**
> They are HPA healthy-stomach nTPM scaled by fold changes measured separately in GSE60427.
> Only `log2FC_vs_healthy` is an observed quantity. No study measured nTPM in infected tissue.


## Files

- `hpa_gastric_hpylori.ipynb` — Colab notebook: fetches HPA, builds the CSV, plots the comparison
- `hpa_gastric_hpylori.csv` — 16 rows (8 genes × 2 conditions), long format

CSV columns: `gene`, `ensembl`, `description`, `condition`, `nTPM`, `log2FC_vs_healthy`, `source`

## Reproduce

Open the notebook in Colab and Run all — it re-queries the HPA API, so it needs no local
setup and no data files. To use your own differential expression results, edit the `LOG2FC`
dict in the first cell; nothing else changes.

## Finding

Measured in GSE60427 (16 Hp+ gastritis vs 8 Hp− normal biopsies), log2FC:

| Gene | Gastritis | IM |
|---|---|---|
| LCN2 | +4.22 | +3.29 |
| CXCL8 | +2.66 | +2.40 |
| ANGPTL4 | +1.36 | +2.54 |
| ATP4B | +1.35 | −0.64 |
| MUC5AC | −0.58 | −1.46 |
| PGC | −0.32 | −0.96 |
| GKN1 | −0.05 | −0.31 |
| TFF1 | −0.02 | −0.12 |

The signal is inflammatory: LCN2, CXCL8 and ANGPTL4 rise sharply and scale with severity.
GKN1 and TFF1 don't move — the collapse reported in the literature is from gastric *cancer*
tissue, not infected mucosa. Atrophy appears only at intestinal metaplasia, where PGC,
MUC5AC and ATP4B drop.

So the arms split by stage: LCN2/CXCL8 flag active infection, PGC/MUC5AC/ATP4B flag
progression — the distinction that carries cancer risk.

> **Limits:** one cohort, one array, 8 genes chosen in advance, no significance testing.
> Small effects are unresolved, not null.

## Next step

Genome-wide differential expression across all ~50,000 probes with FDR correction,
rather than 8 genes chosen in advance.

## Data source
- [GSE60427](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE60427) — gastric biopsies, Bhutan and Dominican Republic cohorts (GEO)
- [Human Protein Atlas](https://www.proteinatlas.org/) (proteinatlas.org), CC BY-SA 4.0

