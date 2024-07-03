- 01/07/2024

  partial clustering?

  This blog,  [How to generate missing values?](https://rmisstastic.netlify.app/how-to/generate/misssimul#:~:text=Missing%20Completely%20At%20Random%20values,Bernoulli%20distribution%20of%20parameter%20perc) ,introduces a couple of different ways to generate MAR data.
  
- 03/07/2024

  The whole structure of handling missing data:
  * Detecting missing data
  * Determining their type (MAR, MCAR, MNAR)
  * Handle them according to their type
    Many ways to deal with these missing entries:
      - Complete Analysis (may result in losing information, or lead to biased analysis)
      - Treat the missingness as an indicator (Create a new binary feature indicating whether a value was missing. This can sometimes improve model performance) (Mentioned in this blog [Effective Strategies for Handling Missing Values in Data Analysis](https://www.analyticsvidhya.com/blog/2021/10/handling-missing-value/) in section: How to Use “Missingness” as a Feature? )
      - Imputation 
        * KNN imputation, Multiple imputation, creating several data sets rather than one filled with single imputed values.
        * KDE imputation (Figure out the distribution of observed data, and try to sample values from the estimated distribution and impute them)
        * Machine Learning Techniques (Use algorithms like Random Forest or XGBoost to predict missing values based on other features in the dataset)
  * See if the performance of classification/clustering algorithm is improved after imputation
  * Experiment: Use a complete data set/simulated data set(How?), and generate some missing values (MCAR is not as informative as MAR does). After all these, 
  
- 01/07/2024
- 01/07/2024
- 01/07/2024
- 01/07/2024
- 01/07/2024
- 01/07/2024
- 01/07/2024
- 01/07/2024
