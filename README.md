# GWAS-pipeline  
GWAS pipeline requires .bed, .bim, and .fam input files.  
To complete PCA analysis, hapmapdata and bmerge data(bed, bim, and fam) will be required  
For final imputation, HRC-1000G-check-bim.pl (http://www.well.ox.ac.uk/~wrayner/tools/) is requred,additionally for this tool to be fully functional, the unzipped tab delimited HRC reference is required (http://www.haplotype-reference-consortium.org/site).      
Hapmapdata and bmerge data for the test data for hg19 is hosted on our github  

Intallation of PLINK (https://www.cog-genomics.org/plink2/) is required.   
Python modules used in pipleine: pandas, matplotlib, os, sys, numpy, Pandas, matplotlib, and numpy must be installed on your system.  
Perl modules used in "HRC imputation": strict, warnings, Getopt::Long, IO::Uncompress::Gunzip, and Term::ReadKey must be installed on your system.  


# To run the program, enter "python gwas-pipelineQC.py file_name pop_data_for_PCA_plots bmerge_data HRC_reference"  

Example: python gwas-pipelineQC.py testdata pop_HM3_hg19_forPCA.txt HM3_ASN_CEU_YRI_Unrelated_hg19_noAmbig  HRC.r1-1.GRCh37.wgs.mac5.sites.vcf

Note. When entering the file name and bmerge data, extentions should not be entered


The file containing the pop data for PCA plots should be similar to the .fam input file.
Except in row 1 you should include the population data, also data should be tab delimited.
For example, it should read: POPULATION FID IID (other info from .fam file)

PCA plots will only be created for datasets containing ASN, CEU, and YRI as the populations being tested for.
If there are any deviations from these populations, changes will need to be made to the code.
GWAS points are assumed to be any point that isn't already labeled from the pop data for PCA plots file.

Other options include IBD relatedness and number of standard deviations for the heterozygosity check  
If you do not include these options the defaults will utilized



Output Information  
---Step1: Sex Check QC---  
---Step2: SNP call rate---  
Step2_0: filters SNPS with <99% call rate QC  
Step2_1: unfiltered SNP call rate graph data  
Step2_2: filtered SNP call rate graph data  
---Step3: Person Call rate---  
Step3_0: filters persons with standard 0.1 threshold QC  
Step3_1: unfiltered person call rate graph data  
Step3_2: filtered person call rate graph data  
---Step4: Hardy-Weinberg---  
Step4_0: Hardy-Weinberg QC  
Step4_1: Hardy-Weinberg stats  
---Step5: ---  
Step5_0: Prune.in: filtered SNPs below r^2 theshold of 0.2, prune.out: filterted SNPs above threshold    
Step5_1: Heterozygosity check   
---Step6: ---  
Step6_0: Generates pairwise IBS  
Step6_1: Filters related individuals  
---Step7: ---  
Step7_0: Heterozygosity check      
Step7_1: Filters outliers      
---Step8: ---  
Step8_0: Generates missing SNPs from HAPMAP and QC files to be merged, filters SNPs that are missing     
Step8_1: filters SNPs that are missing   
Step8_2: merged genotypes  
Step8_3: filtered SNPs for pca  
Step8_4:  
Step8_5:  
