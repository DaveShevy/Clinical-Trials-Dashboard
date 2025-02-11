# Clinical Trials Data Pipeline and AI Analysis
# This is a work in Progress Project.
- Developed the Microsoft Fabric Pipeline to extract data from the AACT (Aggregate Analysis of ClinicalTrials.gov) database and create an automated data pipeline in Microsoft Fabric for Power BI dashboards.
- Chose Microsoft Azure OpenAI as the LLM based on preliminary testing and cost analysis. (Need to do testing to see if we need to fine-tune the model for higher accuracy extraction)
- Developed a strong understanding of Clinical Trials data and the AACT database.



## Purpose
Improve the research experience at ClinicalTrials.gov by providing a visual dashboard with up-to-date clinical trial information. Additionally, an AI-powered text parsing module extracts structured insights from eligibility criteria, enhancing the search experience. Collaboration with Stakeholders will be important to determine the data story of the dashboard, currently its about a specific disease and the clinical trials associated with it.


## Key References
https://aact.ctti-clinicaltrials.org/data_dictionary
https://aact.ctti-clinicaltrials.org/schema

## Overview
This project extracts data from the AACT (Aggregate Analysis of ClinicalTrials.gov) database and creates an automated data pipeline in Microsoft Fabric for Power BI dashboards. The data refreshes weekly, ensuring up-to-date clinical trial information. Additionally, an LLM can process unstructured eligibility criteria, extracting key insights.

## Features
- **Automated Data Ingestion**: Extracts relevant clinical trial data from AACT. (Pipeline Created in Microsoft Fabric)
- **Filtered Data Export**: Saves structured data (studies, sponsors, facilities, interventions) to Excel. (After testing, will be integrated into Microsoft Fabric)
- **Microsoft Fabric & Power BI**: Enables a visual dashboard with scheduled refreshes. (Weekly)
- **AI-Powered Text Parsing**: GPT-4 to extract structured insights from eligibility criteria.

## Data Extraction
- Connects to the AACT PostgreSQL database.
- Filters studies related to **breast cancer, type 2 diabetes, and Alzheimer’s disease**.
- Exports tables (e.g., studies, sponsors, outcomes, facilities, eligibility criteria) to Excel.

## AI Processing
- Tested with DeepSeek, OpenAI, and Hugging Face models.
- Uses **GPT-4** to extract structured information from eligibility criteria.
- Outputs structured JSON with:
  - Inclusion/exclusion criteria.
  - Special condition flags (e.g., "BRCA mutation", "HER2").
- Includes a cost estimation module for AI usage. (Per Token Usage)

## Setup & Requirements
### Prerequisites
- Python (>= 3.8)
- PostgreSQL client
- Required Python packages:
  ```sh
  pip install pandas sqlalchemy transformers torch openai tiktoken
  ```

### Environment Variables
Set up database credentials in the script:
```python
DB_HOST = "aact-db.ctti-clinicaltrials.org"
DB_PORT = 5432
DB_NAME = "aact"
DB_USER = "YOUR_USERNAME"
DB_PASS = "YOUR_PASSWORD"
```

### Running the Notebook
1. Ensure PostgreSQL access to AACT.
2. Run the extraction functions to pull clinical trials data.
3. Process eligibility criteria with AI models.
4. Export results to Excel for Power BI visualization.

## Future Enhancements
- Implement Azure OpenAI for scalable AI parsing.
- Integrate within the current Microsoft Fabric pipeline.
- Expand data filtering criteria, and discuss with Stakeholders who actual use ClinicalTrials.gov about how to improve there research experience.


