
# Data Description
Deposits the results showing how different platforms of Illumina probes (HM450, EPIC, MSA) overlap with different versions of SIV regions (ESS, SIV, CoRSIVs).

# Illumina Probe Data
**data/illumina/EPIC.hg38.txt:** bed file containing all EPIC probes on chr1-22\
**data/illumina/HM450.hg38.txt:** bed file containing all HM450 probes on chr1-22\
**data/illumina/MSA.hg38.txt:** bed file containing all MSA probes on chr1-22\
**data/illumina/epic_hm450.txt:** bed file containing all EPIC and HM450 probes on chr1-22, union by regions, probe coordinates that overlap across versions are merged into one probe\
**data/illumina/epic_hm450_msa_union.txt:** bed file containing all EPIC+HM450+MSA probes on chr1-22, union by regions, probe coordinates that overlap across versions are merged into one probe\

# SIV region data
**data/SIV regions/ESS.hg38.bed:** bed file for ESS regions, from S7 of 2017 ESS paper (PMID:29310692; supplmentary_tables/ESS-2017.xlsx)\
**data/SIV regions/ME.hg38.bed:** bed file for ME regions, from S3 of 2015 SIV paper (PMID:26062908; supplmentary_tables/SIV-2015.xlsx)\
**data/SIV regions/SIV.hg38.bed:** bed file for SIV regions, from S9 of 2017 ESS paper (PMID:29310692; supplmentary_tables/ESS-2017.xlsx)\
**data/SIV regions/siv_all.bed:** following the convention of S18 of 2023 CoRSIV paper (PMID: 36631879; supplmentary_tables/CoRSIV-2023.xlsx), SIV and ME regions are combined and referred to as SIV regions\
**data/SIV regions/corsiv2019.txt:** bed file for CoRSIV regions, from S3 of 2019 CoRSIV paper (PMID: 31155008; supplmentary_tables/CoRSIV-2019.xls)\
**data/SIV regions/all_regions.bed:** union of all ESS, SIV, and CoRSIV regions\

# Result
Overlap statistics stored in **illumina_probe_overlap_summary.xlsx**, with code in **probe_overlap.ipynb**.

# Notes
Illumina probe annotations are from https://zwdzwd.github.io/InfiniumAnnotation.
