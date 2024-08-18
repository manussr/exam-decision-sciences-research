# Question 1: Comprehensive Data Acquisition and Preprocessing

Task:
Download and preprocess CO2 emissions data along with a wide range of socio-economic
and environmental indicators from the World Bank’s Climate Change database.

## Preprocessing

K-Nearest Neighbors (KNN) imputation is employed to address missing values in datasets with various indicators by leveraging its capacity to preserve the underlying data structure. The process begins by removing non-numeric columns, such as 'country' and 'date', to isolate the numeric data. This data is then standardized using StandardScaler, which transforms features to have a mean of zero and a standard deviation of one, ensuring that each feature contributes equally to distance calculations. After standardization, KNNImputer with three neighbors is used to estimate and fill in missing values based on the similarity of data points in the scaled space. The imputed values are then reverted to their original scale using the inverse transform of StandardScaler. Finally, the dataset is reconstructed by reattaching the non-numeric columns to the imputed numeric data, resulting in a comprehensive dataset that integrates both original and imputed values. This approach effectively combines KNN imputation with standardized feature scaling, ensuring accurate and contextually relevant handling of missing data.

KNN imputation is a robust method due to its flexibility and its effectiveness in maintaining data relationships. Unlike parametric methods that rely on specific assumptions about data distribution, KNN imputes missing values based on the similarity to neighboring data points, thus preserving the inherent structure of the data. This method is particularly advantageous for datasets with diverse and interrelated indicators, as it accommodates various feature distributions without distorting the data. Standardizing the data before imputation is essential, as it ensures equal contribution from all features, preventing those with larger scales from disproportionately affecting the imputation. This approach not only improves the accuracy of the imputed values but also maintains the multivariate nature of the data, making KNN imputation a practical and effective choice for complex datasets with missing values.

## Key statistics

| Indicator                                                                                                          | count       | mean           | std            | min           | 25%           | 50%           | 75%           | max           |
|--------------------------------------------------------------------------------------------------------------------|-------------|----------------|----------------|---------------|---------------|---------------|---------------|---------------|
| CO2_emissions                                                                                                      | 5690.000000 | 1.030626e+06   | 3.476438e+06   | 0.000000e+00  | 2.303333e+03  | 2.011651e+04  | 2.373627e+05  | 3.556056e+07  |
| GDP_current_US                                                                                                     | 5690.000000 | 1.908900e+12   | 7.095445e+12   | 1.396473e+07  | 5.644204e+09  | 3.449635e+10  | 4.338546e+11  | 8.794557e+13  |
| Population_total                                                                                                   | 5690.000000 | 2.793706e+08   | 8.705055e+08   | 9.609000e+03  | 1.652923e+06  | 9.947042e+06  | 6.780651e+07  | 7.821272e+09  |
| Electric_power_consumption_kWh_per_capita                                                                          | 5690.000000 | 2093.043120    | 2482.653514    | 9.579196      | 607.012896    | 1234.844683   | 2483.822436   | 21420.628504  |
| Urban_population_percentage_of_total                                                                               | 5690.000000 | 57.294093      | 22.966936      | 8.246000      | 38.427371     | 57.046122     | 76.197750     | 100.000000    |
| Educational_attainment_at_least_Bachelors_or_equivalent_population_25_older_than_total_percentage                  | 5690.000000 | 12.986930      | 9.754490       | -1.776357e-15 | 4.870232      | 10.500970     | 19.594940     | 59.260880     |
| Passenger_cars_per_1000_people                                                                                     | 5690.000000 | 92.446888      | 81.965917      | 0.300000      | 20.333333     | 53.696807     | 162.379518    | 290.000000    |
| Renewable_electricity_output_percentage_of_total                                                                   | 5690.000000 | 25.832625      | 28.969410      | 0.000000      | 1.254077      | 16.874250     | 41.757445     | 100.000000    |

## Indicators distributions

![IndicatorsDistribution](/Question-1/whisker-plots.png)

## Correlation Heatmap

![HeatMap](/Question-1/heatmap-question-1.png)
