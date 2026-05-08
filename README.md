

# 444 Final Project

## Project Overview
In this  project we  compared traditional, machine learning, neural, and foundation-model. We approached a realistic business forecasting task and then explain which methods perform best and why. We forecasted room demand for the 17 hotel properties using the sample_hotels.parquet. We looked for Y daily room demand for the next 4 weeks. 

We did all of our work on the following DeepNote File: 
[DeepNote File](https://deepnote.com/workspace/ISA444-b9f43125-8122-4dd6-9928-9afea823b37b/project/Final-Project-44bf3ddd-e5de-4d20-8ce8-c4038e2ca0ff/notebook/Final-Project-2533c10aab9c43f0b3e9cc2f5fcca158?utm_source=share-modal&utm_medium=product-shared-content&utm_campaign=notebook&utm_content=44bf3ddd-e5de-4d20-8ce8-c4038e2ca0ff)

and the TimeCopilot and TABpfn on this deepnote: 
[TEBpfn](https://deepnote.com/workspace/ISA444-b9f43125-8122-4dd6-9928-9afea823b37b/project/Final-Project-44bf3ddd-e5de-4d20-8ce8-c4038e2ca0ff/notebook/TimeCopilot-70af92c57aa74a5ea8786ec36e1664a0?utm_source=share-modal&utm_medium=product-shared-content&utm_campaign=notebook&utm_content=44bf3ddd-e5de-4d20-8ce8-c4038e2ca0ff )  

## Step One: prepare and validate data
The first thing we did was prepare and validate our hotel data. Based off the plots we produced, we removed hotel 28 and 77. The following images show the data we kept. 

<img width="924" height="582" alt="Screenshot 2026-05-04 at 2 11 18 PM" src="https://github.com/user-attachments/assets/cb9aa4bc-34a5-4a0e-be32-47048de1a31e" />

 <img width="947" height="566" alt="Screenshot 2026-05-04 at 2 11 49 PM" src="https://github.com/user-attachments/assets/5344d2f3-b2e2-4bb0-b3af-86cbdfdd2c64" />

 <img width="931" height="574" alt="Screenshot 2026-05-04 at 2 12 10 PM" src="https://github.com/user-attachments/assets/049a4275-65c1-48e8-83e3-a5b6408be811" />


## Step Two: Set up a 5-fold time-series cross-validation
We then set up a 5 fold time series cross validation. 

## Step three: Train and compare all required models
We ran the baseline models with no predictors. In this step we ran Naive, SeasonalNaive, AutoETS, and AutoARIMA.
Following that we ran AutoARIMA with predictors. 

Then we did the Machine Learning models.  

Lastly we did the TimeCoPilot model

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

Looking at the baseline models without predictors the AutoARMIA won. This model has the most lowest evaluation metrics. 

TALK ABOUT AUTOARMIMA W PREDS

TALK ABOUT NEURAL 

Out of the TimeCopilot models, the TimesFM-2.5 model outpreformed the others. 

Lastly the LightGBM model was the best model of the machine learning ones. 

## Step five: Generate final test forecasts and export results to CSV

 ---CREATE A GRAPH WITH THE MODEL WE LIKE THE MOST TO FORECAST---

## Step six: Create forecast-vs-actual plots for every series
Take the best model and apply it to each hotel! 

## Step seven: Conclusion


