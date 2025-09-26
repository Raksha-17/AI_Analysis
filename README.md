# Impact_of_AI_on_Digital_Media_Analysis
Derive actionable insights from two datasets — Global AI Impact and AI Job Market Insights — to inform strategy on AI adoption, market dynamics, and talent planning across countries and industries.

## Introduction
* Goal: Derive actionable insights on global AI impact and job market dynamics to inform strategy (e.g., policy, talent planning, or product focus).
* Scope: Two datasets.
* Global AI impact: country, industry, job_loss_due_to_AI_percent, year, etc.
* AI job market insights: industry, AI_adoption_level, salary_usd, job_title, location, etc.
* Data quality: <2% missingness on key fields per dataset.
* Key insights: identify top 5 industries by impact and top 5 regions by adoption-growth alignment.
* Reproducibility: end-to-end notebook or SQL workflow that outputs a single KPI sheet.

I will follow the steps of the data analysis process: Ask, Prepare, [Process](https://github.com/Raksha-17/AI_Analysis/blob/main/Data_Exploration), [Analyze](https://github.com/Raksha-17/AI_Analysis/blob/main/Data_Analysis), Share and Act.

### Quick links:
Data Source: [Impact of AI on Digital Media (2020-2025)] (https://www.kaggle.com/datasets/atharvasoundankar/impact-of-ai-on-digital-media-2020-2025)

### SQL Queries:

* [Data Exploration](https://github.com/Raksha-17/AI_Analysis/blob/main/Data_Exploration) 
* [Data Analysis](https://github.com/Raksha-17/AI_Analysis/blob/main/Data_Analysis)  
  
Data Visualizations: [Tableau]()  

## Ask
### Business Task
* Quantify cross-country and cross-industry AI impact and link it to adoption and salary dynamics.
* Provide prioritized insights for decision-makers on where AI adoption is strongest and where potential impact is highest.

### Inputs / Outputs:
#### Inputs:
* ai_job_market_insights: Industry, AI_Adoption_Level, Job_Title, Salary_USD, Location, Country, Region, etc.
* global_ai_impact: Country, Industry, Job_Loss_Due_to_AI_PERCENT, AI_Adoption_Rate_PERCENT, Year, etc.

### Analysis
#### Outputs:
* KPI sheets per dataset (e.g., average salary by role/adoption, total impact by country/industry, adoption vs. impact maps).
* Cross-dataset correlations (e.g., adoption_rate vs. average_impact).
#### Evaluation Metrics:
* Correlation strength (Pearson/Spearman) between adoption and impact.
* Stability of top domains across years.
* Data quality metrics (missingness, duplication rate).

## Prepare
#### Data Sources:
* ai_job_market_insights.csv
* global_ai_impact.csv

#### Data Organization:
* ai_job_market_insights: Industry, AI_Adoption_Level, Job_Title, Salary_USD, Location, Country, Region, Year, possibly other fields.
* global_ai_impact: Country, Industry, Job_Loss_Due_to_AI_PERCENT, AI_Adoption_Rate_PERCENT, Year, etc.
  
## Process:
* Check for missing values in key fields (Salary_USD, Country, Industry, Job_Title, Job_Loss_Due_to_AI_PERCENT).
* Validate consistent naming (Industry, Location/Country synonyms).
#### Access & Compliance:
If sharing externally, mask or aggregate sensitive fields; ensure row-level identifiers aren’t exposed.

### Data Exploration
SQL Query: [1.Data Exploration](https://github.com/Raksha-17/AI_Analysis/blob/main/Data_Exploration) 

Before cleaning the data, I am familiarizing myself with the data to find the inconsistencies.

1. Normalize country/region names; fix typos.
   <img width="1874" height="232" alt="5" src="https://github.com/user-attachments/assets/a56b5bf8-39f5-4e6e-ae2e-381ef5c54ca5" />
   <img width="1874" height="232" alt="6" src="https://github.com/user-attachments/assets/22b197ce-e056-4842-8ba4-65e81194b84c" />

2. Count nulls per key column:
 <img width="1906" height="732" alt="1" src="https://github.com/user-attachments/assets/399758e0-7473-413d-99f6-d6da311911c4" />
3. Check distinct counts to validate the number of unique hosts/listings.
<img width="1906" height="764" alt="2" src="https://github.com/user-attachments/assets/5a24f9c4-b9aa-4588-a16f-f715ca2bc52d" />
4. Make queries explicit and robust - Jobs by industry and AI adoption level (explicit columns).
<img width="1874" height="732" alt="3" src="https://github.com/user-attachments/assets/d0974b3f-64ff-4687-984c-7af96f50b210" />

5. Average salary by role and adoption level (safe median).
<img width="1874" height="732" alt="4" src="https://github.com/user-attachments/assets/8a693c9e-799b-4731-b667-8e5f916a9a8b" />

## Analyze
SQL Query: [Data Analysis](https://github.com/Raksha-17/AI_Analysis/blob/main/Data_Analysis)  

The data is stored appropriately and is now prepared for analysis. I queried multiple relevant tables for the analysis and visualized them in Tableau. 

The analysis question is:

1. Regions with strongest adoption signals and growth potential.
2. Industries with highest cumulative AI impact and corresponding workforce implications.
3. Salary dynamics by industry and adoption level to inform talent strategy and benchmarking.
4. Relationships between AI adoption rate and job loss to guide policy, reskilling, and program design. 

