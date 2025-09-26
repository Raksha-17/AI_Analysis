-------Data Exploration------------

/*  Job market insights    */

SELECT *
FROM `ai-analysis-472316.my_project_ai_analysis.ai_job_market_insights`;

/*   Global AI impact  */

SELECT *
FROM `ai-analysis-472316.my_project_ai_analysis.global_ai_impact`;

------Improve data quality checks (suggested additions)
/* Count nulls per key column */

SELECT
  SUM(CASE WHEN Industry IS NULL THEN 1 ELSE 0 END) AS missing_industry,
  SUM(CASE WHEN AI_Adoption_Level IS NULL THEN 1 ELSE 0 END) AS missing_adoption_level,
  SUM(CASE WHEN Salary_USD IS NULL THEN 1 ELSE 0 END) AS missing_salary,
  SUM(CASE WHEN Country IS NULL THEN 1 ELSE 0 END) AS missing_country
FROM `ai-analysis-472316.my_project_ai_analysis.ai_job_market_insights`;

/* Check distinct counts to validate the number of unique hosts/listings */

SELECT COUNT(DISTINCT Country) AS distinct_countries,
       COUNT(DISTINCT Industry) AS distinct_industries
FROM `ai-analysis-472316.my_project_ai_analysis.ai_job_market_insights`;

-------Make queries explicit and robust
/* Jobs by industry and AI adoption level (explicit columns)*/

SELECT
  Industry AS industry,
  AI_Adoption_Level AS ai_adoption_level,
  COUNT(*) AS total_jobs
FROM `ai-analysis-472316.my_project_ai_analysis.ai_job_market_insights`
GROUP BY Industry, AI_Adoption_Level
ORDER BY Industry, AI_Adoption_Level;

/* Validation and safety checks */
/*Basic counts to ensure you’re not duplicating joins*/

SELECT
  (SELECT COUNT(*) FROM `ai-analysis-472316.my_project_ai_analysis.ai_job_market_insights`) AS jobs_rows,
  (SELECT COUNT(*) FROM `ai-analysis-472316.my_project_ai_analysis.global_ai_impact`) AS impact_rows;

/*Spot-check sums by country for sanity*/

SELECT country, ROUND(SUM(Job_Loss_Due_to_AI_PERCENT),2) AS sum_impact
FROM `ai-analysis-472316.my_project_ai_analysis.global_ai_impact`
GROUP BY country
LIMIT 20;
