

# 444 Final Project

## Project Overview
In this  project we  compared traditional, machine learning, neural, and foundation-model. We approached a realistic business forecasting task and then explain which methods perform best and why. We forecasted room demand for the 17 hotel properties using the sample_hotels.parquet. We looked for Y daily room demand for the next 4 weeks. 

We did the baseline models, model with predictions, and machine learning the following DeepNote File: 
[DeepNote File](https://deepnote.com/workspace/ISA444-b9f43125-8122-4dd6-9928-9afea823b37b/project/Final-Project-44bf3ddd-e5de-4d20-8ce8-c4038e2ca0ff/notebook/Final-Project-2533c10aab9c43f0b3e9cc2f5fcca158?utm_source=share-modal&utm_medium=product-shared-content&utm_campaign=notebook&utm_content=44bf3ddd-e5de-4d20-8ce8-c4038e2ca0ff)

TimeCopilot and TABpfn on this deepnote: 
[TEBpfn](https://deepnote.com/workspace/ISA444-b9f43125-8122-4dd6-9928-9afea823b37b/project/Final-Project-44bf3ddd-e5de-4d20-8ce8-c4038e2ca0ff/notebook/TimeCopilot-70af92c57aa74a5ea8786ec36e1664a0?utm_source=share-modal&utm_medium=product-shared-content&utm_campaign=notebook&utm_content=44bf3ddd-e5de-4d20-8ce8-c4038e2ca0ff )  

And Neural Forecast in this colab: 
[Neural](https://colab.research.google.com/drive/15X2HTfM5jgDDFHwBj_d0MgWARMrCmFtG#scrollTo=r1LfmzipVH1a)

## Step One: prepare and validate data
The first thing we did was prepare and validate our hotel data. Based off the plots we produced, we removed hotel 28 and 77. The following images show the data we kept. 

<img width="924" height="582" alt="Screenshot 2026-05-04 at 2 11 18 PM" src="https://github.com/user-attachments/assets/cb9aa4bc-34a5-4a0e-be32-47048de1a31e" />

 <img width="947" height="566" alt="Screenshot 2026-05-04 at 2 11 49 PM" src="https://github.com/user-attachments/assets/5344d2f3-b2e2-4bb0-b3af-86cbdfdd2c64" />

 <img width="931" height="574" alt="Screenshot 2026-05-04 at 2 12 10 PM" src="https://github.com/user-attachments/assets/049a4275-65c1-48e8-83e3-a5b6408be811" />


## Step Two: Set up a 5-fold time-series cross-validation
We then set up a 5 fold time series cross validation. For each cross-validation, we had horizon=28, step-size=28, and number of windows = 5

## Step three: Train and compare all required models
We ran the baseline models with no predictors. In this step we ran Naive, SeasonalNaive, AutoETS, and AutoARIMA.
Following that we ran AutoARIMA with predictors. 

Then we did the Machine Learning models, Neural, and  TimeCoPilot models. 

## Step four: Aggregate evaluation metrics and count model wins
The CSV below shows the evaluation metrics with some of the models that we ran (Naive, SeasonalNaive, AutoETS, AutoARIMA with No Preds, and AutoARIMA with Preds) 
([CSV with basline models](https://github.com/user-attachments/files/27451013/2026-05-06T17_53_40%2B00_00_6dva.csv) )

This CSV shows the evaluation metrics with the machine learning models that we ran (Lasso,KNN,Random Forest,LightGBM)
([CSV with Machine learning models](https://github.com/user-attachments/files/27450394/2026-05-06T17_30_18%2B00_00_in9m.csv))

This CSV shows the evaluation metrics with the NeuralForecast models
[CSV with Neural Forecast](https://github.com/user-attachments/files/27531648/neuralforecasts_metrics.csv)
)

This CSV shows the evaluation metrics with the TimeCopilotForecasts (Chronos,Moirai,TimesFM,TabPFN)
([CSV with TimeCiplot AND TabPFN ](https://github.com/user-attachments/files/27451628/tf_eval.csv))

We then counted how often each model wins, where a win means the model achieves the lowest value for a specific metric on a given series (for example, lowest MAE). The following charts show those results: 

Baseline model: <img width="308" height="157" alt="Screenshot 2026-05-07 at 1 40 16 PM" src="https://github.com/user-attachments/assets/e138f3b1-47f4-421e-8dc2-e1b64f8fd6e7" />

Neural: <img width="193" height="102" alt="unnamed" src="https://github.com/user-attachments/assets/6b5a0c41-d7cc-4444-bd6e-feaa6e8fce01" />

TimeCoPilot: <img width="306" height="138" alt="Screenshot 2026-05-08 at 11 44 40 AM" src="https://github.com/user-attachments/assets/fef98910-b476-492b-b0f0-fbe6461f615a" />

Machine Learning: <img width="312" height="136" alt="Screenshot 2026-05-08 at 11 53 42 AM" src="https://github.com/user-attachments/assets/8acca331-11d2-46e3-a6ff-3d4a61c1671a" />

Looking at the baseline models without predictors the AutoARMIA won. This model has the most lowest evaluation metrics in the most cases, which means that AutoARIMA will perform the best when forecasting the hotel occupancy. Since AutoARIMA with predictions was conducted using a different cross evaluation, we were not able to compare the counts of AutoARIMAwPred with the rest of the models without predictions, but in the evaluation forecast in the sf_eval.csv, it is shown that using AutoARIMAwPredictions provides slightly better results because it has lower metric results using that model. AutoARIMA would work the best for hotel occupancy since this model work well with repeating patterns, stable seasonal structure, predictable cyclic demand, which would be found in hotel forecasts. 

Out of the two neural models, AutoNBEATS preformed best. AutoNBEATS performed significantly better since it was the best model in 37 cases, while AutoNHITS only performed better in 15 cases. 

Out of the TimeCopilot models, the TimesFM-2.5 model outpreformed the others. TimesFM would work best on this data since it is built as a general-purpose forecasting foundation model. 

Lastly the LightGBM model was the best model of the machine learning ones. LightGBM had the best metrics compared to the other models since LightGBM won in 39 cases, while the next winner was KNN, which only won in 17 cases. LightGBM performed well on this data since it is good at capturing non-linear demand patterns that can happen with pricing changes, holidays, and events. 

## Step five: Create forecast-vs-actual plots for every series
Based on the results from the model counts, we took the model that perfomed the best and created plots to forecast the results and compare them with each other. 

Neuralforecast plots:
<img width="1834" height="3161" alt="forecast image" src="https://github.com/user-attachments/assets/d98562d2-9463-4f50-bcbe-5695957e573f" />

AutoARIMA plots: 
<img width="1765" height="3161" alt="AutoARIMA_forecasts" src="https://github.com/user-attachments/assets/d068eba8-7646-4a7b-b46f-a3b058a0ebda" />

Machine Learning plots:  
<img width="1755" height="3161" alt="ML_graphs" src="https://github.com/user-attachments/assets/2d86c59e-f12e-4ed8-8816-79fb8ab29ea7" />

TimeCopilot Plots: 
<img width="1776" height="1411" alt="TimeCopilot_forecast" src="https://github.com/user-attachments/assets/5560071a-3eb1-4139-ae6d-7444464ca233" />


## Step six: Conclusion
In this project, we conducted an end-to-end predictive analysis. We started by preparing the inital data and then used key evaluation metrics to test several different types of models against each other. After identifying the top-performing models from each category, we generated and graphed the final 28-day forecasts.

Throughout the evaluation phase, we discovered that AutoARIMA was the strongest performer for capturing the specific seasonality and trends found in hotel data, consistently outperforming our baseline models. We also found that the model’s accuracy improved significantly by incorporating "On The Books" (OTB) data and other seasonal predictors like holidays and target dates.

The success of these models is clearly shown in our forecast graphs. You can visibly see that the AutoARIMA models produce the most realistic and accurate predictions, successfully mapping out future demand.

We also did include the TabPFN and it was cool to use such new technology. 

