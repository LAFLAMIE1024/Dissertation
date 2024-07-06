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
  Being metioned in this blog [Diagnosing Type of Missing Data (MCAR, MAR, MNAR)](https://www.reddit.com/r/AskStatistics/comments/17nigqk/diagnosing_type_of_missing_data_mcar_mar_mnar/), we can't do much about MCAR (deletion) and MNAR (better improve data set) as both of they usually do not provide further information of missingness. So what we are looking for is "the patterns in the missingness", and "do the records where a given feature is missing have a different distribution than the records where the feature isn't missing?"
    * If the answer to that question is a clear "yes", then that feature **isn't missing at random**.\
      Value missing here is significantly different from the other values in this column -> Missing not at random
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
  * [Use random forest for imputation](https://zhuanlan.zhihu.com/p/635931775) ->  start from the feature with least missing values, which is our target column, and train the random forest on the non-missing part of the target column. After that, we predict missing values in this target column using the other features as input.
  遍历所有的特征，从缺失最少的开始进⾏填补（因为填补缺失最少的特征所需要的准确信息最少）。填补⼀个特征时(次特征作为标签值)，先将其他特征的缺失值⽤0代替，每完成⼀次回归预测，就将预测值放到原本的特征矩阵中，再继续填补下⼀个特征。每⼀次填补完毕，有缺失值的特征会减少⼀个，所以每次循环后，需要⽤0来填补的特征就越来越少。当进⾏到最后⼀个特征时（这个特征应该是所有特征中缺失值最多的），已经没有
任何的其他特征需要⽤0来进⾏填补了，⽽我们已经使⽤回归为其他特征填补了⼤量有效信息，可以⽤来填补缺失最多的特征。
  * Auto-regression model
  
  
- 07/07/2024

  Found a research paper, titled [From Predictive Methods to Missing Data Imputation:An Optimization Approach](https://jmlr.org/papers/volume18/17-073/17-073.pdf).
  It proposes "flexible framework based on formal optimization to impute missing data with mixed continuous and categorical variables"
  And the authors pose the missing data problem as an "optimization problem", in which they optimize the missing values in all data points and dimensions simultaneously
  ![image](https://github.com/LAFLAMIE1024/Dissertation/assets/73602420/001ea987-df78-42a4-9466-18829dc92189)
  So complicated.
  
- 01/07/2024


  
- 01/07/2024

  
- 01/07/2024

  
- 01/07/2024
