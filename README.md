# Power BI Customer Churn Analysis

**Project Status:** Completed (October 2025)

[![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?style=for-the-badge&logo=Power%20BI&logoColor=black)](https://powerbi.microsoft.com/en-us/)
[![DAX](https://img.shields.io/badge/DAX-2E8540?style=for-the-badge)](https://docs.microsoft.com/en-us/dax/)



---

### Dashboard Preview
![Customer Churn Dashboard](images/Dashboard Image.png)

---

### Table of Contents
1. [Project Overview](#1-project-overview)
2. [Dataset](#2-dataset)
3. [Tools Used](#3-tools-used)
4. [Data Cleaning and Transformation](#4-data-cleaning-and-transformation)
5. [Data Analysis and DAX Measures](#5-data-analysis-and-dax-measures)
6. [Key Insights](#6-key-insights)
7. [Actionable Recommendations](#7-actionable-recommendations)
8. [How to Use This Repository](#8-how-to-use-this-repository)
9. [Contact](#9-contact)

---

### 1. Project Overview

The objective of this project is to analyze the key drivers of customer churn for a telecommunications company. By identifying the primary factors contributing to customer attrition, the business can develop targeted strategies to improve retention.

This Power BI dashboard provides an interactive and consolidated view of various customer attributes and their relationship with churn, enabling stakeholders to explore the data and make informed decisions.

### 2. Dataset

This project utilizes the **Telco Customer Churn** dataset, a popular public dataset from Kaggle.
* **Source:** [Kaggle](https://www.kaggle.com/datasets/blastchar/telco-customer-churn)
* The dataset contains information about 7,043 customers, including their demographics, subscribed services, account information, and churn status.

### 3. Tools Used

* **Power BI Desktop:** For data modeling, analysis, and dashboard creation.
* **Power Query:** For data extraction, transformation, and loading (ETL).
* **DAX (Data Analysis Expressions):** For creating calculated measures and columns to enhance analysis.

### 4. Data Cleaning and Transformation

During the ETL phase in Power Query, the following data cleaning and preparation steps were performed:
* **Data Type Correction:** Ensured all columns were assigned the correct data types (e.g., TotalCharges converted from text to decimal).
* **Handled Inconsistencies:** Standardized categorical data by replacing "No internet service" with "No" across multiple service columns (`OnlineSecurity`, `TechSupport`, etc.) to simplify analysis.
* **Null Value Management:** Addressed blank values in the `TotalCharges` column, associating them with new customers (zero tenure) and replacing them with 0.

### 5. Data Analysis and DAX Measures

Several key DAX measures were created to power the dashboard visuals:
* **Churn Rate:** A central KPI to calculate the overall percentage of customers who have churned.
    ```dax
    Churn Rate = DIVIDE([Churned Customers], [Total Customers])
    ```
* **Total Customers:** A simple count of all customer IDs.
    ```dax
    Total Customers = COUNTROWS(Customers)
    ```
* **Churned Customers:** A count of customers who have churned, used extensively in the decomposition tree and other visuals.
    ```dax
    Churned Customers = CALCULATE([Total Customers], Customers[Churn] = "Yes")
    ```

### 6. Key Insights

The analysis revealed several critical factors that strongly influence customer churn:
* **Contract Type is the Biggest Driver:** Customers on **Month-to-Month** contracts have a dramatically higher churn rate (over 42%) compared to those on One-year or Two-year contracts (less than 12% and 3% respectively).
* **New Customers are High-Risk:** Churn is heavily concentrated in the first few months of tenure. Customers are most likely to leave within the first 1-5 months.
* **Payment Method Influences Loyalty:** Customers using **Electronic check** as their payment method churn at a much higher rate (45%) than those on automatic payment methods like credit cards or bank transfers (~15%).
* **Service Gaps Increase Churn:** Customers without **Tech Support** are more than twice as likely to churn. Similarly, Fiber Optic customers, while paying more, also have a higher churn rate, suggesting potential service quality or pricing issues.

### 7. Actionable Recommendations

Based on the insights, the following strategic recommendations are proposed:
1.  **Promote Long-Term Contracts:** Develop a targeted marketing campaign to incentivize Month-to-Month customers to switch to One-year or Two-year plans, perhaps by offering a promotional discount or additional service perks.
2.  **Enhance New Customer Onboarding:** Implement a proactive customer engagement strategy for the first three months to address any early-stage issues and demonstrate the value of the service, thereby reducing early tenure churn.
3.  **Incentivize Automatic Payments:** Offer a small discount or a one-time credit for customers who switch from manual payment methods like Electronic Check to automatic payments to increase customer "stickiness."

### 8. How to Use This Repository

1.  **View the Live Dashboard:** Click the link at the top of this README to interact with the dashboard directly in your browser.
2.  **Explore the Project File:**
    * Clone this repository to your local machine.
    * Download and install [Power BI Desktop](https://powerbi.microsoft.com/en-us/desktop/).
    * Open the `Telco_Churn_Analysis.pbix` file to view the full report, data model, and DAX measures.

### 9. Contact

Created by **Niranjan Kumar Chaurasiya** 

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/niranjankumarchaurasiya999/)
[![GitHub](https://img.shields.io/badge/GitHub-100000?style=for-the-badge&logo=github&logoColor=white)](https://github.com/niranjan77978)
