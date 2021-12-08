#### Project Motivation
___
This capstone project was the last requirement to pass the Applied Data Science Course which is part of the MIT: Professional Education Program. The data provided featured the carbon emissions from the electrical power industry from 1973 to 2016. The following power sectors are represented in the data: coal, natural gas, distillate fuel, petroleum coke, residual fuel oil, petroleum, geothermal, and non-biomass waste. Similar data can be viewed from the U.S. Energy Information Administration's Monthly Energy Review.

MIT's Applied Data Science program has predefined the focus of the capstone as the following:
"Forecast the carbon emissions value for natural gas fuel type for the last 12 months and propose certain measures that can be adoped as policies to reduce these emissions".

#### Problem Summary
___
The US needs to be able to accurately model and forecast CO2 emissions for Natural gas to lead in action under the Paris Agreement in the following ways:
1. Being able to track progress on current Natural Gas policies as it relates to its 2030 goal (the year the US will reduce carbon emissions by 50-52% below 2005 levels). 
2. Error/Miscalculation checker (either in reporting or accounting) for reporting dates established under the Enhanced Transparency Framework adopted in the Paris Agreement (2024 is the nearest due date).
3. Create new policies, backed from data, if current programs are not meeting deadlines.

#### Approach Used to Create an Accurate Forecasting Model?
___
1. Split Train and Test
2. Stationarize: Process (Log, Differencing) and Validation (Visual, Augmented Dickey Fuller Test)
3. Decompose (multiplicative vs additive) into Trend, Seasonality, and Residuals
4. Plot ACF and PACF plots to determine p,d,q
5. Fit using the different models: AR, MA, ARMA, ARIMA, and SARIMAX
6. Compare results using Evaluation Metric (AIC)
7. Forecast-test set Validation using RMSE

#### Final Model Specifications and Why it is the Best?
___
SARIMAX is believed to be the most robust because of the seasonality parameter. The final hyperparameters were determined using Grid Search and were found to be (p,d,q)(P,D,Q, m): (1, 0, 1)(0, 0, 1, 12)

The AIC for this model and hyperparameters was -1084.88. See below for chart comparing the AIC for other models.

<p align="center">
<img src="https://github.com/Kyle-f-r/Time-Series-Carbon-Emission-Forecasting/blob/master/images/Model_AIC_table.png?raw=true" width="150" height="140" />
</p>
<p align="center">
    <em></em>
</p>

<p align="center">
<img src="https://github.com/Kyle-f-r/Time-Series-Carbon-Emission-Forecasting/blob/master/images/Test_Forecast.png?raw=true" width="570" height="400" />
</p>
<p align="center">
    <em>Forecasted data for the last 12 months and the test set</em>
</p>

#### Recommendations for Implementation
___
Steps to account for when implementing using MLOps:  the software development lifecycle, and integration with model generation including continuous integration and delivery, deployment, monitoring of health and diagnostics, and analysis of business metrics.
<p align="center">
<img src="https://github.com/Kyle-f-r/Time-Series-Carbon-Emission-Forecasting/blob/master/images/Implementation_flowchart.png?raw=true" width="400" height="250" />
</p>
<p align="center">
    <em></em>
</p>


#### Risks Involved in Implementing the Forecasted Model
___
1. Excessive time to deploy and increased monetary cost to maintain. This can be caused by misalignment with current database frameworks and languages.
2. Unexpected behavior once deployed. (High prediction variance with future dataset)
3. Possible restructuring of support systems like: how data is initiated into the ML model, how data is recorded
4. Possible limit in model usefulness - Future policies that change the electric production landscape rendering the ML model useless