# Data availability

The analyses in this repository use publicly available processed and supplementary files deposited in the NCBI Gene Expression Omnibus (GEO). No new biological samples were collected and no human participants were recruited for this reanalysis. The repository contains the analysis notebook and derived manuscript figures, but does not redistribute the original GEO supplementary files or raw sequencing data.

## GEO accessions

- **GSE228774** — cell type-intrinsic differences in the host transcriptome of *Chlamydia trachomatis*-infected primary human endocervical epithelial cells and vaginal epithelial cells. The reanalysis used mock and wild-type L2 conditions for three replicates per cell type. [NCBI GEO record](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE228774)
- **GSE198272** — *C. trachomatis* infection in human endocervical epithelial cells, including mock and L2-infected conditions. The reanalysis used three biological replicates per condition. [NCBI GEO record](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE198272)
- **GSE180782** — *C. trachomatis* infection of End1/E6E7 cells with mock, serovar L2 and serovar B conditions. The reanalysis used three biological replicates per condition. [NCBI GEO record](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE180782)
- **GSE158814** — genome-wide analysis of HeLa cells infected with *C. trachomatis* serovar E at 20 h and 44 h, including IFN-γ-conditioned samples. The reanalysis used the coding/mRNA count entries and two replicates per selected condition. [NCBI GEO record](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE158814)
- **GSE242947** — human monocyte-derived macrophages trained with zymosan, depleted zymosan or β-glucan and sampled at 0, 1 and 3 h. The reanalysis used two donor replicates per ligand/time condition. [NCBI GEO record](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE242947)

The source studies associated with these records should be cited when their data are reused. Their bibliographic records and DOIs are included in [`references/Chlamydia_transcriptomic_reanalysis_references.bib`](references/Chlamydia_transcriptomic_reanalysis_references.bib).

## Retrieval and provenance

The notebook retrieves GEO supplementary files during execution through the NCBI GEO FTP endpoints. It records the downloaded-file MD5 hashes in `run_log.json` when the notebook is run. The original notebook was configured to store downloaded files under `/content/ct_reanalysis/data` and derived outputs under `/content/ct_reanalysis/results` in Google Colab.

Because GEO records and supplementary files can be updated, reproducibility should be assessed using the accession numbers, file hashes and software versions recorded by the notebook run rather than by assuming that a current download is byte-identical to a previous download.

## Derived data and results

The notebook generates the following derived outputs when executed:

- `DE_*.csv` — differential-expression results for each contrast.
- `GSEA_*.csv` — preranked gene-set enrichment results.
- `cross_dataset_concordance.csv` — pairwise infection-contrast concordance.
- `celltype_difference_HVE_vs_HCEC.csv` — comparison of infection-associated fold changes between HVE and HCEC.
- `conserved_genes_core_contrasts.csv` — genes significant and directionally consistent across the four core epithelial contrasts.
- `validation_directional_check.csv` — directional validation of core genes in HeLa contrasts.
- `infection_vs_trained_concordance.csv` — comparison of infection and macrophage-training contrasts.
- `prespecified_pathway_NES.csv` and `prespecified_pathway_FDR.csv` — pathway-level results for the prespecified gene-set subset.
- `sample_table_*.csv` — sample metadata used in each analytical context.
- `run_log.json` — seed, file hashes, exclusions, package versions and model settings.

## Publication-ready statement

> All data analysed in this study are publicly available from the NCBI Gene Expression Omnibus under accession numbers GSE228774, GSE198272, GSE180782, GSE158814 and GSE242947. The study did not generate new biological samples. The analysis notebook and derived figures are available in the accompanying GitHub repository. Original GEO supplementary files and raw sequencing data are not redistributed and remain available under the terms of the NCBI GEO repository and the relevant source studies.
