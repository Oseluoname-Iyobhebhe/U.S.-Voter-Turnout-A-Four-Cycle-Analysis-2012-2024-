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
The data was cleaned using pandas dataframe in python. The steps taken in the data preparaation process can be found in the file attached.


  ### Research Questions
  The project aimed at answering the following researh questions:
  - Research Question 1: How has the average voter turnout rate (VEP_TURNOUT_RATE and VAP_TURNOUT_RATE) changed across the four election cycles?
  - Research Question 2: Which states consistently exhibit high or low voter turnout rates, and what factors might explain these trends?
  - Research Question 3: How do the percentages of noncitizens and counts of ineligible individuals (prison, probation, parole, felons) correlate with voter turnout rates?
  - Research Question 4: How do ineligibility factors (prison, probation, parole, and felony disenfranchisement) compare between states with the highest and lowest voter turnout rates?


 ### Data Analysis and Visualization
 The data was analysed and visualised using python libraries pandas, matplotlib.plyplot, and seaborn. The steps taken in this process and the results can be found in the file attached. 

### Findings 
- Research Question 1:
Voter turnout has generally increased from 2012 to 2020, peaking in 2020 before slightly declining in 2024. VEP turnout is consistently higher than VAP turnout, highlighting the impact of ineligibility factors. The surge in 2020 likely resulted from heightened political engagement, while the 2024 dip may indicate voter fatigue or changing political dynamics.

- Research Question 2:
State-level turnout varies widely, with states like Hawaii and Oklahoma consistently showing lower participation, while Minnesota and Wisconsin lead in engagement. These differences suggest that factors such as voting laws, accessibility, and civic culture influence turnout. Low-turnout states may benefit from targeted outreach and policy changes.

- Research Question 3:
A strong correlation exists among different forms of voting ineligibility, particularly felony disenfranchisement. Higher noncitizen percentages correlate weakly with lower turnout, but other factors likely contribute. States with the lowest turnout tend to have higher ineligibility rates, reinforcing the impact of restrictive voting laws on participation.

### Recommendations 
- Low-turnout states should implement targeted voter education campaigns to address apathy and misinformation, particularly in communities with historically low participation.

- Implement policies such as early voting, same-day registration, and mail-in ballots to make voting more accessible, especially in states with restrictive election laws.

- States with high ineligibility rates due to felony convictions should consider policy reforms, such as automatic rights restoration upon sentence completion, to reintegrate eligible voters into the electoral process.

- Although noncitizens cannot vote, outreach efforts should focus on encouraging civic participation, such as voter registration drives targeting naturalized citizens and communities with high immigrant populations.

- Policymakers should conduct state-level assessments to identify unique challenges—whether logistical, legal, or social—that prevent eligible voters from participating and implement targeted interventions accordingly.

### Limitations
- Some states may report voter eligibility and turnout data differently, leading to inconsistencies in the analysis.

- While trends were identified, we cannot directly prove that factors like felon disenfranchisement or noncitizen percentages cause lower voter turnout.

- Socioeconomic conditions, voter suppression laws, and political climate were not fully accounted for, though they likely impact turnout.

- Findings apply at the state level but may not reflect local variations within states, such as urban vs. rural differences.

- Turnout can be influenced by specific candidates, key issues, or major events in a given election year, which were not isolated in this study.

- Self-reported or administrative voting records may not capture unregistered eligible voters or other hidden barriers to participation.
  
### References 
United States Elections Project(n.d).Retrieved from https://www.electproject.org/


















