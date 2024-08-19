# Question 2: Predictive Modeling and Scenario Analysis

Task:
Develop a predictive model to forecast CO2 emissions based on the comprehensive set of
indicators. Use the model to answer an analytical question: “If a country increases its GDP
by 10%, what is the expected percentage change in CO2 emissions, assuming all other
factors remain constant?

## Scenario analysis

The goal is to develop a predictive model using XGBoost to forecast CO2 emissions based on a comprehensive set of socio-economic and environmental indicators. The model is then used to answer an analytical question: "If a country increases its GDP by 10%, what is the expected percentage change in CO2 emissions, assuming all other factors remain constant?"


### Data preparation

The dataset, extended_data_imputed, contains several indicators, with 'CO2_emissions' as the target variable. The non-numeric columns 'date' and 'country' are excluded from the features (X), leaving the indicators as predictors.

To address the posed question, the GDP for each country is increased by 10% in the dataset, simulating a scenario where GDP growth is observed while all other indicators remain unchanged.
The model, trained on the original dataset, is then used to predict CO2 emissions for this simulated scenario.

### Choice of model

XGBoost is an excellent choice for a regression task on an imputed dataset containing various indicators such as CO2 emissions, GDP, population, and other socio-economic factors due to the following key reasons:

* Versatility: XGBoost effectively handles datasets with a mix of continuous and categorical variables. Given the diverse indicators in the dataset, XGBoost's ability to manage different types of features makes it highly suitable for this regression task, even after imputation.

* Insights into Relationships: XGBoost provides a mechanism to assess feature importance, offering a clear understanding of which indicators most significantly influence the target variable. This is particularly valuable when working with a wide range of socio-economic and environmental indicators, as it helps identify the key drivers of the regression outcome.

* Resilience: XGBoost is inherently robust to outliers and works well with datasets that have undergone imputation. This resilience is advantageous in scenarios where countries may have incomplete data or extreme values due to unique circumstances, ensuring that the model remains reliable.

* Complex Patterns: XGBoost excels in capturing non-linear relationships and interactions between features, often present in complex global datasets. For instance, the relationship between GDP and CO2 emissions might not be linear, and XGBoost can model such complexities more effectively than linear models.

* Model Generalization: XGBoost incorporates regularization parameters that help prevent overfitting, which is crucial when dealing with a dataset spanning 20 years across multiple countries. This feature allows the model to generalize well to unseen data, providing more reliable predictions in the context of global indicators.

* Optimization: XGBoost offers a wide range of hyperparameters that can be fine-tuned to optimize model performance for specific datasets. This flexibility allows for tailored model development that aligns closely with the characteristics of the dataset, ensuring the best possible predictive accuracy.

In summary, XGBoost is well-suited for a regression task on an imputed dataset containing diverse and complex global indicators. Its versatility, robustness, and efficiency, coupled with its ability to handle non-linear relationships, provide insights into feature importance, and prevent overfitting, make it a powerful tool for accurately modeling and predicting outcomes based on intricate socio-economic and environmental data.

### Model training

The data is split into training and test sets to evaluate the model's performance. A GridSearchCV is employed with a 5-fold cross-validation to tune hyperparameters of the XGBoost model, including the number of estimators, learning rate, max depth, subsample ratio, and regularization parameters (alpha and lambda).
The grid search identifies the best combination of parameters, and the final model is trained on the entire training dataset.

### Model evaluation

The model's performance is assessed using Root Mean Squared Error (RMSE) and R-squared metrics. Cross-validation results are also considered to validate the model's robustness.
A low RMSE and a high R-squared value indicate the model's ability to accurately predict CO2 emissions based on the given indicators.

## Results

### Fine-tuning results

The XGBoost model was fine-tuned using GridSearchCV, evaluating 2,916 different parameter combinations across 5 folds, resulting in a total of 14,580 fits. The objective was to find the optimal set of hyperparameters for predicting CO2 emissions based on acquired socio-economic and environmental indicators.

The table below displays the optimal parameters identified for the model:

| **Parameter**          | **Value**                                    |
|------------------------|----------------------------------------------|
| **alpha**              | 0.5 (L1 regularization)                      |
| **colsample_bytree**   | 0.8 (percentage of features used per tree)   |
| **gamma**              | 0 (minimum loss reduction to make a further partition) |
| **lambda**             | 1.0 (L2 regularization)                      |
| **learning_rate**      | 0.1 (step size shrinkage)                    |
| **max_depth**          | 5 (maximum depth of a tree)                  |
| **n_estimators**       | 300 (number of trees)                        |
| **subsample**          | 0.8 (fraction of samples used for each tree) |

### Model performance

* Root Mean Squared Error (RMSE): 180,144.51
This value represents the standard deviation of the residuals (prediction errors). A lower RMSE indicates better model performance, and in this case, the model demonstrates high accuracy in predicting CO2 emissions.

* R-squared: 0.9964
The R-squared value indicates that approximately 99.64% of the variance in CO2 emissions is explained by the model. This suggests a strong relationship between the predictors and the target variable, with the model capturing nearly all the variance.

* Cross-Validated RMSE (Best Model): 155,138.91
The cross-validated RMSE provides an estimate of the model's performance on unseen data. The value indicates the model’s predictive accuracy is consistent across different folds of the data, validating its robustness.

The identified hyperparameters suggest a well-balanced model that avoids overfitting while capturing the essential relationships between the predictors and CO2 emissions.
The very high R-squared value confirms the model's effectiveness in explaining the relationship between socio-economic indicators and CO2 emissions.
The relatively low RMSE values (both train-test and cross-validated) indicate that the model is precise in its predictions, making it a reliable tool for forecasting and scenario analysis.

The model is highly accurate and robust, making it a strong candidate for predicting CO2 emissions based on the given set of indicators. The results suggest that the model is well-calibrated to provide reliable insights into the potential environmental impact of economic and social changes.