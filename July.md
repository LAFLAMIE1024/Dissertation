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

  Thus, the experiment of testing how well we handled can be conducted like:
  1. Choose a real complete data set/simulated data set\
    - If real, Size? Number of features? Continuous or discrete feature?
    - If simulated, distribution (Gaussian? Gamma?)?
  2. Generate some missing values (MCAR is not as informative as MAR does).
  3. Depending on the type of missing values created, try all methods mentioned above.\
     After imputation, **evaluate the accuracy of imputation**.
  4. **See if the performance of classification/clustering algorithm is improved after preprocessing**.
  
- 04/07/2024

  Finding out if there is hidden correlation between variables by using random forest?
  
- 05/07/2024

  Missing data is not necessary of one type. It could be MAR and MNAR at the same time.
  Being metioned in this blog [Diagnosing Type of Missing Data (MCAR, MAR, MNAR)](https://www.reddit.com/r/AskStatistics/comments/17nigqk/diagnosing_type_of_missing_data_mcar_mar_mnar/), we can't do much about MCAR (deletion) and MNAR (better improve data set) as both of they usually do not provide further information of missingness. So what we are looking for is "the patterns in the missingness", and "do the records where a given feature is missing have a different distribution than the records where the feature isn't missing? If the answer to that question is a clear "yes", then that feature isn't missing at random. A clear "no" means the feature is missing completely random. If it's less clear then the feature then it can likely said to be missing at random, but could also go either way. It could also be the result of multiple sources of missingness."
  
- 01/07/2024
- 01/07/2024
- 01/07/2024
- 01/07/2024
- 01/07/2024
- 01/07/2024
