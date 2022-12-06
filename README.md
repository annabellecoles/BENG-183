# BENG-183
**What Is K-Means Clustering?**

K-means clustering is an unsuperivised machine learning algorithm used to cluster data. K-means clustering groups datapoints into k# of clusters centered around centroids (the center of each cluster). 

**Why is k-means clustering important?**



**Algorithm**

We iterate over the algorithm until we reach our desired results or convergence occurs.
Convergence is where the results of the algorithm no longer change. Aka. once centroid and cluster re-assignment no longer changes. 
Convergence
Determines when iteration ceases. Convergence occurs when there is no longer any change in cluster assignment and centroid location. 



<img src="https://user-images.githubusercontent.com/59674595/205348356-2c56f50a-6a37-4801-bba8-80fc99be3ca1.png" width="400" height="500">

TODO citation: Statistics for Machine Learning,by Pratap Dangeti, Released July 2017 https://www.oreilly.com/library/view/statistics-for-machine/9781788295758/c71ea970-0f3c-4973-8d3a-b09a7a6553c1.xhtml

Advantages
 
Simple algorithm 
Time complexity: linear 

Disadvantages

**Applications**

K-means Clustering is a very useful and applicable algorithm both in biology and other fields. For example, in biology, k-means clustering can be applied to scRNA-seq data to cluster the data into cell types and reveal patterns in the data. Furthermore, k-means clustering can be used in gene co-expression networks to reveal relationships between differnet genes and their expression. Outside of biology, k-means clustering is an algorithm that can be used in marketing to cluster customers, and in geographic analysis can be used to cluster an area into different regions depending on factors such as crime, average household size, etc. 

CASE STUDY: Using K-means clustering to identify cell types in scRNA-seq data 

<details>
<summary>1. Pre-processing</summary>
<br>
First, the quality of each read needs to be checked. To check the quality of reads, a tool called FASTQC is used. FASTQC provides a report on the quality of the data, and if the data is deemed good quality the data is now ready to be aligned to the reference genome. There are many tools to perform alignment, one of those is STAR (Spliced Transcripts Alignment to a Reference). The final step of processing involves counting the number of reads that map to each gene. STAR stores the aligned data in a BAM file, there are tools such as featureCounts which take in a BAM file (the alignment output) and output a count matrix (number of reads per gene). (https://hbctraining.github.io/Intro-to-rnaseq-hpc-O2/lessons/05_counting_reads.html)
</details>

<details>
<summary>2. Normalization</summary>
<br>
The data must be normalized prior to clustering to remove any bias introduced into the data by different factors including, but not limited to, gene length and GC content. One useful tool to normalize scRNA-seq data is scTransform, a function in Seurat. https://blog.bioturing.com/2022/01/27/a-guide-to-scrna-seq-normalization/#:~:text=What%20is%20scRNA%2DSeq%20Normalization,level%20of%20biological%20gene%20expression. 
</details>

<details>
<summary>3. Dimensionality Reduction</summary>
<br>
Once the data has been normalized, the data must be dimensionaly reduced. This is a necessary step prior to clustering because k-means clustering measures the eucladian distance between data points, and in high-dimensionality space, this is very difficult to measure. One type of dimensionality reduction is PCA (principal component analysis). After performing dimensionality reduction, each cell is represented by a single data point and is mapped to a graphical location. 
</details>


<details>
<summary>4. Clustering</summary>
<br>
At last, the data is ready to be clustered (using k-means clustering)! Clustering results depend on the value of k chosen. K represents the number of clusters. First, each centroid (the center of each cluster) is randomly assigned to the position of a data point. Next, the distance between each centroid and each data point is measured. Then, the data points are assigned to the cluster in which they are closest to (the smallest eucladian distance between a datapoint and a centroid). The algorithm continues until convergence is achieved. See the algorithm section for a more detailed description of how the algorithm works. The final output of the algorithm is the dataset clustered into k # of clusters with each unique data point assigned to a cluster.
</details>

**Python Packages**
