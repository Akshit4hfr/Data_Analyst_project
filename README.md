# Data_Analyst_project

Before performing exploratory analysis, the raw dataset was carefully cleaned and standardized to ensure accuracy, consistency, and reliability. This stage focused on transforming the original Kaggle layoffs table into a structured, analysis-ready format using SQL best practices.

The process began by creating a staging table to preserve the raw data while allowing safe experimentation and transformation. All cleaning operations were performed on this staging layer, ensuring that the original dataset remained intact for reference or rollback.

Duplicate detection was handled using ROW_NUMBER() window functions partitioned across all relevant fields, including company name, location, industry, layoff counts, dates, funding stage, and country. Records flagged with duplicate row numbers were removed after validation, resulting in a deduplicated dataset stored in a second staging table.

Next, the project focused on data standardization and error correction. Blank industry values were converted to NULL for easier handling, then populated by joining rows belonging to the same company that contained valid industry information. Industry naming inconsistencies—such as multiple variations of “Crypto”—were standardized into a single category. Country names were cleaned by trimming punctuation, and dates were converted from text format into proper SQL DATE fields using STR_TO_DATE.

Null value treatment was approached conservatively. Fields such as total_laid_off, percentage_laid_off, and funds_raised_millions were intentionally left unchanged when missing, as these NULLs carry analytical meaning and are useful during later aggregation and trend analysis.

Finally, records that lacked both layoff counts and percentage data were removed, since they provided no actionable insight for analysis. Temporary helper columns used for duplicate detection were dropped, leaving behind a streamlined, production-ready table.

This cleaning phase demonstrates real-world data preparation skills, including staging strategies, duplicate handling, standardization, null management, and schema refinement—core competencies for any Data Analyst working with messy, real business datasets.
