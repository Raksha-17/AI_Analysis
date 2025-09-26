# Impact_of_AI_on_Digital_Media_Analysis
Derive actionable insights from two datasets — Global AI Impact and AI Job Market Insights — to inform strategy on AI adoption, market dynamics, and talent planning across countries and industries.

## Introduction
####Goal: Derive actionable insights on global AI impact and job market dynamics to inform strategy (e.g., policy, talent planning, or product focus).
####Scope: Two datasets:
####Global AI impact: country, industry, job_loss_due_to_AI_percent, year, etc.
####AI job market insights: industry, AI_adoption_level, salary_usd, job_title, location, etc.
####Data quality: <2% missingness on key fields per dataset.
####Key insights: identify top 5 industries by impact and top 5 regions by adoption-growth alignment.
####Reproducibility: end-to-end notebook or SQL workflow that outputs a single KPI sheet.

I will follow the steps of the data analysis process: Ask, Prepare, Process, [Analyze](), Share and Act.

### Quick links:
Data Source: [Impact of AI on Digital Media (2020-2025)] (https://www.kaggle.com/datasets/atharvasoundankar/impact-of-ai-on-digital-media-2020-2025)

SQL Queries:  

[Data Analysis]()  
  
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
### Data Sources:
ai_job_market_insights.csv ()
global_ai_impact.csv ()

### Data Organization:
* ai_job_market_insights: Industry, AI_Adoption_Level, Job_Title, Salary_USD, Location, Country, Region, Year, possibly other fields.
* global_ai_impact: Country, Industry, Job_Loss_Due_to_AI_PERCENT, AI_Adoption_Rate_PERCENT, Year, etc.
  
## Process:
* Check for missing values in key fields (Salary_USD, Country, Industry, Job_Title, Job_Loss_Due_to_AI_PERCENT).
* Validate consistent naming (Industry, Location/Country synonyms).
### Access & Compliance:
If sharing externally, mask or aggregate sensitive fields; ensure row-level identifiers aren’t exposed.

### Data Exploration
SQL Query: [1.Data Exploration]() 

1. Normalize country/region names; fix typos.
2. Handle missing Salary_USD or Job_Loss_Due_to_AI_PERCENT with imputation or flagging.
3. Growth indicators per country/region if multiple years exist.
4. Adoption bins (Low/Medium/High) based on AI_Adoption_Rate_PERCENT.
5. Quick aggregations to establish baselines (mean salary by industry/adoption, total impact by country).

## Analyze
SQL Query: [Data Analysis]()  

The data is stored appropriately and is now prepared for analysis. I queried multiple relevant tables for the analysis and visualized them in Tableau. 

