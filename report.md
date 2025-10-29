# Report: Insurance Supervision Analysis
The following report contains recommendations for the Insurance Supervision Manager on resource allocation towards firms, based on some preliminary analysis performed on the dataset provided.
## Data Cleaning
The following steps were undertaken to clean the data:
- From the 'General' sheet, firms (rows) that had all 0's were dropped.
- From the 'Underwriting' sheet, firms (rows) that had all 0's were dropped.
- This resulted in 306 rows in the 'General' sheet, and 243 rows in the 'Underwriting' sheet, each row corresponding to a single firm. Initially, both sheets contained 325 firms.
- Following this inital step, we merge the original (wide-format) data across both sheets into a single pandas dataframe. This results in 226 unique firms for our analysis.
- Data finally pivoted to long format for easier comparisons and analysis. This results in data with 4 columns - 'Firm', 'Year', 'Metric' and 'Value'.
 maybe show data here if there's space.

## Prioritisation Methodology


## Errors and Outlier Analysis
Detail the process of identifying and addressing errors and outliers in the dataset, including statistical methods or visualization techniques used.