#  A workflow for single Cell RNA-seq data analysis
The analysis of scRNA-seq data can be divided into two steps:
* generated a count matrix for all the genes and all the cells of one individual
* data analysis based on this count matrix (imputation, clustering, differential expression)



Also, we will discuss techniques that generate the scRNA-data, such as single-cell isolation and library preparation. For the comparison of 6 popular techs, please see   [Ziegenhain et al. (2017)](<https://www.sciencedirect.com/science/article/pii/S1097276517300497>)



This documents will use publicly available datasets `PBMCs`, around 68k peripheral blood mononuclear cells.





![](http://ww1.sinaimg.cn/large/005SiqoKgy1g4x2fuzxi4j30tp0giaeq.jpg)

For the left panel, we will use [Cell Ranger](<https://support.10xgenomics.com/single-cell-gene-expression/software/pipelines/latest/what-is-cell-ranger>) to [process](<http://research.fhcrc.org/content/dam/stripe/sun/software/scRNAseq/scRNAseq.html>) scRNA data from 10x Genomics. Then, we will use [Seurat](<https://satijalab.org/seurat/v3.0/pbmc3k_tutorial.html>) R package to process the data analysis. 

