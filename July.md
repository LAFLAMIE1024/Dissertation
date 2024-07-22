- 01/07/2024

  partial clustering?

  This blog,  [How to generate missing values?](https://rmisstastic.netlify.app/how-to/generate/misssimul#:~:text=Missing%20Completely%20At%20Random%20values,Bernoulli%20distribution%20of%20parameter%20perc) ,introduces a couple of different ways to generate MAR data.
  
- 03/07/2024

  The whole structure of handling missing data:
  * Select all rows with missing data
  * Determining their type (MAR, MCAR, MNAR)
  * Handle them according to their type, and there are many ways to deal with these missing entries:
      - Complete Analysis (may result in losing information, or lead to biased analysis)\
        but suitable for small proportion of data MCAR, which means that directly deleting them is not likely to cause huge impact on the analysis, and it is time efficient.
      - Treat the missingness as an indicator\
        Create a new binary feature indicating whether a value was missing. This can sometimes improve model performance\
(Mentioned in this blog [Effective Strategies for Handling Missing Values in Data Analysis](https://www.analyticsvidhya.com/blog/2021/10/handling-missing-value/) in section: How to Use “Missingness” as a Feature? )
      - Imputation
        * KNN imputation, Multiple imputation\
          Create several data sets rather than one filled with single imputed values.\
          Inefficient when it comes to large data set.
        * KDE + sample imputation\
          Figure out the distribution of observed data, and try to sample values from the estimated distribution and impute them.
        * Machine Learning Techniques\
          Use algorithms like Random Forest or XGBoost to predict missing values based on other features in the dataset.
  Then we can apply our statistical model or machine learning model on this preprocessed data set for prediction or classification.
  
- 04/07/2024

  Finding out if there is hidden correlation between variables by using random forest?
  
- 05/07/2024

  Missing data is not necessary of one type. It could be MAR and MNAR at the same time.
  Being metioned in this blog [Diagnosing Type of Missing Data (MCAR, MAR, MNAR)](https://www.reddit.com/r/AskStatistics/comments/17nigqk/diagnosing_type_of_missing_data_mcar_mar_mnar/), we can't do much about MCAR (deletion) and MNAR (better improve data set) as both of they usually do not provide further information of missingness. So what we are looking for is "the patterns in the missingness", and "do the **records where a given feature is missing** have a different distribution than the **records where the feature isn't missing**?"
    * If the answer to that question is a clear "yes", then that feature **isn't missing at random**.\
      What's the distribution of those records?
    * A clear "no" means the feature is missing completely at random.
    * If it's less clear then the feature can be likely said to be missing at random, but could also go either way.\
      It could also be the result of **multiple sources of missingness**.

  As data MCAR is not informative of missingness, it would be more practical to investigate data MAR and MNAR (?).

  The experiment can be conducted like:
    * Choose a real complete data set/simulated data set\
      - If real, Size? Number of features? Continuous or discrete feature?
      - If simulated, distribution (Gaussian? Gamma?)?
    * See the performance of existing machines learning model or clustering approach on this data set.
    * Remove some entries to create missing data.
    * Depending on the type of missing values created, try all methods mentioned above (3 July).\
      When it comes to imputation, **evaluate the accuracy of imputation**.
    * **See if the accuracy of classification/clustering algorithm is reachieved, or even improved after preprocessing**.
      Theoretically, records with missing values imputed can help reducing bias or provide more information for the classification model.
  
- 06/07/2024

  Imputations methods are limited. But the way of creating missing data could be various.
  "either **segmenting your data according to missingness** or **making it clear some other way**."
  
  * Clustering points (segmenting data) and handle missing value using cluster-based imputation -> somehow finding out pattern
  * [Use random forest for imputation](https://zhuanlan.zhihu.com/p/635931775)\
    ->  start from the feature with least missing values, which is our target column, and train the random forest on the non-missing part of the target column.\
    After that, we predict missing values in this target column using the other features as input.
  
  The algorithm iterates over all the features and fills them starting with the least missing ones (because the least accurate information is required to fill the least missing features). When filling in a feature (the sub-feature is used as a label value), the missing values of the other features are replaced with zeros, and for each regression prediction, the predicted value is put into the original feature matrix before continuing to fill in the next feature. Each time a regression is completed, the number of features with missing values is reduced by one, so that fewer and fewer features need to be filled with zeros after each cycle. When the last feature (which should have the most missing values of all the features) is selected, there are no more features that need to be filled with zeros, and we have already used regression to fill in a large amount of information for the other features, so we can use it to fill in the feature with the most missing values.

  * Auto-regression model (?)
  
  
- 07/07/2024

  Found a research paper, titled [From Predictive Methods to Missing Data Imputation:An Optimization Approach](https://jmlr.org/papers/volume18/17-073/17-073.pdf).
  It proposes "flexible framework based on formal optimization to impute missing data with mixed continuous and categorical variables"
  And the authors pose the missing data problem as an "optimization problem", in which they optimize the missing values in all data points and dimensions simultaneously
  ![image](https://github.com/LAFLAMIE1024/Dissertation/assets/73602420/001ea987-df78-42a4-9466-18829dc92189)
  So complicated.

  But it shows comprehensive experiment.
  Now I know what to do with mine: real data set only. Particularly focus on mar and mnar.
  And data MAR **ONLY** depend on other observable information, which means that MAR is less general than MNAR.
  
- 14/07/2024
  
  MCAR could be imputed when we are evaluating the performance of predictive models on various data sets. (of different fields)\
  Difficult to diagnose the hidden pattern within the data set -> Generate missing value by using your own designed scheme -> Evaluate the proximity of imputed values and original values\
  Expecting to improve the performance of predictive model after imputation -> Evaluate the accuracy, recall and F1 score of models on the same data set.
  
  
- 21/07/2024
  
  "... Complete case analyses, which are based on only observations for which all relevant data are present and no fields are missing, of a data set containing MAR data may or may not result in bias. If the complete case analysis is biased, however, proper accounting for the known factors (in the above example, sex) can produce unbiased results in analysis. ... As with MAR data, complete case analysis of a data set containing MNAR data may or may not result in bias; if the complete case analysis is biased, however, the fact that the sources of missing data are themselves unmeasured means that (in general) this issue cannot be addressed in analysis and the estimate of effect will likely be biased."

  true function? unknown. might be a formula containing multiple parameters -> simplify the problem and define the hidden mechanism manually.\
  EM algorithm? How to define the mechanism by using EM? Are we inviting some function describing the relationship between variables? Try to approximate the distribution of original value by updating the parameters in the EM algorithm.
  what about categorical variables? how to impute?
  
- 22/07/2024

  data set? house price
  missing there? 
  
- 01/07/2024
