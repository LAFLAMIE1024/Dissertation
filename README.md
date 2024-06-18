# Dissertation
## Progress Document
This repo aims at documenting everything I do till I submit my dissertation.

## Working Diary

- 05/06/2024
  
  Read given references.
  
  Especially the survey.

  Clarify the aim: **Review available methods for classification and clustering with missing data, and illustrate some of them using both simulated and real datasets.**
  
  One specific objective would be to *test a plausible conjecture* that classification performance can be improved by first clustering the data and then using cluster-based imputation of missing values.

  Conjecture?

- 06/06/2024
  
  Search for practical filed that missing data issue involved in.
  (Field of interest: recommendation system)

  Searched some related articles.

  [**Key Issue: Users typically rate only a small fraction of all available items.**](https://dl.acm.org/doi/abs/10.1145/1835804.1835895)

- 18/06/2024

  Can't do RS system (need numerical, continuous data)

  - [**Comparison of Performance of Data Imputation Methods for Numeric Dataset**](https://www.tandfonline.com/doi/full/10.1080/08839514.2019.1637138)

  we comprehensively compare seven data imputation methods:
  
    - mean imputation
    - median imputation
    - kNN imputation
    - predictive mean matching
    - Bayesian Linear Regression (norm)
    - Linear Regression
    - non-Bayesian (norm.nob)
    - random sample
  
  We have used five different numeric datasets obtained from UCI machine learning repository for analyzing and comparing performance of the data imputation methods. Performance of the data imputation methods is 
  assessed using **Normalized Root Mean Square Error (RMSE)** method. The results of analysis show that kNN imputation method outperforms the other methods.

  It has also been found that performance of the data imputation method is independent of the dataset and percentage of missing values in the dataset.
  
  ...

  Appropriately dealing with missing values is important and challenging task because it requires i) careful examination of all instances of data to identify **pattern of missingness in the data (Missing at random, Missing not at random, missing completely at random )** and ii) clear understanding of different imputation techniques.

  - [**Missing traffic data: comparison of imputation methods**](https://ietresearch.onlinelibrary.wiley.com/doi/full/10.1049/iet-its.2013.0052)

  Generally, these missing data imputation methods can be categorised into three kinds:
  
    - prediction methods
    - interpolation methods
    - statistical learning methods.
    
  To assess their performance, these methods are compared from different aspects in this paper, including *reconstruction errors*, *statistical behaviours* and *running speeds*.
  

  

  
 
