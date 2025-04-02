# U.S.-Voter-Turnout-A-Four-Cycle-Analysis-2012-2024-


## Table of content

- [Project Overview](#project-overview)
- [Data Sources](#data-sources)
- [Tools](#tools)
- [Data Collection](#data-collection)
- [Data Preparation](#data-preparation)
- [Exploratory Data Analysis](#exploratory-data-analysis)
- [Findings](#findings)
- [Recommendations](#recommendations)
- [Limitations](#limitations)
- [References](#references)

### Project Overview
This project examines the dynamics of voter participation in U.S. presidential elections, focusing on four election cycles from 2012 to 2024. The study aims to identify key trends, patterns, and potential factors influencing voter participation rates over this twelve-year period. 

### Data Sources
The data for this project was sourced from [United States Election Project](https://www.electproject.org/), a platform that provides national and state-level voter turnout statistics.

### Tools
Python(Pandas; matplotlib.pyplot; and seaborn)

### Data Collection
The data was downloaded in CSV file from the website

### Data Preparation
The data was cleaned using pandas dataframe in python. specifically, the steps taken in the data preparaation process includes:
- importing the libraries 
  ```python 3
  import pandas as pd
```
- Automating the data cleaning process
As i was dealing with four differnt electoral cycles meaning four different data set, i automated the data cleaning process so as to eliminate repetitive task and improve speed, efficiency, and accuracy.
  ```python 3
def wrangle(filepath, election_year):
    
    df = pd.read_csv(filepath)
    
    drop_columns = ["Unnamed: 3", "ELIGIBLE_OVERSEAS","SOURCE","VOTE_FOR_HIGHEST_OFFICE"]
    
    df = df.drop(columns=[col for col in drop_columns if col in df.columns], errors="ignore")
    
    numeric_cols = [
        "TOTAL_BALLOTS_COUNTED", "VAP", "NONCITIZEN_PCT",
        "INELIGIBLE_PRISON", "INELIGIBLE_PROBATION",
        "INELIGIBLE_PAROLE", "INELIGIBLE_FELONS_TOTAL",
        "VEP", "VEP_TURNOUT_RATE", "VAP_TURNOUT_RATE"
         ]
    cols_to_clean = ["VAP", "INELIGIBLE_PRISON", "INELIGIBLE_PROBATION", 
                 "INELIGIBLE_PAROLE", "INELIGIBLE_FELONS_TOTAL", "VEP"]
    
    df[cols_to_clean] = df[cols_to_clean].apply(lambda x: x.str.replace(',', '').astype(float))
    
    cols_to_fix = ["NONCITIZEN_PCT","VEP_TURNOUT_RATE","VAP_TURNOUT_RATE"]
    
    df[cols_to_fix] = df[cols_to_fix].apply(lambda x: x.str.replace('%','').astype(float))
    
    cols_to_adjust = ["TOTAL_BALLOTS_COUNTED"]
    
    df[cols_to_adjust] = df[cols_to_adjust].astype(str).replace({',': ''}, regex=True).astype(int)
    
    df = df[df["STATE"] != "United States"]
    
    df["Election_Year"] = election_year
    
    return df
```
