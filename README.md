# Hotel Booking Cancellation Analysis
End-to-end project using Predictive and Causal analysis for Hotel Booking Cancellation

#### Group Members: 
- Oyundari Batbayar
- Jaya Chaturvedi
- Vinay Govias
- Kaz Hayashi
- Reo Paul Jackson

## Problem Statement

In the fast-paced hospitality industry, effectively managing hotel cancellations is crucial for maintaining revenue and enhancing guest experiences. Industry leaders emphasize a multifaceted strategy that includes optimizing revenue through strategic overbooking, building customer loyalty with effective communication, and implementing flexible cancellation policies. Integrating these practices with machine learning tools allows hotels to reduce the financial impact of cancellations and gain a competitive edge by meeting customer needs and ensuring high satisfaction levels.

## Hypothesis

In our project, we aim to tackle the issue of handling booking cancellations in the hotel industry by employing a robust modeling framework. This includes a classification model to predict the likelihood of cancellations and a causal inference model to understand the impact of deposit policies on cancellation behavior. Through this approach, we aim to refine reservation policies and adjust deposit requirements to decrease cancellations and boost revenue.

## Overview of Dataset

Our dataset, sourced from Kaggle (https://www.kaggle.com/datasets/arezaei81/hotel-bookingcvs), comprises 36 columns with a mix of 20 numeric and 16 categorical variables. These columns fall into five main categories: customer details, hotel information, amenities offered, booking specifics, and the target variable of cancellation status. 

## Data Preparation

**Data Cleaning:**
- Columns that cause data leakage such as 'reservation_status_date', 'reservation_status', and 'assigned_room_type' were removed.
- Sparse columns with over 10% missing values, like 'Company' and 'Agent', were dropped.
- Personally Identifiable Information (PII) was removed to maintain privacy.

**Feature Engineering:**
- New features tracking previous customer bookings were created.
- The 'Country' feature was refined to include only those with significant instances.

**Outlier Detection:**
- Box plots were used for visualization and the Isolation Forest algorithm identified and removed 2% of the data as outliers.

**Feature Selection:**
- The Random Forest algorithm assessed feature importance, and the least significant features were removed to optimize the dataset.

**Class Imbalance Solutions:**
- Techniques like Random Oversampling and SMOTE were used to balance the dataset.

## Modeling Process

We followed a rigorous multi-step modeling process to ensure the robustness of our predictive analysis:

1. **Benchmarking a Variety of Models:** A comprehensive suite of models was benchmarked to establish baseline performances. The models tested included:
   - DummyClassifier (as a baseline)
   - LogisticRegression
   - KNeighborsClassifier (KNN)
   - RandomForestClassifier
   - CatBoostClassifier
   - AdaBoostClassifier
   - XGBoostClassifier
   - LightGBMClassifier
   - A Stacked Model incorporating the above models

2. **Data Splitting:** The dataset was split into training and testing sets with a 70-30 train-test split, ensuring adequate data for learning while also maintaining a substantial evaluation set.

3. **Preprocessing:** The data was preprocessed to standardize features and address class imbalances. Techniques like Random Oversampling and SMOTE were employed to achieve a balanced dataset.

4. **Hyperparameter Tuning:** Extensive hyperparameter tuning was performed using cross-validation and grid search methods, with a focus on improving the ROC-AUC score.

5. **Model Evaluation:** The performance of the models was evaluated using a range of metrics, including accuracy, precision, recall, F1 score, and the ROC-AUC. ROC and Precision-Recall (PR) curves were plotted to visualize model performance.

6. **Model Selection:** After evaluating all models, the one with the best performance metrics was selected for further analysis and deployment.


## Key Takeaways

- RandomForest model exhibited significant improvement post-tuning.
- LightGBM and KNN also showed commendable performance.
- The Stacked Model demonstrated robust general performance.

## Results and Interpretation

Our chosen model, Random Forest model, has the highest accuracy of 0.880 and a ROC-AUC score of 0.865 post fine-tuning, suggesting that this model has strong predictive accuracy and the ability to effectively differentiate between the target classes.

### Random Forest Feature Importance
- The Random Forest model identified lead time as the most significant predictor of cancellation, implying that the longer the period between booking and the actual stay, the higher the chance of cancellation.
- The average daily rate was the next most crucial factor, indicating that more expensive bookings have a higher cancellation rate.

### SHAP Analysis
- The SHAP analysis revealed insights into the impact of various features on the likelihood of a booking cancellation.
- Key factors included customer nationality, with some nationalities showing a higher propensity to cancel, and the hotel's deposit policy, where non-refundable deposits significantly affected cancellation decisions.
- Additionally, special requests made by customers were linked to a higher commitment to the booking, suggesting that customers who make special requests are less likely to cancel.

Both analyses underscore the importance of considering a range of factors when predicting booking cancellations and tailoring hotel policies accordingly.

## Causal Inference

Here, we propose a dynamic deposit policy, categorized by customer sensitivity to deposits, aiming to maximize successful reservations while minimizing cancellations.

## Causal Inference Modeling

- Employing the T-learner approach to estimate CATE/ITE.
- Fit different models on T1 and T0 groups (two models; it is T-learner)
- Calculating differences in outcomes to assess CATE/ITE for customer segments.

## Results of Causal Inference

The causal inference analysis provided actionable insights with actual values indicating how different subgroups are affected by deposit policies:

- **First-Time Guests (Is Repeated Guest (0))**
  - CATE Estimate: -0.56, indicating that first-time guests are significantly more likely to cancel if no deposit is required.

- **Distribution Channel**
  - Direct: CATE Estimate: -0.63
  - Corporate: CATE Estimate: -0.44
  - TA/TO: CATE Estimate: -0.56
  - GDS: CATE Estimate: -0.71, highlighting that guests booking through Global Distribution Systems (GDS) are particularly sensitive to deposit requirements, likely due to the higher volume and potential for loss.

- **Market Segment**
  - Groups: CATE Estimate: -0.50
  - Offline TA/TO: CATE Estimate: -0.69
  - Complementary: CATE Estimate: -0.78, suggesting that guests with complimentary stays are very unlikely to cancel as they do not want to miss the trip nor lose a deposit.
  - Aviation: CATE Estimate: -0.56

These results suggest that a dynamic deposit policy could be beneficial, taking into account the different sensitivities of various customer segments to deposit requirements.

## Findings

- The effect of deposit requirements on cancellation rates varies across different customer segments and booking conditions.
- Build policies that cater to the specific needs and sensitivities of different customer groups.
- By tailoring deposit requirements, hotels can optimize their booking to enhance customer satisfaction and revenue stability.
  
## Financial Implications from Causal Inference

In hospitality management, establishing a robust framework for strategic decision-making is crucial to navigate the complexities of guest booking dynamics effectively. The step-by-step framework, introduced in the Financial Implications report, offers a structured approach to assess the financial impact of deposit requirements on customer behavior. 

## Results

- The ROI for implementing a deposit policy for first-time hotel guests is estimated to be 31.4%.
- For every dollar spent on managing the deposit process, the hotel gets a return of $31.40 in increased revenue and net gains from deposits.
- The direct application of CATE to estimate reduction in cancellations is considered simplified. Therefore, there is a caution to reconsider the deposit policy as it could potentially reduce the overall number of successful bookings.

## Conclusion and Next Steps

In conclusion, the judicious application of predictive modeling and causal inference techniques, particularly CATE, provides a robust framework for decision-makers in the hospitality industry. Our successful illustration of this approach underscores the profound potential for such data-driven strategies to enhance profitability and operational efficiency. Future endeavors may build upon this foundation, incorporating more granular data to refine and personalize deposit strategies, thus further fortifying the financial resilience of hotels against the perennial challenge of booking cancellations.

### Next Steps

- **Model Deployment**: Create a user interface for the hotel management team to easily access and interpret model predictions.
- **Additional Research**: Validating the impact of requiring a deposit on successful reservation rates requires further research since the dataset only includes data for completed reservations.
- **Optimizing Deposit Requirement**: With impact of deposit on cancellation and successful bookings, we can formulate an optimization problem to find the best mix of deposit policies for each customer

---
## How to Run this Project

- Final_Project_Notebook.ipynb contains every code written for the preprocessing, EDA, predictive, and causal analyses.
- Financial_Analysis__ROI_Estimation.pdf includes financial implications and ROI estimation derived from causal analysis.
- Presentation Deck.pdf contains presentation slides for this project.
- hotel_booking.csv is the dataset used for this project.
---

## Contributing
We encourage contributions to this project. If you have suggestions for improving the models or the analysis, please fork this repository, make your changes, and submit a pull request. For significant changes, please open an issue first to discuss what you would like to change.



