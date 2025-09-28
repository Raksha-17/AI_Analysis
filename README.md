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

I will follow the steps of the data analysis process: [Ask](https://github.com/Raksha-17/AI_Analysis/blob/main/README.md#ask), [Prepare](https://github.com/Raksha-17/AI_Analysis/blob/main/README.md#prepare), [Process](https://github.com/Raksha-17/AI_Analysis/blob/main/README.md#process), [Analyze](https://github.com/Raksha-17/AI_Analysis/blob/main/README.md#analyze), [Share](https://github.com/Raksha-17/AI_Analysis/blob/main/README.md#share) and [Act](https://github.com/Raksha-17/AI_Analysis/blob/main/README.md#act).

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

5.Validation and safety checks - Basic counts to ensure you’re not duplicating joins.

<img width="1906" height="264" alt="7" src="https://github.com/user-attachments/assets/56c8e688-50c9-4272-9584-b501c609feb7" />

6.Spot-check sums by country for sanity.

<img width="1874" height="264" alt="8" src="https://github.com/user-attachments/assets/ba6eb68d-f49c-481d-b59a-6be30fedee9d" />


## Analyze
SQL Query: [Data Analysis](https://github.com/Raksha-17/AI_Analysis/blob/main/Data_Analysis)  

The data is stored appropriately and is now prepared for analysis. I queried multiple relevant tables for the analysis and visualized them in Tableau. 

The analysis question is:

1. Regions with strongest adoption signals and growth potential.
2. Industries with highest cumulative AI impact and corresponding workforce implications.
3. Salary dynamics by industry and adoption level to inform talent strategy and benchmarking.
4. Relationships between AI adoption rate and job loss to guide policy, reskilling, and program design. 

* ai_job_market_insights: Jobs by industry and AI adoption level.
  
<img width="1874" height="232" alt="11" src="https://github.com/user-attachments/assets/93edaff0-e44e-44fe-8475-481caa592b39" />

AI Adoption level is high in Healthcare, Tech and Manufacturing.

* Average salary by role and adoption level (safe median).
  
<img width="1874" height="232" alt="12" src="https://github.com/user-attachments/assets/96e6c50a-3a1f-4035-aae2-b5744e50f3a5" />

When Adoption rate is lower, avg_salary is high for AI researcher, HR manager, Operations Manager, Sales Manager, Product Manager and Software Engineer; When Adoption rate is higher, avg_salary is high for Cybersecurity Analyst, Data Scientist,Marketing Specialist and UX Designer.

* ai_job_market_insights: Regions with strongest growth projection, Assuming: Region and Job_Growth_Projection (as a percentage or index).

<img width="1874" height="264" alt="13" src="https://github.com/user-attachments/assets/a2b39329-204b-444e-845d-152d46470552" />

Region with Strongest Growth Projection is Tokyo, New York, Berlin and Toronto.

* global_ai_impact: Impact by country and Industry.

<img width="1874" height="232" alt="14" src="https://github.com/user-attachments/assets/b8ed150f-dee6-4e13-ad00-9ce333a9ef7e" />

Highest Impact in UK in Media, France in Gaming, Japan in Manufacturing.

* global_ai_impact: Adoption vs. impact.

<img width="1874" height="232" alt="15" src="https://github.com/user-attachments/assets/345e4f31-fd9f-4416-ac9e-b24c41a06d1a" />

AI Adoption rate and its Impact is high in Gaming, Retail , Manufacturing.
  
* Yearly total impact by country and domain (global_ai_impact).

<img width="1874" height="232" alt="16" src="https://github.com/user-attachments/assets/29704c24-359e-481e-b3db-0f68f142ce8c" />

In 2020 Germany Manufacturing Industry had the highest impact followed by China in Legal in 2025 and India in Media in 2024.

* Yearly adoption/readiness vs. impact (global_ai_impact). 

 <img width="1874" height="232" alt="17" src="https://github.com/user-attachments/assets/3b51eef7-de09-4203-9a22-2e757cd84ebc" />

China, Japan, South Korea has highest avg_impact in 2021,2025,2024.

* Yearly top domains by total impact (global_ai_impact).

<img width="1874" height="264" alt="18" src="https://github.com/user-attachments/assets/1f1eca61-a266-437b-9d5d-784f12cfd200" />

Gaming, Manufacturing and Retail has highest impact on avg.

* Cross-dataset joins (correlations) Example: Link ai_job_market_insights with global_ai_impact (using country/industry keys).

<img width="1874" height="232" alt="19" src="https://github.com/user-attachments/assets/8d3109cf-f553-4099-8ee2-fa6d9ed0bff6" />

 AI Adoption level is high in Manufacturing in Berlin, Healthcare in Dubai, Retail in London.

* Top-N and profiling patterns. Top 5 domains by total impact (global_ai_impact).

<img width="1874" height="264" alt="20" src="https://github.com/user-attachments/assets/7fec1c59-a486-483a-aeaf-2d202128c6fa" />

Gaming, Media, Manufacturing, Automotive.

* Top-3 roles by salary within each adoption level (ai_job_market_insights).
  
<img width="1874" height="232" alt="21" src="https://github.com/user-attachments/assets/7fd25448-384b-4b99-a762-d85c388e6721" />

Salary is high for Marketing Specialist, Data Scientist and UX Designer.

## Share

Data Visualization: [Tableau]()  

* Regions with strongest adoption signals are Berlin, Tokyo, New York, Toronto, Dubai, London. (as observed)
* Regions with high adoption but lower immediate impact - Potential resilience in job mix or effective upskilling; study transferable skills and cross-industry mobility.

Regional growth potential indicators (dashboard prompts)

Year-over-year growth in AI_Adoption_Rate_PERCENT
Projected openings or job_growth_projection (index)
Average salary growth for AI-forward roles

* Top cumulative impact domains (by Job_Loss_Due_to_AI_PERCENT across years) are Gaming, Media, Manufacturing, Retail, Automotive (as observed)

High adoption + high impact → displacement risk; requires reskilling, role redesign, safety nets.
Moderate adoption + high impact → focus on rapid upskilling and internal mobility.
Low adoption + moderate impact → monitor for tipping points; proactive capability-building.
Cross-industry patterns to watch

Rising demand for data-centric and security roles (Data Scientist, Cybersecurity Analyst) in mature markets.
Emerging premium roles in marketing, UX, and product management as AI augments product teams.
3) Salary dynamics by industry and adoption level
Key observation patterns

When adoption is high, salaries rise for AI-forward roles (e.g., Data Scientist, Cybersecurity Analyst, AI Researchers in select markets).
When adoption is lower, some roles (AI Researchers, HR/Operations Managers, Sales Managers, Product Managers, Software Engineers) show relatively higher average salaries (likely scarcity in those markets or premium seniority).
Implications for talent strategy

Map compensation bands by industry and adoption tier; adjust for regional cost of living.
Prioritize global sourcing for high-demand roles in markets with rising adoption but limited local supply.
Invest in upskilling programs to move workers from lower-adoption to higher-value AI-enabled roles.

Proactive reskilling programs in high-adoption regions/industries with rising loss.
Cross-training to create new-role pipelines (e.g., AI ops, AI governance, data ethics).
Pairing public funding with private incentives for displaced workers.
Alternative measures to enrich insight

 ## Act

Regions with strongest adoption signals and growth potential - Action: Prioritize regional talent initiatives, partnerships, and incubators in these hubs.

Regional growth potential indicators - Action: Target investment in regions with rising adoption AND rising demand signals.

Industries with highest cumulative AI impact and workforce implications Action: Prioritize retraining and new-role creation in these domains; design industry-specific transition programs.
Workforce implications by industry

### Recommendations:

The top revenue contributors to Airbnb in Jersey City are entire homes from Ward E, Ward F, Ward C, Ward D by far, to maximize revenue, it is essential that Airbnb makes the most out of the potential of these listings. Potential areas to be optimized and explored are:

- The prices of entire homes in top four neighbourhoods should reflect the large demand;

- Help superhosts price their properties in a way that reflects their status;

-  Help instantbookable listings price properly taking into consideration the convenience they are providing;

- Help highly rated listings price properly to reflect their high ratings and superior quality of services.

Limitations and assumptions:

- This analysis assumes that hosts that have not been reviewed since November 2022 are inactive;

- Revenue potential is only measured by the potential revenue coming in the next 30 days, with the assumption that most visitors book their stays less than 30 days in advance.
