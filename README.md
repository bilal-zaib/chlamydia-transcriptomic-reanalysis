# Cross-context reanalysis of host transcriptional responses to *Chlamydia trachomatis*

This repository contains the analysis notebook, manuscript, figures and citation library for a cross-study reanalysis of publicly available human RNA-seq datasets involving *Chlamydia trachomatis* infection and macrophage training.

The analysis identifies a conserved epithelial interferon/inflammatory response across independent infection contrasts, while showing that the broader transcriptional response depends strongly on cell identity, infection stage and cytokine context. Macrophage-training data are used as a mechanistic comparator, not as a pooled validation dataset.

## Repository contents

```text
.
├── README.md
├── DATA_AVAILABILITY.md
├── CITATION.cff
├── .gitignore
├── notebooks/
│   └── Chlamydia_GEO_reanalysis_Colab_v2.ipynb
├── manuscript/
│   ├── Chlamydia_transcriptomic_reanalysis_manuscript.pdf
│   ├── Chlamydia_transcriptomic_reanalysis_manuscript.docx
│   └── Chlamydia_transcriptomic_reanalysis_manuscript.md
├── figures/
│   ├── chlamydia_concordance_heatmap.png
│   └── chlamydia_validation.png
└── references/
    └── Chlamydia_transcriptomic_reanalysis_references.bib
```

## Data sources

The notebook downloads the processed supplementary files directly from the NCBI Gene Expression Omnibus (GEO). The repository does not redistribute GEO data files. See [`DATA_AVAILABILITY.md`](DATA_AVAILABILITY.md) for the complete accession list, source descriptions and data-use notes.

| GEO series | Biological context | Samples used in the reanalysis |
|---|---|---|
| [GSE228774](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE228774) | Primary human vaginal epithelial cells, mock versus *C. trachomatis* L2 infection | 3 mock, 3 infected |
| [GSE198272](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE198272) | Human endocervical epithelial cells, mock versus *C. trachomatis* L2 infection | 3 mock, 3 infected |
| [GSE180782](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE180782) | End1/E6E7 endocervical cells, mock versus L2 or B infection | 3 mock, 3 L2, 3 B |
| [GSE158814](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE158814) | HeLa cells infected with serovar E at 20 h or 44 h, with or without IFN-γ | 2 replicates per selected condition |
| [GSE242947](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE242947) | Human monocyte-derived macrophages trained with zymosan, depleted zymosan or β-glucan | 2 donors at 0, 1 and 3 h per ligand |

## Main analyses

The notebook performs the following steps:

1. Downloads supplementary files from GEO and records MD5 hashes.
2. Parses CLC spreadsheets and processed count files into gene-level matrices.
3. Performs descriptive quality control using library sizes, PCA and sample-correlation heatmaps.
4. Fits differential-expression models with PyDESeq2/DESeq2-style negative-binomial models.
5. Applies Benjamini–Hochberg correction to gene-level P values.
6. Compares infection-associated log2 fold changes across epithelial and HeLa contexts.
7. Defines a 549-gene core epithelial response significant and directionally consistent across four infection contrasts.
8. Performs preranked GSEA using Hallmark, Reactome, GO biological-process and prespecified innate-immunity gene sets.
9. Compares infection contrasts with macrophage-training contrasts without pooling the datasets.
10. Exports differential-expression tables, GSEA tables, concordance results, sample tables and a run log when executed in Colab.

## Reproducing the analysis

The notebook is designed for Google Colab.

1. Open [`notebooks/Chlamydia_GEO_reanalysis_Colab_v2.ipynb`](notebooks/Chlamydia_GEO_reanalysis_Colab_v2.ipynb) in Google Colab.
2. Run the installation cell.
3. Run the notebook from top to bottom.
4. Allow network access to NCBI GEO when prompted.
5. The notebook writes downloaded data under `/content/ct_reanalysis/data` and analysis outputs under `/content/ct_reanalysis/results`.
6. The final cell creates `ct_reanalysis_results.zip` for download from Colab.

The recorded notebook used random seed 42 and the following principal package versions:

- PyDESeq2 0.6.0
- GSEApy 1.3.2
- pandas 3.1.1
- NumPy 2.4.6
- SciPy 1.16.3
- statsmodels 0.15.0
- scikit-learn 1.6.1

Minor differences in package versions, GEO supplementary files or external gene-set libraries may change numerical outputs. The notebook records the downloaded-file hashes and software versions at runtime.

## Interpretation and scope

This is a cross-study reanalysis, not a pooled meta-analysis. The GEO series differ in cell type, serovar, infection time, IFN-γ exposure, sequencing platform, sample size and control structure. No cross-study batch correction was performed. The macrophage dataset measures ligand-trained macrophage states and should not be interpreted as a direct equivalent of epithelial infection.

The manuscript reports the notebook’s recorded results without adding unsupported mechanistic claims. In particular, pathway-level conclusions should be checked against the exported GSEA tables generated by the notebook rather than inferred from gene names alone.

## Manuscript

The manuscript is available in three formats:

- [PDF](manuscript/Chlamydia_transcriptomic_reanalysis_manuscript.pdf)
- [Word document](manuscript/Chlamydia_transcriptomic_reanalysis_manuscript.docx)
- [Markdown](manuscript/Chlamydia_transcriptomic_reanalysis_manuscript.md)

## Citation

If you use this repository or the reanalysis, cite the repository using [`CITATION.cff`](CITATION.cff) and cite the underlying GEO series relevant to your reuse. The complete Zotero-importable BibTeX library is in [`references/Chlamydia_transcriptomic_reanalysis_references.bib`](references/Chlamydia_transcriptomic_reanalysis_references.bib).

## License and third-party data

No license is asserted over the original GEO datasets or over third-party publications. Those materials remain subject to their original repository, publisher and author terms. Before adding a repository license, confirm the intended licensing status of the notebook, manuscript and figures with all contributors. The `.gitignore` file excludes downloaded GEO data and generated result directories from accidental commits.
