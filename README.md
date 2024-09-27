
# Data Description
This repository presents the results of the overlap analysis between various platforms of Illumina probes (HM450, EPIC, MSA) and different versions of CoRSIV-like regions (ESS, SIV, CoRSIVs). 

**TLDR:**
- CoRSIV region coordinates are in **cleaned_data/regions/corsiv_regions_autosome_padded.bed**.
- Control region coordinates are in **cleaned_data/regions/control_regions_all.bed**.
- HM450, EPIC, MSA, EPIC+HM450, EPIC+HM450+MSA probes overlapping with CoRSIVs are under directory **cleaned_data/probes**.
- **data_summary/corsiv_annotated_manifest.csv** includes probe annotations for EPIC and HM450 probes overlapping with CoRSIVs.
- EPIC+HM450 probes overlapping with control regions are in **cleaned_data/probes/control_HM450_EPIC_probes_all.bed**.


All coordinates follow 0-based start and 1-based end BED file convention, and is based on hg38.



## Illumina probe data
- **cleaned_data/illumina/EPIC.clean.bed:** BED file containing all EPIC probes on chromosomes 1-22.
- **cleaned_data/illumina/HM450.clean.bed:** BED file containing all HM450 probes on chromosomes 1-22.
- **cleaned_data/illumina/MSA.clean.bed:** BED file containing all MSA probes on chromosomes 1-22.
- **cleaned_data/illumina/HM450_EPIC.clean.bed:** BED file containing all EPIC and HM450 probes on chromosomes 1-22.
- **cleaned_data/illumina/HM450_EPIC_MSA.clean.bed:** BED file containing all EPIC+HM450+MSA probes on chromosomes 1-22. 

First three columns are CpG_chr, CpG_beg, CpG_end, representing genomic coordinate for the target probe. Genome version is hg38. Each probe is 2bp wide. Multiple probe IDs referring to the same region are merged into one, with distinct IDs listed in the fourth column. Probes overlapping across versions are merged into one. Processing carried out to generate the above files can be found in **probe_overlap.ipynb**.


## CoRSIV-like region and Control regions
- **input_data/ME.hg38.bed:** BED file for ME regions, from Table S3 of Silver & Kessler, 2015 **[1]** (input_data/SIV-2015.xlsx).
- **input_data/SIV.hg38.bed:** BED file for SIV regions, from Table S9 of Van Baak, 2018 **[2]** (input_data/ESS-2018.xlsx).
- **input_data/ESS.hg38.bed:** BED file for ESS regions, from Table S7 of Van Baak, 2018 **[2]** (input_data/ESS-2018.xlsx).
- **input_data/corsiv2019.txt:** BED file for CoRSIV regions, from Table S3 of Gunasekara, 2019 **[3]** (input_data/CoRSIV-2019.xls).
- **cleaned_data/regions/corsiv_regions_autosome_padded.bed:** Union of all ME, SIV, ESS and CoRSIV regions. Overlapping regions are merged into one single region. Regions that are smaller than 200 bp or not multiples of 100 bp are padded to the nearest hundred bp, with equal padding on both sides.
- **cleaned_data/regions/control_regions_all.bed:** 10 sets of control regions (N = 103,880) generated to be mapped to CoRSIV regions (N = 10,388) based on chromosome, CpG density, gene proximity, and number of EPIC/HM450 probes. Each individual set is also listed in **cleaned_data/regions/control_regions_N.bed**, for N = 1 to 10. Comparison of features between CoRSIVs and control regions are listed in **data_summary/corsiv_control_matching.csv**.

First three columns are region_chr, region_beg, region_end, representing genomic coordinate for the target region. Fourth and fifth columns represent region ID. Processing carried out to generate the above files can be found in **probe_overlap.ipynb**.

## CoRSIV and Control Probes
- **cleaned_data/probes/corsiv_HM450_probes.bed:** BED file containing all HM450 probes overlapping with CoRSIVs.
- **cleaned_data/probes/corsiv_EPIC_probes.bed:** BED file containing all EPIC probes overlapping with CoRSIVs.
- **cleaned_data/probes/corsiv_MSA_probes.bed:** BED file containing all MSA probes overlapping with CoRSIVs.
- **cleaned_data/probes/corsiv_HM450_EPIC_probes.bed:** BED file containing all EPIC and HM450 probes overlapping with CoRSIVs.
- **cleaned_data/probes/corsiv_HM450_EPIC_MSA_probes.bed:** BED file containing all EPIC, HM450 and MSAprobes overlapping with CoRSIVs.
- **cleaned_data/probes/control_HM450_EPIC_probes_all.bed:** BED file containing all EPIC and HM450 probes overlapping with 10 sets of control regions. Each individual set is also listed in **cleaned_data/probes/control_HM450_EPIC_probes_N.bed:**, for N = 1 to 10.

First four columns are probe_chr, probe_beg, probe_end and probe_id. The remaining four columns are region_chr, region_beg, region_end and region_id. Processing carried out to generate the above files can be found in **probe_overlap.ipynb**.


## Results
The overlap statistics are stored in **data_summary/illumina_probe_overlap_summary.xlsx**, with corresponding code in **probe_overlap.ipynb**.
- **Table 1:** Number of probes on chromosomes 1-22 for each Illumina Platform: HM450, EPIC, MSA, HM450 U EPIC (all probes on EPIC and/or HM450), and HM450 U EPIC U MSA (all probes on all three platforms).
- **Table 2:** Number of regions in each CoRSIV-like region: ME, SIV, ESS, CoRSIVs, and Union (all CoRSIV-like regions).
- **Table 3:** Number of probes overlapping with CoRSIV-like regions, broken down by platform.
- **Table 4:** Percentage of probes overlapping with CoRSIV-like regions, broken down by platform.
- **Table 5:** Number of CoRSIV-like regions overlapping with at least one probe, broken down by platform.
- **Table 6:** Percentage of CoRSIV-like regions overlapping with at least one probe, broken down by platform.

**data_summary/corsiv_annotated_manifest.csv** includes probe annotations for EPIC and HM450 probes overlapping with CoRSIVs.
  
## Notes

Illumina probe annotations are sourced from [Zhou Lab InfiniumAnnotation](https://zwdzwd.github.io/InfiniumAnnotation) or official Illumina website.

Please download all files below before running the code in **probe_overlap.ipynb**: [HM450 GenCode Annotation](https://github.com/zhou-lab/InfiniumAnnotationV1/raw/main/Anno/HM450/HM450.hg38.manifest.gencode.v36.tsv.gz), [EPIC GenCode Annotation](https://github.com/zhou-lab/InfiniumAnnotationV1/raw/main/Anno/EPIC/EPIC.hg38.manifest.gencode.v36.tsv.gz), [MSA GenCode Annotation](https://github.com/zhou-lab/InfiniumAnnotationV1/raw/main/Anno/MSA/MSA.hg38.manifest.gencode.v41.tsv.gz), [HM450 manifest](https://webdata.illumina.com/downloads/productfiles/humanmethylation450/humanmethylation450_15017482_v1-2.csv), [EPIC UCSC Annotation](https://webdata.illumina.com/downloads/productfiles/methylationEPIC/infinium-methylationepic-v-1-0-b5-manifest-file-csv.zip), [MSA UCSC Annotation](https://support.illumina.com/content/dam/illumina-support/documents/downloads/productfiles/infiniummethylationscreening/MSA-48v1-0_20102838_A1.csv).

## References
**[1]** Silver MJ, Kessler NJ, Hennig BJ, Dominguez-Salas P, Laritsky E, Baker MS, Coarfa C, Hernandez-Vargas H, Castelino JM, Routledge MN, Gong YY, Herceg Z, Lee YS, Lee K, Moore SE, Fulford AJ, Prentice AM, Waterland RA. Independent genomewide screens identify the tumor suppressor VTRNA2-1 as a human epiallele responsive to periconceptional environment. Genome Biol. 2015 Jun 11;16(1):118. doi: 10.1186/s13059-015-0660-y. PMID: [26062908](https://pubmed.ncbi.nlm.nih.gov/26062908/); PMCID: PMC4464629.

**[2]** Van Baak TE, Coarfa C, Dugué PA, Fiorito G, Laritsky E, Baker MS, Kessler NJ, Dong J, Duryea JD, Silver MJ, Saffari A, Prentice AM, Moore SE, Ghantous A, Routledge MN, Gong YY, Herceg Z, Vineis P, Severi G, Hopper JL, Southey MC, Giles GG, Milne RL, Waterland RA. Epigenetic supersimilarity of monozygotic twin pairs. Genome Biol. 2018 Jan 9;19(1):2. doi: 10.1186/s13059-017-1374-0. PMID: [29310692](https://pubmed.ncbi.nlm.nih.gov/29310692/); PMCID: PMC5759268.

**[3]** Gunasekara CJ, Scott CA, Laritsky E, Baker MS, MacKay H, Duryea JD, Kessler NJ, Hellenthal G, Wood AC, Hodges KR, Gandhi M, Hair AB, Silver MJ, Moore SE, Prentice AM, Li Y, Chen R, Coarfa C, Waterland RA. A genomic atlas of systemic interindividual epigenetic variation in humans. Genome Biol. 2019 Jun 3;20(1):105. doi: 10.1186/s13059-019-1708-1. PMID: [31155008](https://pubmed.ncbi.nlm.nih.gov/31155008/); PMCID: PMC6545702.

**[4]** Gunasekara CJ, MacKay H, Scott CA, Li S, Laritsky E, Baker MS, Grimm SL, Jun G, Li Y, Chen R, Wiemels JL, Coarfa C, Waterland RA. Systemic interindividual epigenetic variation in humans is associated with transposable elements and under strong genetic control. Genome Biol. 2023 Jan 12;24(1):2. doi: 10.1186/s13059-022-02827-3. PMID: [36631879](https://pubmed.ncbi.nlm.nih.gov/36631879/); PMCID: PMC9835319.
