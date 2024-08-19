# Question 1: Comprehensive Data Acquisition and Preprocessing

Task:
Download and preprocess CO2 emissions data along with a wide range of socio-economic
and environmental indicators from the World Bank’s Climate Change database.

## Data acquisition

The data for this task was obtained using Wbdata, a Python interface for accessing and retrieving information from the World Bank's databases. The dataset spans from January 1, 2000, to January 1, 2020. Once you run the script question-1.ipynb, it will create 2 files: world_bank_extended_data.csv and world_bank_extended_data_imputed.csv . The later was used for creating this file.

The dataset includes the following indicators:

* EN.ATM.CO2E.KT: Total CO2 emissions (kt) - The total amount of carbon dioxide emissions, measured in kilotons.

* NY.GDP.MKTP.CD: Gross Domestic Product (GDP) at current prices (USD) - The total value of all goods and services produced within a country, measured in current US dollars.

* SP.POP.TOTL: Total population - The total number of people residing in a country.

* EG.USE.PCAP.KG.OE: Energy use per capita (kg of oil equivalent) - The amount of energy consumed per person, measured in kilograms of oil equivalent.

* SP.URB.TOTL.IN.ZS: Urban population (% of total population) - The percentage of the total population living in urban areas.

* SE.TER.CUAT.BA.ZS: Tertiary education attainment (% of population aged 25-64 with a bachelor's degree or higher) - The percentage of individuals aged 25-64 who have completed tertiary education.

* IS.VEH.NVEH.P3: Number of vehicles per capita - The number of vehicles available per person in a country.

* EG.ELC.RNEW.ZS: Renewable electricity consumption (% of total electricity consumption) - The percentage of electricity consumed that is generated from renewable sources.

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

In the next plot, we observe the trend of CO2 emissions over time. It is evident that CO2 emissions have consistently increased each year, except for a decline observed in 2020. This decrease may be attributed to external factors, such as significant global socioeconomic events. 

![CO2EmissionsOverTime](/Question-1/images/co2-emissions-over-time.png)

In this chart, we visualize the relationship between three variables. From the data, we derive the following insights:

As GDP increases, CO2 emissions also tend to increase, indicating that economic growth is accompanied by higher energy consumption and CO2 emissions.
The color gradient illustrates that countries with higher levels of urbanization tend to exhibit higher CO2 emissions.
It's important to note that there is considerable overlap between data points of different colors, suggesting that urbanization alone does not solely determine CO2 emissions levels.

![CO2GDPUrb](/Question-1/images/co2-emissions-gdp-urbanization.png)


## Indicators distributions

In the next figure, distributions of variables from the dataset are displayed. The y-axis for CO2 emissions, GDP, total population, and energy use per capita has been set to a logarithmic scale for improved visualization. Outlier values were identified using the interquartile range (IQR) method with a threshold of 1.5 times the IQR above the third quartile and below the first quartile. Notably, these indicators exhibit outlier values, particularly in CO2 emissions, GDP, and total population, which account for 17.47%, 18.58%, and 20.09% of the dataset, respectively.

![IndicatorsDistribution](/Question-1/images/whisker-plots.png)



## Correlation Heatmap

The following figure illustrates the correlations between the variables in the dataset. Warmer colors indicate stronger correlations.

Key observations include:

* CO2 emissions show high correlations with GDP and total population, reflecting how economic output and population size impact carbon emissions.
* GDP is also highly correlated with total population, suggesting that larger populations may drive higher economic output.
* There is a notable correlation between the urban population and the number of vehicles per capita, indicating that more urbanized regions tend to have more vehicles.
* The urban population is positively correlated with tertiary education attainment, suggesting that more urban areas have higher levels of educational attainment.
* A negative correlation is observed between the number of vehicles per capita and renewable electricity consumption, indicating that higher vehicle ownership may be associated with lower renewable energy use.


![HeatMap](/Question-1/images/heatmap-question-1.png)


