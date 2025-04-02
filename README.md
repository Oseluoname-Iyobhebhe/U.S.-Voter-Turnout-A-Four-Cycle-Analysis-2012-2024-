# U.S.-Voter-Turnout-A-Four-Cycle-Analysis-2012-2024-


## Table of content

- [Project Overview](#project-overview)
- [Data Sources](#data-sources)
- [Tools](#tools)
- [Data Collection](#data-collection)
- [Data Preparation](#data-preparation)
- [Research Question](#research-question)
- [Data Analysis and Visualizations](#data-analysis-and-visualizations)
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

- Loading the Dataset
 
```python 3
df1 = wrangle("Turnout_2024G_v0.3.csv", 2024)
df2 = wrangle("Turnout_2020G_v1.2.csv", 2020)
df3 = wrangle("Turnout_2016G_v1.0.csv", 2016)
df4 = wrangle("Turnout_2012G_v1.0.csv", 2012)
```

- Verifying Data Accuracy
  ```python 3
  df1.info()
  df2.info()
  df3.info()
  df4.info()
  ```
  
- Concatenating the dataframes
  ```python 3
  df_clean = pd.concat([df1, df2, df3, df4], ignore_index = True)
  ```

- Saving the clean dataframe into a CSV file
    ``` python 3
    df_clean.to_csv("Voter_Turnout_2016_to_2024.csv", index=False)
    ```

  ### Research Questions
  The project aimed at answering the following researh questions:
  - Research Question 1: How has the average voter turnout rate (VEP_TURNOUT_RATE and VAP_TURNOUT_RATE) changed across the four election cycles?
  - Research Question 2: Which states consistently exhibit high or low voter turnout rates, and what factors might explain these trends?
  - Research Question 3: How do the percentages of noncitizens and counts of ineligible individuals (prison, probation, parole, felons) correlate with voter turnout rates?


 ### Data Analysis and Visualization
 The data was analysed and visualised using python libraries pandas, matplotlib.plyplot, and seaborn. the steps taken in this process include:

 - importing the libraries
   
   ```python 3
   import matplotlib.pyplot as plt
   import seaborn as sns 
   ```

 - Research Question 1
     ```python 3
     turnout_by_year = df_clean.groupby('Election_Year')[['VEP_TURNOUT_RATE', 'VAP_TURNOUT_RATE']].mean().reset_index()
     print(turnout_by_year)
     ```
- Visualizing the Average Voter Turnout Rate by Election Year

```python 3
plt.figure(figsize=(10,6))
sns.lineplot(data=turnout_by_year, x='Election_Year', y='VEP_TURNOUT_RATE', marker='o', label='VEP Turnout Rate')
sns.lineplot(data=turnout_by_year, x='Election_Year', y='VAP_TURNOUT_RATE', marker='o', label='VAP Turnout Rate')
plt.title('Average Voter Turnout Rate by Election Year')
plt.xlabel('Election Year')
plt.ylabel('Turnout Rate (%)')
plt.legend()
plt.grid(True)
plt.show()
```
- Research Question 2
  
```python 3
state_turnout = df_clean.groupby('STATE')[['VEP_TURNOUT_RATE']].mean().reset_index().sort_values(by='VEP_TURNOUT_RATE')
print(state_turnout)
```

_ Visualizing the Average VEP Turnout Rate by State
```python 3
plt.figure(figsize=(12,8))
sns.barplot(x='VEP_TURNOUT_RATE', y='STATE', data=state_turnout, palette='viridis')
plt.title('Average VEP Turnout Rate by State')
plt.xlabel('Average Turnout Rate (%)')
plt.ylabel('State')
plt.show()
```

- Research question 3
  
- ```python 3
  cols = ['NONCITIZEN_PCT', 'INELIGIBLE_PRISON', 'INELIGIBLE_PROBATION', 
        'INELIGIBLE_PAROLE', 'INELIGIBLE_FELONS_TOTAL', 'VEP_TURNOUT_RATE', 'VAP_TURNOUT_RATE']
corr_matrix = df_clean[cols].corr()
print(corr_matrix)
  ```

- Visualizing the Correlation Matrix
