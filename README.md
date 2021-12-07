#### Project Motivation
___
This capstone project was the last requirement to pass the Applied Data Science Course which is part of the MIT: Professional Education Program. The data provided by the provided featured the carbon emissions from the electrical power industry from 1973 to 2016. The following power sectors are represented in the data: coal, natural gas, distillate fuel, petroleum coke, residual fuel oil, petroleum, geothermal, and non-biomass waste. Similar data can be viewed from the U.S. Energy Information Administration's Monthly Energy Review.

MIT's Applied Data Science program has predefined the focus of the capstone as the following:
"Forecast the carbon emissions value for natural gas (NNEIEUS) fuel type for the next 12 months and propose certain measures that can be adoped as policies to reduce these emissions".

#### Problem and Solution Summary
Problem: The US needs to be able to accurately model and forecast CO2 emissions for Natural gas to lead in action under the Paris Agreement in the following ways:
(1) Being able to track progress on current Natural Gas policies as it relates to its 2030 goal (the year the US will reduce carbon emissions by 50-52% below 2005 levels). 
(2) Error/Miscalculation checker (either in reporting or accounting) for reporting dates established under the Enhanced Transparency Framework adopted in the Paris Agreement (2024 is the nearest due date).
(3) Create new policies, backed from data, if current programs are not meeting deadlines.

#### Approach Used to Create an Accurate Forecasting Model?
___
(1) Split Train and Test
(2) Stationarize: Process (Log, Differencing) and Validation (Visual, Augmented Dickey Fuller Test)
(3) Decompose (multiplicative vs additive) into Trend, Seasonality, and Residuals
(4) Plot ACF and PACF plots to determine p,d,q
(5) Fit using the different models: AR, MA, ARMA, ARIMA, and SARIMAX
(6) Compare results using Evaluation Metric (AIC)
(7) Forecast-test set Validation using RMSE

#### Final Model Specifications and Why it is the Best?
___
SARIMA is believed to be the most robust because of the seasonality parameter, and because it will limit the complexity of the model. For instance, an AR model can be used with decent results, however, it would require p = 12. For the SARIMA model, the final hyperparameters were determined using previous p and q values taken from the PACF and ACF graphs. Some brute force methods were done to find the model with the lowest AIC value when fit. The hyperparameters were in form (p,d,q)(P,D,Q, m): (1, 0, 1)(0, 0, 1, 12)

The AIC for this model and hyperparameters was -1084.88. See below for graph containing other models and some hyperparameter tunings.

<p align="center">
<img src="" width="200" height="200" />
</p>
<p align="center">
    <em>PUT MODEL_AIC_TABL HERE</em>
</p>

<p align="center">
<img src="" width="200" height="200" />
</p>
<p align="center">
    <em>PUT TRAINING FIT HERE</em>
</p>

<p align="center">
<img src="" width="200" height="200" />
</p>
<p align="center">
    <em>PUT FORECAST HERE</em>
</p>

#### Recommendations for Implementation
___
Steps to account for when implementing using MLOps:  the software development lifecycle, and integration with model generation including continuous integration and delivery, deployment, monitoring of health and diagnostics, and analysis of business metrics.
<p align="center">
<img src="" width="200" height="200" />
</p>
<p align="center">
    <em>PUT STEPS HERE</em>
</p>

#### Risks Involved in Implementing the Forecasted Model
___
(1) Excessive time to deploy and increased monetary cost to maintain. This can be caused by misalignment with current database frameworks and languages.
(2) Unexpected behavior once deployed. (High prediction variance with future dataset)
(3) Possible restructuring of support systems like: how data is initiated into the ML model, how data is recorded
(4) Possible limit in model usefulness - Future policies that change the electric production landscape rendering the ML model useless