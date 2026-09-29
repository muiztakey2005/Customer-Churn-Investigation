# Validation and Key Decisions

## 1. Project

**Project:** Customer Churn Investigation
**Dataset:** IBM Telco Customer Churn public dataset
**Analysis Environment:** Python / Jupyter / Google Colab

## 2. Data Quality Validation

The dataset was checked before and after cleaning.

### Validation Results

* Dataset shape: 7,043 rows × 21 columns
* Missing values after cleaning: 0
* Duplicate rows: 0
* Duplicate customer IDs: 0
* `TotalCharges` data type after cleaning: `float64`
* All 7,043 customer records were retained.

## 3. Key Data-Cleaning Decision

`TotalCharges` contained 11 blank values.

Investigation showed that all 11 affected customers had:

* `tenure = 0`
* A valid `MonthlyCharges` value
* `Churn = No`

Based on this observed pattern, the blank `TotalCharges` values were set to `0`.

This is treated as a data-cleaning decision based on the observed dataset pattern. The analysis does not claim knowledge of the original data-generation process.

## 4. Analytical Decisions

### Tenure Grouping

Customer tenure was grouped into:

* 0–12 months
* 13–24 months
* 25–48 months
* 49–72 months

This grouping was used to make churn patterns easier to interpret and support customer segmentation.

### Customer Segmentation

Customers were segmented primarily using:

* Tenure group
* Contract type

A combined high-risk segment was additionally examined using:

* Tenure group
* Contract type
* Payment method

## 5. Validation of Analytical Findings

The analysis examined:

* Overall churn distribution
* Tenure and churn
* Contract type and churn
* Monthly charges and churn
* Internet service and churn
* Payment method and churn
* Customer segments and churn
* Combined high-risk customer segment

The findings are descriptive associations observed in the dataset.

## 6. Interpretation Boundary

The analysis identifies characteristics associated with higher or lower observed churn rates.

The results should **not** be interpreted as proof that a particular characteristic directly causes churn.

The proposed retention actions are therefore hypotheses for further investigation rather than proven causal interventions.

## 7. Limitations

* The analysis is based on a single public dataset and may not generalize to every customer population.
* The analysis is descriptive and does not include a predictive churn model.
* Important factors such as customer satisfaction, support interactions, competitor activity, and service experience are not available in the dataset.
* Financial impact of churn and retention actions was not measured.
* Smaller customer segments require cautious interpretation.

## 8. Recommended Next Steps

1. Collect customer satisfaction and support-interaction data.
2. Investigate reasons for early-tenure churn.
3. Test retention interventions using controlled experiments.
4. Develop a predictive churn model.
5. Estimate the financial impact of churn and retention actions.
6. Monitor churn patterns over time.

## 9. Reproducibility

The project is maintained in a version-controlled GitHub repository.

The repository contains:

* Analysis notebook
* Raw dataset
* README documentation
* Python package requirements
* Project documentation

The notebook can load the dataset from the repository's local `data/raw/` path when executed locally and can fall back to the public IBM dataset URL when that local path is unavailable.

## 10. Review Status

The project includes:

* Defined stakeholder and scope
* Documented data-cleaning decisions
* Data-quality validation
* Business-question-driven EDA
* Evidence-based observations
* Customer segmentation
* Retention opportunities
* Limitations and next steps
* Reproducibility documentation
