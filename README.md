# single cell RNA sequencing



## scRNA-seq研究历史

* first NGS single-cell transcripome analysis was published in 2009 (PMID: 19349980, Nat Mathods)
* advantages in available experimental tech and bioinformatic pipeline (PMID: 23685454, Nature)

## single-cell isolation tech

* limiting dilution - 1a
* micromanipulation (显微操作) - 1b
* flow-activated cell sorting (FACS) - 1c
* laser capture microdissection (激光捕获显微切割) - 1d
* microfluidic tech (微流体) - 1e
* rare circulating tumor cells - 1f

![](http://ww1.sinaimg.cn/large/005SiqoKly1g4mprrroenj31e01l3tct.jpg)

## scRNA-seq library preparation

### typical workflow - fig (1g)

1. Cell lysis (细胞溶解)
2. reverse into cDNA
3. second-strand synthesis
4. cDNA amplification (including SMART, 10×genomics, Anydeplete)

以`10 × genomics` 为例，简要描述cDNA扩增过程：
* 凝胶珠上事先固定特定DNA片段，包括：Barcode + UMI + PolyT
* Barcode用于区分凝胶珠或者细胞; UMI用于区分原始cDNA分子，区分基因片段重复还是duplication，以及区分真实的SNP位点还是PCR产生的突变。
* 10 × genomics仪器将单个细胞与单个凝胶珠通过油相混合起来，形成油包水小液滴。
* 接下来将细胞膜破掉，是其中mRNA发生逆转录反应，得到cDNA（注意此时每个cDNA分子都包含barcode和UMI）。
* 将所有带了标签的cDNA分子抽出来，加上接头，进行常规PCR扩增后在illumina上测序。

`基于UMI的方法不适用于allele-specific expression or isoform usage`
`smart-seq产生full-length transcripts，适用于alterative-splicing events and allele-specific expression using SNPs`
`10 × genomics可以一次得到大量细胞数据，但只能得到mRNA信息，大部分lncRNA丢失。`
`UMI很好地去除了duplication以及PCR引入的SNP位点，但对RNA质量要求较高，降解会引起5'端信息丢失`

## computational tools
* computational pipelines for handling raw data remain limited
* some companies provide software tools, such as 10 × genomics
* gold-standard tools have yet to be developed.

### processing the data

* fastqc: low-quality basese (3' end), adapter sequence
* trimmed UMIs prior to alingment
* alignment: BWA, STAR
* RNA-seQC: post-alignment summary stats (mapped reads, annotated exonic regions)
* reads are allocated to exonic, intronic, or intergenic
* only reads that map to exonic loci with high-quality are considered for generation gene expression matrix (cell × gene)
* normalization 
* cell type identification (PCA, t-SNE, LLE, Isomap)
* t-SNE is implemented in Cell Ranger pipeline (10 × genomics) and Seurat In R package.  


以上总结来自review : 
[PMID: 30089861](%3Cdiv%3Ehttps://www.nature.com/articles/s12276-018-0071-8%3C/div%3E)