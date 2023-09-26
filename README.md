### Project Accurate Revenue Forecasting (DATA IS CONFIDENTIAL and NOT INCLUDED IN GITHUB)

**by D. Prodan**

#### Executive summary

This project explored forecasting revenue for a specific company product with the goal of identifying an automated approach that could improve forecasting accuracy. Within our company, we use data and forecasts that have both monthly and daily granularity, therefore this project examined forecasting accuracy with both monthly and daily granularity.

As a result, one approach (using a model called Prophet) was identified that provides a high degree of accuracy for both monthly and daily forecasting. Based on the actual data for 2015-2019 periods, this model achieved ~3% accuracy (measured as the difference between forecasted values and actual values). This model can be put in use with relative ease and the forecast can be updated when desired, including with daily frequency.


#### Rationale (Why should anyone care about this question?)

The financial outlook of a company is an important input to critical financial and business decisions, for example how much can we afford to invest this quarter or year, should we accelerate or decelerate our investments, how much funding is required for the company, etc. The outlook is grounded in forecasts for various income statement line items, such as revenue and operating expenses. An improvement in accuracy of forecasts will help improve the overall accuracy of the outlook and consequently the quality of decisions. 

As forecasts are based on the best available data at the time, an important aspect of forecasting is dynamic and rapid inclusion of new information such as product launches and external events such as covid or macro economic or competitive factors. This project focused on exploring several forecasting techniques with the help of machine learnings models that could provide two key benefits: 
1) improved forecasting accuracy thus resulting in better outcomes
2) automated forecasting that would enable more frequent updates of forecast, and ultimately more accurate forecasts. 

In general, forecasts play a crucial role in various aspects of decision-making:

Planning & Strategy Development: Forecasting provides an estimate of future conditions and outcomes, which allows organizations to plan and strategize accordingly. For instance, a company can plan its production levels based on a sales forecast.

Budgeting: Financial forecasts are the foundation for budgeting. By predicting revenues and expenses, organizations can develop budgets that guide financial decision-making throughout the fiscal year.


Resource Allocation: By forecasting demand or requirements, companies can efficiently allocate resources. This helps in reducing waste and ensuring optimal utilization of resources.

Capital Investment Decisions: Companies can use forecasts to determine if it's the right time for capital expenditures, like buying new machinery like Nvidia GPUs or expanding facilities.

Setting Expectations: For publicly traded companies, forecasts (especially earnings forecasts) help in setting market expectations. Not meeting these forecasts can negatively impact stock prices.


Risk Management: Forecasting helps in anticipating potential risks in the future. By understanding these risks in advance, organizations can develop strategies to mitigate them or even capitalize on new opportunities.


#### Research Question
The project set out to:
1. Explore the trends in data
2. Develop several predictive models (including SARIMAX, Prophet, LSTM, Randon Forest, CNN and XGBoost) that are suitable for time series forecasting, and contrast the accuracy of these models as applied to the specific revenue data for the examined time period (2015-2019). I used 2015-2017 data to train the models, and 2018-2019 data to test the accuracy of the model. Various optimization techniques were used to improve model accuracy - from feature engineering to hyperparameter tuning. Model accuracy was assessed primarily using MAPE (mean average percentage error) - primarily due to being intuitive and its also a benchmark that's already used at the company.

#### Data Sources - what data will you use to answer you question?

The data used for this project represents a time series of historical revenue for a specific product covering 2015-2019 period with daily (and monthly) granularity.


#### Methodology
I broadly followed a structured approach called CRISP-DM methodology:

1. Business Understanding: Define the problem and project objectives.
2. Data Understanding: Gather and explore the data to identify patterns and anomalies.
3. Data Preparation: Clean and transform the data for analysis.
4. Modeling: Explore suitable models, trained them using the prepared data, and evaluate their performance.
5. Evaluation: Assess the model's performance using metrics and its alignment with business objectives.

The methodology also includes deployment of the model in production and integration into business systems. In this project, I have not performed these steps, however I will do that outside of this scope of the project.

#### Results - What did your research find?

TLDR: Out of all forecasting models explored, Prophet came out as a top model that provides a high degree of accuracy of ~3%, improves on existing accuracy, and is relatively easy to implement and use. 


FURTHER DETAILS:

Three models (SARIMAX, Prophet and LSTM) demonstrated a high degree of accuracy of approximately 3% MAPE. This is very impressive and it's an improvement relative to the current accuracy using existing approaches. 

Out of these three models, Prophet provided a high degree of accuracy for both monthly and daily granularity. It also required relatively little time to train. 

SARIMAX provided high accuracy for monthly data, however required very long training time for daily data, therefore being less practical. This is not surprising as SARIMAX models can be computationally intensive and time-consuming, especially when applied to daily data with strong seasonal patterns, such as yearly seasonality, which is the case here

LSTM model provided an even higher degree of accuracy than Prophet for daily data (2.9% vs 3.5%), however relatively low accuracy for monthly data. It's possible that LSTM accuracy for monthly forecasting could have been improved with additional optimization and feature engineering. 

It's not surprising that Prophet came out as top model as it was developed to address this particular use case, i.e. as a high-performance forecasting tool for making accurate time series predictions for data with pronounced seasonal patterns.

The other models explored (Random Forest, XG Boost) were materially less accurate or tended to overfit (XGBoost). It is likely that with incremental tuning their accuracy could have been improved. I've explored some basic optimization techniques however have not 


Model			Train MAPE	Test MAPE
SARIMAX Monthly		0		0.036257
PROPHET Monthly		0.01163		0.029578
PROPHET Daily		0.034191	0.034494
LSTM Monthly		0.029658	0.086470
LSTM Daily		0.043788	0.029377
RandomForest Monthly	0.014429	0.220437
XG Boost Monthly	0.0		0.194975


#### Next steps - What suggestions do you have for next steps?

I recommend that we go ahead with implementing Prophet forecasting approach alongside existing approach, continue monitoring performance of both approaches for a period of several months, and, if the new approach consistently provides higher accuracy over a period of several quarters, we explore switching to the new model.

In addition, further optimization techniques should be explored to improve model accuracy, for example separately examining and handling events that impact revenue on intermittent or permanent basis. These events could include internal factors such as product launches (permanent impact) or outages (temporary impact), and external events such as government elections or sporting events (e.g. Olympics) that provide a temporary boost to revenue. Other optimization techniques to explore could include data augmentation (incorporating incremental data - e.g. user related activity that drives the revenue), or tuning various model parameters. 


#### Outline of project
- Google Colab Notebook included in same folder

##### Contact and Further Information
Daniel Prodan, [do not call]