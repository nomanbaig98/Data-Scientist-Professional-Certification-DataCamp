# DataCamp's Data Scientist Professional Certification
# Recipe Site Traffic

The objectives of our project revolve around two key goals: predicting recipes that will result in high traffic and achieving an 80% accuracy in predicting high traffic recipes.

To achieve these objectives, our initial step entailed a thorough examination of the provided dataset. The dataset comprises 947 observations across 8 columns. Within these columns, one corresponds to a unique recipe ID, while four are numerical variables—encompassing attributes like calories and three nutritional components. An additional two columns are categorical variables, representing "category" and "servings," respectively. Lastly, the final column serves as our target variable, indicating high traffic status.

During our exploration, we meticulously addressed data preprocessing and cleaning tasks. This encompassed actions such as removing duplicates, managing missing values through replacement or deletion, converting data types as needed, and more. By the conclusion of this stage, our efforts led to a streamlined dataset featuring 895 observations, effectively prepared and devoid of inconsistencies for further analysis.

![Picture1](https://github.com/erturkmemmedli/Recipe-Site-Traffic-Project/assets/49902768/90563eb5-6cc9-45bb-bbff-9620890111dd)


Our exploratory data analysis commenced with the utilization of a pairplot, enabling us to visualize relationships among numerical variables. Through the scatterplots representing variable interactions, a prominent observation emerges: there is no substantial relationship between these variables. This is a desirable outcome, as the absence of correlation prevents potential biases in model development.

![Picture2](https://github.com/erturkmemmedli/Recipe-Site-Traffic-Project/assets/49902768/87537e01-73a2-4951-81bb-20322ef5811a)

Subsequently, we employed histograms to unveil the distribution patterns of calories and nutritional components within the recipes. The outcome, as depicted on the screen, indicates that all these distributions exhibit a right-skewed nature. This suggests that recipes generally tend to favor lower values in terms of both calories and the quantity of nutritional components.

![Picture3](https://github.com/erturkmemmedli/Recipe-Site-Traffic-Project/assets/49902768/81e81e46-015b-4e9d-9f24-31cd12dd1299)

In the subsequent analysis presented through boxplots, we are offered a distinct perspective that reinforces our earlier observations. The boxplots effectively highlight the presence of outliers and accentuate how observations predominantly cluster on the left side, corresponding to lower values. This serves as further evidence of the prevalent right-skewness in the distribution.

Given these consistent findings, it becomes apparent that opting for the median as the preferred statistical measurement metric is prudent. This choice is logical considering the skewed nature of the data distribution.

![Picture4](https://github.com/erturkmemmedli/Recipe-Site-Traffic-Project/assets/49902768/1a6b8acb-ef5b-4760-bf11-2506b2142f2e)


In this section, our focus shifts to evaluating the medians of numerical variables according to different categories. What becomes evident is that the medians for calories and nutritional components are not uniformly distributed, diverging based on the type of food and beverages. This underscores the influence of the food category on these specific attributes' medians.

![Picture5](https://github.com/erturkmemmedli/Recipe-Site-Traffic-Project/assets/49902768/188aa0c2-03ce-40ea-9752-04cc70b6734f)

Subsequently, we shifted our attention to examining the connection between categorical variables and the high traffic status. The left figure reveals that while the proportions of high traffic to low traffic recipes are generally comparable, instances with a serving count of 6 tend to achieve higher traffic. Additionally, the right figure illustrates that certain categories consistently generate higher traffic rates. Notably, the top three categories contributing to higher traffic are "Vegetable," "Potato," and "Pork," while the "Beverages" category falls at the lower end in terms of traffic.

With the completion of our analysis, we proceeded to develop the most fitting model to achieve our objectives. Given that our task involves a binary target variable, the problem aligns with the domain of binary classification algorithms within supervised machine learning. For tackling this, we have the option to construct various models including Linear Regression, Decision Tree, Random Forest, Support Vector Machines, and more. My choice for the baseline model is Linear Regression, while the other models serve as comparison models in this context.

![Picture6](https://github.com/erturkmemmedli/Recipe-Site-Traffic-Project/assets/49902768/d6b066e1-f82e-49d5-995f-5220706cc222)


However, prior to model fitting, a crucial step is to transform our numerical variables due to their right-skewed distribution. I've explored an array of techniques, encompassing outlier removal, outlier capping, winsorization, logarithmic transformation, square root transformation, Box-Cox transformation, and Yeo-Johnson transformation.

Among these options, the most optimal choice emerged as the Yeo-Johnson transformation. The distribution of numerical variables post this transformation is depicted on the screen. This transformation effectively mitigates the right-skewed nature of the data, enhancing the compatibility with our models.

![Picture7](https://github.com/erturkmemmedli/Recipe-Site-Traffic-Project/assets/49902768/cac1deed-cc0c-45f9-b703-4cab0e5f7045)


Subsequent to the transformation of numerical variables, the next step involved implementing one-hot encoding to address the categorical variables. Specifically, this encoding was applied solely to the "category" column. While the "servings" column is categorical in nature, its numeric values carry logical meaning, representing the count of servings. Therefore, this column was not subjected to one-hot encoding, as its numerical values are contextually meaningful.

![Picture8](https://github.com/erturkmemmedli/Recipe-Site-Traffic-Project/assets/49902768/2e463ce6-016b-49e0-af46-5c5b69e86e4e)


After this comprehensive journey of data preprocessing, analysis, and model development, we've arrived at a conclusive synthesis of our efforts:

We embarked on this venture with two primary objectives: predicting high traffic recipes and achieving an 80% accuracy rate in these predictions. Our dataset consisted of 947 observations distributed across 8 columns. Among these, one column represented a unique recipe ID, four columns were dedicated to numerical variables (calories and three nutritional components), two columns dealt with categorical variables (category and servings), and the final column constituted our target variable (high traffic).

Our rigorous approach to preprocessing encompassed duplicate elimination, managing missing values, data type conversions, and more. This culminated in a refined dataset featuring 895 clean observations, primed for analysis.

The exploratory analysis phase commenced with a pairplot, revealing minimal correlation among numerical variables—safeguarding against bias. Subsequently, histograms and boxplots confirmed the right-skewed nature of the data distribution, necessitating the preference for median over mean.

Further analysis was conducted to assess medians according to categories. It became evident that medians for calories and nutritional components were non-uniform, contingent on the food or beverage category.

We scrutinized the relationship between categorical variables and high traffic. This exploration highlighted the significance of serving count and specific categories in influencing traffic rates. Notably, "Vegetable," "Potato," and "Pork" emerged as high traffic-driving categories, while "Beverages" demonstrated lower traffic.

With these insights in mind, we delved into model development. Given the binary nature of our target variable, we explored various supervised machine learning models including Linear Regression, Decision Tree, Random Forest, and Support Vector Machines. We selected Linear Regression as our baseline model, while the others served as comparison models.

Model development commenced after implementing the Yeo-Johnson transformation on numerical variables and performing one-hot encoding for categorical variables. The data was divided into train and test sets, models were fitted, and predictions were generated. Evaluation revealed that the Logistic Regression model demonstrated strong alignment between test and train results, without signs of overfitting. This model yielded a precision of 80.87%, fulfilling our 80% high traffic prediction objective.

While Decision Tree and Random Forest models exhibited overfitting due to their robustness, the Support Vector Machines model suffered from underfitting attributed to limited data. More complex models such as Gradient Boosting, LGBM, and xGboost were deemed inappropriate due to the risk of overfitting with insufficient data.

From a business perspective, predicting high traffic as low traffic poses a graver concern. Hence, our emphasis lies on model precision. We introduced a Key Performance Indicator (KPI) termed "High Traffic Conversion Rate," defined by the True Positive / False Positive ratio in the confusion matrix. This KPI should consistently exceed 4.0 based on our baseline model results.

Through this analysis, we identified categories that consistently generate high or low traffic. "Vegetable," "Potato," and "Pork" categories consistently yield high traffic, recommending their constant presence on the website. Conversely, the "Beverages" category tends to result in low traffic, advising its omission.

To encapsulate, our journey encompassed data preprocessing, analysis, and model development, culminating in the realization that the Logistic Regression model best addresses our objectives. This model emerges as the optimal choice for predicting high traffic recipes with 80% accuracy. Moreover, our introduced KPI provides a benchmark for assessing model performance in a business context, while insights about category traffic can guide content offerings.

