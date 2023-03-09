# Project on the course "Introduction to Data analysis", MIPT 2022
# Single - cell
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
1. Removal of outliers, standardization of data
2. Finding variable features (which means that they carry information)
3. Dimension reduction using linear Methods (PCA)
4. Projection into two-dimensional space using UMAP
5. Clustering
6. Definition of clusters by markers and annotation.


## Results
1. When filtering the data, we selected those genes whose total expression is nonzero (> 250 and < 5000) and the most variable. There are 2000 genes left.
2. There is often no correct answer regarding which clusters are in the data. But in this case, we can use the knowledge from biology since we know the markers for biological sets, that is, for cells that physically and biologically perform different functions. To control processing, we visualize the expression of genes corresponding to only one type of cell (for example, LYZ genes, CD14 (markers of macrophages and monocytes), CD8A - a marker for CD8+T cells, and so on). All genes typical for specific cells are recorded in the cluster_assignment dictionary.
![umap](https://user-images.githubusercontent.com/98456969/222129773-74d9d39e-1465-48ba-b7f5-aed813393b26.png)
On the obtained graphs, it is possible to highlight the areas where these markers are expressed. It can also be noted that approximately the same regions are marked for genes corresponding to the same cell types. At the same time, different markers highlight different areas, which suggests that clustering is appropriate in our case.

3. When divided into 9 clusters, a group of NK cells (cluster 6, partially 9), Mk (cluster 8), CD4+ memory cells and naive cells (cluster 3), CD14 monocytes (presumably cluster 5), FCGR3A+ monocytes (cluster 1), B cells (cluster 4) can be distinguished. However, it did not work out to divide exactly into 9 of our cell types, which is logical since the ratio of different cell types in the blood is not the same.
![Merged_document](https://user-images.githubusercontent.com/98456969/222130655-32972cf7-127a-488c-ae05-88c666c7077a.png)

## Conclusion
Thus, in the case of single-cell RNA seq analysis, based on known patterns, it is possible to determine the naturalness of clustering. Moreover, finding clusters in which only one characteristic gene is expressed makes it possible to decide on the type of cells it belongs to.

## In repo
* In the archive files: genes.tsv, barcodes.tsv, matrix.mtx 
* In notebook there is data analysis project
