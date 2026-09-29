# Customer Churn Investigation

## 1. Project Overview

This project investigates customer churn in a telecommunications subscription dataset. The objective is to identify customer characteristics associated with observed churn, segment customers based on important characteristics, and propose evidence-based retention actions.

The project follows a structured data science workflow covering data understanding, data quality investigation, cleaning, exploratory data analysis, customer segmentation, business insights, retention recommendations, and limitations.

---

## 2. Business Objective

The analysis is intended to support a customer retention or customer success team in understanding:

* The overall level of observed customer churn.
* Which customer characteristics are associated with higher churn.
* Which customer segments show higher observed churn.
* Where targeted retention analysis may be useful.

The analysis is descriptive and does not establish causal relationships.

---

## 3. Dataset

The project uses the IBM Telco Customer Churn public sample dataset.

The dataset contains:

* **7,043 customers**
* **21 columns**
* Customer demographic information
* Subscription and service information
* Contract and payment information
* Monthly and total charges
* Customer churn status

The dataset was accessed from the public IBM repository.

---

## 4. Technology Stack

* Python
* Pandas
* NumPy
* Matplotlib
* Seaborn
* Jupyter / Google Colab

---

## 5. Project Workflow

The analysis follows these stages:

1. Data loading and understanding
2. Initial data inspection
3. Data dictionary creation
4. Data quality investigation
5. Data cleaning
6. Business-question-driven EDA
7. Customer segmentation
8. Combined high-risk segment analysis
9. Retention action recommendations
10. Limitations and next steps

---

## 6. Data Cleaning

The `TotalCharges` column was initially stored as an object because it contained blank values.

The cleaning process included:

* Removing leading and trailing whitespace.
* Replacing blank values with missing values.
* Converting `TotalCharges` to numeric format.
* Investigating the records with missing `TotalCharges`.

The 11 records with missing `TotalCharges` corresponded to customers with zero tenure. These records were retained and their `TotalCharges` values were set to 0 based on the observed data pattern.

Post-cleaning validation confirmed that the dataset contained no remaining missing values, duplicate records, or duplicate customer IDs.

---

## 7. Exploratory Data Analysis

The EDA was structured around business questions rather than isolated visualizations.

### Overall Churn

The dataset contains:

* Retained customers: **5,174 (73.46%)**
* Churned customers: **1,869 (26.54%)**

The overall observed churn rate is therefore **26.54%**.

### Tenure and Churn

Customers with shorter tenure show higher observed churn.

The 0–12 month tenure group has the highest churn concentration, while longer-tenure groups show lower observed churn.

### Contract Type and Churn

Observed churn rates:

* Month-to-month: **42.71%**
* One year: **11.27%**
* Two year: **2.83%**

Month-to-month customers therefore represent an important segment for further retention analysis.

### Monthly Charges and Churn

Average monthly charges:

* Retained customers: **61.27**
* Churned customers: **74.44**

Churned customers therefore have a higher average monthly charge in this dataset.

### Internet Service and Churn

Observed churn rates:

* Fiber optic: **41.89%**
* DSL: **18.96%**
* No internet service: **7.40%**

The fiber-optic segment shows the highest observed churn rate among the internet-service categories.

### Payment Method and Churn

Observed churn rates:

* Electronic check: **45.29%**
* Mailed check: **19.11%**
* Automatic bank transfer: **16.71%**
* Automatic credit card: **15.24%**

The electronic-check segment shows substantially higher observed churn.

---

## 8. Customer Segmentation

Customers were segmented using tenure group and contract type.

The highest observed churn segment is:

**0–12 months + Month-to-month**

* Customers: **1,994**
* Churned: **1,024**
* Churn rate: **51.35%**

Other month-to-month segments also show relatively high observed churn:

* 13–24 months: **37.72%**
* 25–48 months: **32.92%**
* 49–72 months: **26.02%**

This indicates that month-to-month customers have higher observed churn across the analyzed tenure groups.

---

## 9. Combined High-Risk Segment

A focused segment was created using three characteristics:

* Tenure: 0–12 months
* Contract: Month-to-month
* Payment method: Electronic check

Results:

* Customers: **954**
* Churned: **602**
* Churn rate: **63.10%**

This combined segment has a substantially higher observed churn rate than the overall dataset.

The result should be interpreted as an association rather than evidence that these characteristics independently cause churn.

---

## 10. Evidence-Based Retention Opportunities

Based on the observed patterns, the following areas can be investigated:

| Finding                                                | Suggested action                                                          |
| ------------------------------------------------------ | ------------------------------------------------------------------------- |
| High churn among early-tenure month-to-month customers | Develop an early-tenure onboarding and engagement program                 |
| High observed churn among electronic-check customers   | Investigate payment experience and offer easier automatic payment options |
| Higher observed churn among fiber-optic customers      | Investigate pricing, service experience, and support issues               |
| Higher churn among month-to-month customers            | Explore appropriate incentives for longer-term contracts                  |
| 63.10% churn in the combined high-risk segment         | Prioritize this segment for targeted retention analysis                   |

These actions are hypotheses for further validation and should not be interpreted as proven causal interventions.

---

## 11. Limitations

* The analysis identifies associations but does not establish causal relationships.
* The dataset represents a specific customer population and may not generalize to other organizations or time periods.
* The analysis is primarily descriptive and does not include predictive churn modeling.
* Customer satisfaction, support interactions, complaints, competitor activity, and other potentially relevant factors are not available.
* The financial impact of proposed retention actions was not measured.
* Smaller customer segments should be interpreted cautiously.

---

## 12. Next Steps

Potential improvements include:

* Collecting customer satisfaction and support-interaction information.
* Investigating the reasons behind high churn among early-tenure customers.
* Testing retention strategies through controlled experiments.
* Developing a churn prediction model.
* Estimating the financial impact of retention strategies.
* Monitoring churn trends over time.

---

## 13. Reproducibility

The primary analysis is contained in the Jupyter/Google Colab notebook:

```text
notebooks/1_data_understanding_final.ipynb
```

The analysis uses Python and the libraries listed in the Technology Stack section.

The notebook contains the data understanding, cleaning, exploratory analysis, segmentation, findings, recommendations, and limitations.

---

## 14. Responsible Interpretation

The findings in this project are based on observed patterns in the available dataset.

Observed relationships should not be interpreted as proof of causation. Any retention strategy should be validated using additional business data, customer feedback, experimentation, and appropriate performance measurement before implementation.
