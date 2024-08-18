# Question 1: Comprehensive Data Acquisition and Preprocessing

Task:
Download and preprocess CO2 emissions data along with a wide range of socio-economic
and environmental indicators from the World Bank’s Climate Change database.

## Key Indicators

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
