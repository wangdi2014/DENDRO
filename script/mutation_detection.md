# DENDRO mutation detection with GATK

 **DENDRO** uses the following approach in the original paper to generate the initial mutation profiles across genes and cells. We write [an example script](https://github.com/zhouzilu/DENDRO/blob/master/script/mutation_detection_mapreduce.sh) modified from one real data analysis. Just want to clarify that I am not an expert with GATK tool. However, given significant amount of tests and failures, the following pipeline works for DENDRO. See [HaplotypeCaller document](https://software.broadinstitute.org/gatk/documentation/tooldocs/3.8-0/org_broadinstitute_gatk_tools_walkers_haplotypecaller_HaplotypeCaller.php) for more information.


## Questions, Suggestions & Problems

If you have any questions or problems when using DENDRO or DENDROplan, please feel free to open a new issue [here](https://github.com/zhouzilu/DENDRO/issues). You can also email the maintainers of the corresponding packages -- the contact information is shown under Developers & Maintainers.


## Pipeline overview

Initial SNA detection is indeed one of the most important steps in DENDRO pipeline. As stated in the paper, we want to maximize the sensitivity of our detection at this moment. There will be  a lot of false positives calls, but they will be cleaned up in the clustering and pooling steps. Figure 4 shows the detection pipeline. User should check the [example script](https://github.com/zhouzilu/DENDRO/blob/master/script/mutation_detection_mapreduce.sh) together with this figure side-by-side.

<p align="center">
  <img src='https://raw.githubusercontent.com/zhouzilu/DENDRO/master/figure/Pkg_FIG-04.jpg' width='1000' height='600'>
  </p>

  **Figure 5.** A flowchart outlining the procedures of mutation detection from fastq to final GVCF using GATK [ERC GVCF approach](https://gatkforums.broadinstitute.org/gatk/discussion/3893/calling-variants-on-cohorts-of-samples-using-the-haplotypecaller-in-gvcf-mode). The number on the most right corresponding to the steps in the shell script.
  
  
Due to great number of cells, traditional way of calling variants sample by sample is extremely slow. Luckily, GATK has ERC GVCF mode, which utilize a map-reduce like approach. Please check the details [here](https://gatkforums.broadinstitute.org/gatk/discussion/3893/calling-variants-on-cohorts-of-samples-using-the-haplotypecaller-in-gvcf-mode). Our script is built upon ERC GVCF mode togehter with the [variant detection best approach on RNAseq data](https://gatkforums.broadinstitute.org/gatk/discussion/3892/the-gatk-best-practices-for-variant-calling-on-rnaseq-in-full-detail).

Example script is attached [here](https://github.com/zhouzilu/DENDRO/blob/master/script/mutation_detection_mapreduce.sh).

## Citation

Please cite DENDRO.

* **DENDRO**: [no link yet](https://doi.org/10.1093/bioinformatics/bty057)
<br>
  Genetic Heterogeneity Profiling by Single Cell RNA Sequencing ([GitHub](https://github.com/zhouzilu/DENDRO))

## Developers & Maintainers

* [Zilu Zhou](https://statistics.wharton.upenn.edu/profile/zhouzilu/) (zhouzilu at pennmedicine dot upenn dot edu)
  <br>
  Genomics and Computational Biology Graduate Group, University of Pennsylvania

* [Nancy R. Zhang](https://statistics.wharton.upenn.edu/profile/nzh/) (nzh at wharton dot upenn dot edu)
  <br>
  Department of Statistics, University of Pennsylvania
