# Project on the course "Introduction to Data analysis", MIPT 2022
## Authors:
* Marfa Zakirova
* Sergeeva Julia
* Elizaveta Bogdan
## Introduction 
Single - cell analysis involves the consideration of expression profiles from certain genes by RNA. There is a reading of free RNA molecules in the cell: for each such molecule, a small technical sequence unique to each cell (barcode) is preserved, in addition to this, the unique identifier of each RNA molecule is preserved  $\Rightarrow$ A complete quantitative representation of certain RNAs in cells is obtained. Thus, the typical data that we get after one experiment is a large table where the rows are cells and the columns are genes, and in the cell $(i,j)$
 contains a number that shows the amount of RNA of gene $j$ in cell $i$.

## Aim
We will use the data on RNA sequencing of 2700 peripheral mononuclear blood cells. First, we want to identify clusters of gene expression characteristic of specific cells. For example, let's say we know that cells A are characterized by the expression of genes 1 and 2, but not 3 and 4, so we want our model to cluster 1 and 2 well together but separately from 3 and 4. Further, when analyzing cluster 1-2, it may contain data on the expression of gene x; thus, it will be possible to find new cell markers. Also, by finding clusters in which only one characteristic gene is expressed, it is possible to determine the type of cells to which it belongs.


## Workflow
* Removal of outliers, standardization of data
* Finding variable features (which means that they carry information)
* Dimension reduction using linear Methods (PCA)
* Projection into two-dimensional space using UMAP
* Clustering
* Definition of clusters by markers and annotation.


## Results
1. When filtering the data, we selected those genes whose total expression is nonzero (> 250 and < 5000) and the most variable. There are 2000 genes left.
2. Even though we selected highly variable genes, they may be correlated, so we used PCA.
![pca](https://user-images.githubusercontent.com/98456969/222127907-68a062f0-9e81-4549-8899-ff679dc77f8f.png)


## In repo
* In the archive files: genes.tsv, barcodes.tsv, matrix.mtx 
* In notebook there is data analysis project
