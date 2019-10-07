---
title: "Determining the number of cell types present in a tumor sample"

author: "Jane Merlevede"
date: "October 7, 2019"
layout: post
---


<section class="main-content">
<blockquote>
<p>Author: Jane Merlevede</p>
</blockquote>
<div id="context" class="section level2">
<h2>Context</h2>
<p>Deconvolution consists in solving the matrix factorization problem <span class="math inline">\(D=T*A\)</span>, including determining the dimensions of T and A matrices. The number of cell types is closely related to K, the number of columns in T and the numbers of rows in A: the number of cell types is at most K. In the ideal case where one captures only cell population signals, the number of cell types is exactly K.</p>
<p>In most cases however, in particular when using unsupervised approaches, the decomposition captures additional sources of variation, as for example technical bias, sequencing and analysis artifacts, gender or age of the individuals. In this case, the number of cell types is strictly less than K. To limit the presence of these extra sources, one can clean the data beforehand (i.e. to remove undesired signals, as described in the previous paragraph). This will make the number of cell types as close as possible from K. For example, in methylation data, it is common to remove or correct measurements (CpGs) that correlate with patient age or gender prior to any matrix factorization.</p>
</div>
<div id="strategies" class="section level2">
<h2>Strategies</h2>
<p>There are different strategies to select the number of components (and hence deduce the number of cell types). Most of them consist in testing a range of values for K and select the value that optimizes a defined criteria.</p>
<p>Using PCA, one can use the percentage of explained variance by selecting a number of components such that when increasing this number, the percentage of explained variance does not decrease significantly.</p>
<p>Using NMF and ICA, one can look at the stability of components through tens or hundreds of iterations by varying the initializations or/and bootstrapping the cases. Once the components have been extracted (K determined), it is possible to test their correlation with clinical or technical (ethnic group, tobacco exposure, batchs, experimenter, …) information if available, in order to identify if other sources of variability remain.</p>
<p>To confirm that a component is associated with a cell type, one can perform enrichment analysis or compare it with profiles of “pure” cell populations if such are available.</p>
</div>
</section>
