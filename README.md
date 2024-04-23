
# Data Description
This repository presents the results of the overlap analysis between various platforms of Illumina probes (HM450, EPIC, MSA) and different versions of CoRSIV-like regions (ESS, SIV, CoRSIVs).

## Illumina probe data
- **data/illumina/EPIC.hg38.txt:** BED file containing all EPIC probes on chromosomes 1-22.
- **data/illumina/HM450.hg38.txt:** BED file containing all HM450 probes on chromosomes 1-22.
- **data/illumina/MSA.hg38.txt:** BED file containing all MSA probes on chromosomes 1-22.
- **data/illumina/epic_hm450.txt:** BED file containing all EPIC and HM450 probes on chromosomes 1-22. Probes overlapping across versions are merged into one.
- **data/illumina/epic_hm450_msa_union.txt:** BED file containing all EPIC+HM450+MSA probes on chromosomes 1-22. Overlapping probes across versions are merged into one.

## CoRSIV-like region data
- **data/SIV regions/ESS.hg38.bed:** BED file for ESS regions, from Table S7 of Van Baak, 2018 **[2]** (supplmentary_tables/ESS-2018.xlsx).
- **data/SIV regions/ME.hg38.bed:** BED file for ME regions, from Table S3 of Silver & Kessler, 2015 **[1]** (supplmentary_tables/SIV-2015.xlsx).
- **data/SIV regions/SIV.hg38.bed:** BED file for SIV regions, from Table S9 of Van Baak, 2018 **[2]** (supplmentary_tables/ESS-2018.xlsx).
- **data/SIV regions/siv_all.bed:** following the convention of Table S18 of Gunasekara, 2023 **[4]** (supplmentary_tables/CoRSIV-2023.xlsx), SIV and ME regions are combined and referred to as SIV regions.
- **data/SIV regions/corsiv2019.txt:** BED file for CoRSIV regions, from Table S3 of Gunasekara, 2019 **[3]** (supplmentary_tables/CoRSIV-2019.xls).
- **data/SIV regions/all_regions.bed:** Union of all ESS, SIV, and CoRSIV regions. Overlapping regions are merged.

## Results
The overlap statistics are stored in **illumina_probe_overlap_summary.xlsx**, with corresponding code in **probe_overlap.ipynb**.
- **Table 1:** Number of probes on chromosomes 1-22 for each Illumina Platform: HM450, EPIC, MSA, EPIC U HM450 (all probes on EPIC and/or HM450), and Union (all probes on all three platforms).
- **Table 2:** Number of regions in each CoRSIV-like region: CoRSIVs, ESS, SIV, and Union (all CoRSIV-like regions).
- **Table 3:** Number of probes overlapping with CoRSIV-like regions, broken down by platform and region.
- **Table 4:** Percentage of probes overlapping with CoRSIV-like regions, broken down by platform and region.
- **Table 5:** Number of CoRSIV-like regions overlapping with at least one probe, broken down by platform and region.
- **Table 6:** Percentage of CoRSIV-like regions overlapping with at least one probe, broken down by platform and region.
  
## Notes
Illumina probe annotations are sourced from [InfiniumAnnotation](https://zwdzwd.github.io/InfiniumAnnotation).

## References
**[1]** Silver MJ, Kessler NJ, Hennig BJ, Dominguez-Salas P, Laritsky E, Baker MS, Coarfa C, Hernandez-Vargas H, Castelino JM, Routledge MN, Gong YY, Herceg Z, Lee YS, Lee K, Moore SE, Fulford AJ, Prentice AM, Waterland RA. Independent genomewide screens identify the tumor suppressor VTRNA2-1 as a human epiallele responsive to periconceptional environment. Genome Biol. 2015 Jun 11;16(1):118. doi: 10.1186/s13059-015-0660-y. PMID: [26062908](https://pubmed.ncbi.nlm.nih.gov/26062908/); PMCID: PMC4464629.

**[2]** Van Baak TE, Coarfa C, Dugué PA, Fiorito G, Laritsky E, Baker MS, Kessler NJ, Dong J, Duryea JD, Silver MJ, Saffari A, Prentice AM, Moore SE, Ghantous A, Routledge MN, Gong YY, Herceg Z, Vineis P, Severi G, Hopper JL, Southey MC, Giles GG, Milne RL, Waterland RA. Epigenetic supersimilarity of monozygotic twin pairs. Genome Biol. 2018 Jan 9;19(1):2. doi: 10.1186/s13059-017-1374-0. PMID: [29310692](https://pubmed.ncbi.nlm.nih.gov/29310692/); PMCID: PMC5759268.

**[3]** Gunasekara CJ, Scott CA, Laritsky E, Baker MS, MacKay H, Duryea JD, Kessler NJ, Hellenthal G, Wood AC, Hodges KR, Gandhi M, Hair AB, Silver MJ, Moore SE, Prentice AM, Li Y, Chen R, Coarfa C, Waterland RA. A genomic atlas of systemic interindividual epigenetic variation in humans. Genome Biol. 2019 Jun 3;20(1):105. doi: 10.1186/s13059-019-1708-1. PMID: [31155008](https://pubmed.ncbi.nlm.nih.gov/31155008/); PMCID: PMC6545702.

**[4]** Gunasekara CJ, MacKay H, Scott CA, Li S, Laritsky E, Baker MS, Grimm SL, Jun G, Li Y, Chen R, Wiemels JL, Coarfa C, Waterland RA. Systemic interindividual epigenetic variation in humans is associated with transposable elements and under strong genetic control. Genome Biol. 2023 Jan 12;24(1):2. doi: 10.1186/s13059-022-02827-3. PMID: [36631879](https://pubmed.ncbi.nlm.nih.gov/36631879/); PMCID: PMC9835319.
