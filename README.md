# 444 Final Project

## Project Overview
In this  project we  compared traditional, machine learning, neural, and foundation-model. We approached a realistic business forecasting task and then explain which methods perform best and why. We forecasted room demand for the 17 hotel properties using the sample_hotels.parquet. We looked for Y daily room demand for the next 4 weeks.

## Folder Structure
The repository is organized as follows:
```
444FinalProject/
├── data/               # Contains datasets used for the project
├── notebooks/          # Jupyter notebooks with data analysis
├── outputs/           # Generated output files and figures
├── src/               # Source code for the project
└── README.md          # Project overview and documentation
```
#import data
df = (
    pd.read_parquet('sample_hotels-1.parquet'))

display(df)

df = df.rename(columns={
    'hotel_id': 'unique_id',  
    'date': 'ds',              
    'bookings': 'y'})

plot_series(df, engine="matplotlib", max_ids=18)

#get rid of hotel 28 and hotel 77 based on the plots
df = df.query("unique_id not in ['hotel_28', 'hotel_77']")
plot_series(df, engine="matplotlib", max_ids=18)
