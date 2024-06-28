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

  1. [**Comparison of Performance of Data Imputation Methods for Numeric Dataset**](https://www.tandfonline.com/doi/full/10.1080/08839514.2019.1637138)

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

  Appropriately dealing with missing values is important and challenging task because it requires i) careful examination of all instances of data to identify **pattern of missingness in the data (Completely at Random (MCAR), Missing at Random (MAR), and Not Missing at Random (NMAR))** and ii) clear understanding of different imputation techniques.

  2. [**Missing traffic data: comparison of imputation methods**](https://ietresearch.onlinelibrary.wiley.com/doi/full/10.1049/iet-its.2013.0052)

  Generally, these missing data imputation methods can be categorised into three kinds:
  
    - prediction methods
    - interpolation methods
    - statistical learning methods.
    
  To assess their performance, these methods are compared from different aspects in this paper, including **reconstruction errors**, **statistical behaviours** and **running speeds**.
  

- 20/06/2024

  Normalized Root Mean Square Error (NRMSE) : scales are different for different features of the dataset. Once NRMSE is calculated for each variable in the dataset then Mean of NRMSE is calculated for the dataset and is used as a measure to assess performance of the imputation methods ... MNAR is often considered as worst missing type as it may lead to biased result whereas MCAR and MAR might lead to loss of statistical power [1](https://www.tandfonline.com/doi/full/10.1080/08839514.2019.1637138)

  Basically, NRMSE is calculating the difference between imputed value and the normalized true value.
 
  The task of the data set is not necessary to be classfication, that is, it could also be regression, clustering.

- 24/06/2024

  Problems should be more practical. (Think: Why calculate the accuracy of imputed values? How could it help improving model performance? Maybe introducing Deep Learning?)

- 27/06/2024
  Random forest can not only impute missing values by starting from features with least missing values, but can also be applied to prediction after imputing value.
  The problem is: will the machine learning model be affected by the values imputed using the same ML model? I think it depends on how many missing values are there, and what type of missing they are.
  * If there is high proportion (over 50%?) of missing values
  * 
- 28/
  Missing At Random (MAR)
  MAR data occurs when the probability of data being missing depends only on the observed data and not on the missing data itself. In other words, the missingness can be explained by variables for which you have complete information. There is a pattern in the missing values, but this pattern can be explained by other observed variables.
  
  Example: In a survey, younger respondents might be less likely to answer certain questions. If the missingness is related to age (which is recorded) but not to the specific question being asked, the data is MAR.

  How to handle?

  1. Maximum Likelihood Estimation (MLE)
Example: In a clinical trial, some patients drop out due to side effects, and the dropout is related to recorded baseline characteristics like age and initial health status.

Application:

Step 1: Specify a likelihood function that includes the observed data and the missing data mechanism.
Step 2: Use an algorithm (e.g., Expectation-Maximization) to estimate the parameters that maximize the likelihood function.
Step 3: Use these parameter estimates to make inferences about the population.

  2. Inverse Probability Weighting
[Review of inverse probability weighting for dealing with missing data](https://doi.org/10.1177/0962280210395740)

"Almost all datasets collected for medical or social research are missing some information that was intended to be collected. This complicates their analysis. A commonly used approach is to exclude individuals with missing data. However, estimates obtained from this ‘complete-case’ (CC) analysis may be biased if the excluded individuals are systematically different from those included. Inverse probability weighting (IPW) is one of several methods that can reduce this bias. In this method, complete cases are weighted by the inverse of their probability of being a complete case."


  Missing Not At Random (MNAR)
  MNAR occurs when the missingness of data is related to the unobserved data itself, which is not included in the dataset. This type of missing data has a specific pattern that cannot be explained by observed variables.
  
  Example: In a survey about income, individuals with very high or very low incomes might be less likely to report their earnings. This results in missing data that is systematically related to the income variable itself
  
  Understanding the type of missing data is crucial because it determines the appropriate strategy for handling missing values and ensuring the integrity of statistical analyses. Techniques such as handling missing values, how to handle missing values, how to fill missing values in dataset, and missing value imputation are essential for mitigating biases and ensuring robust results in scenarios such as sentiment analysis python, python sentiment analysis, and how to do sentiment analysis in python.
