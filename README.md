# Cardio Catch Diseases

## Predicting cardiovascular diseases

![](img_banner_title.png)

# 1. Business Problem.

## Basic Need (Goal):
According to the National Health Service (NHS), Cardiovascular Disease (CVD) is a general term for conditions that affect the heart or blood vessels. Often associated with stroke or heart attack, they are actually consequences of having a CVD, such as coronary heart disease or cerebrovascular disease. For example, clogged arteries occur primarily because of the presence of fat inside of them, which prevents blood from flowing to the heart or brain and can eventually cause a heart attack. According to World Health Organization (WHO), CVDs are the leading cause of death worldwide, an estimated 17.9 million people died in 2019, representing one third of all global deaths. Especially because there are no symptoms and stroke can be the first sign of underlying disease. Therefore, it is important to detect cardiovascular disease as early as possible so that doctors can provide treatment as quickly as possible. An accurate assessment of heart failure risk would help prevent serious heart attacks and improve patient safety. This project aims to develop a disease classification tool with stable accuracy.

## Business Plan: 
Cardio Catch Diseases is a company specialized in detecting heart disease in the early stages. Its business model lies in offering an early diagnosis of cardiovascular disease for a certain price.

Currently, the diagnosis of cardiovascular disease is manually made by a team of specialists. The current accuracy of the diagnosis varies between 55% and 65%, due to the complexity of the diagnosis and also the fatigue of the team who take turns to minimize the risks. The cost of each diagnosis, including the devices and the payroll of the analysts, is around $1,000.00.

The price of the diagnosis, paid by the client, varies according to the precision achieved by the team of specialists.

| Exam Accuracy | Price          | Rules                                    | Example                         |
|:--------------|:---------------|:-----------------------------------------|:--------------------------------|
| Above 50%     | min \$500\.00  | \+\$500 for each additional 5% precision | Precision = 55% \-> \$1,000\.00 |
| Up to 50%     | $0\.00         | N/A                                      | N/A                             |

## Root Cause:
Thus, we see that **different values in the exam precision**, given by the team of specialists, make the company either have a profitable operation, revenue greater than the cost, or an operation with a loss, revenue less than the cost. This instability of the diagnosis makes the company to have an **unpredictable cashflow**.

## Stakeholder:
Cardio Catch Diseases CEO

## Solution plan:

Granularity: Diseases classification

Problem type: Classification

Final product: Diseases diagnosis with a maximum precision

# 2. Business Assumptions.
For this business assume 70K costumers

# 3. Solution Strategy

The strategy adopted was using the model process CRoss Industry Standard Process for Data Mining (CRISP-DM), using the steps below:
1) **Business understanding** – Understand what does the business need, how them make money, disease's concepts, metrics
2) **Data understanding/Data Description** – In this step view data dimensions and types of variables, use statistics metrics to identify data outside the scope of business and clean the data with NA
3) **Feature Engineering** - Create new attributes to better describe the phenomenon that will be modeled. Through variables ap_hi and ap_lo create blood pressure and with height and weight create BMI
4) **Data Filtering** - Using statistical tools to select columns that do not contain information for modeling or that do not match the scope of the business.
5) **Exploratory Data Analysis** - Explore the data to find insights and better understand the impact of variables on model learning.
6) **Data Preparation** – Prepare the data to apply ML models,using normalization
7) **Feature Selection** - Selection of the most significant attributes applying Boruta, Relief and Lasso.
8) **Modeling** – Applying Logistic Regression, Random Forest, K-NN, SVM, AdaBoost and Decision Tree combining boosting and bagging methods
9) **Evaluation** – Which model best meets the business objectives?
10) **Convert Model Performance to Business Values** - Convert the performance of the Machine Learning model into a business result.
11) **Deployment** – Publish the model in a cloud allowing the stackholder view the results


# 4. Data Insights

Below the insights got from the data:

**1) Analysis between 39 - 64. People over 50 are on average 20% more likely to have CVD than under 50** - On average people over 50 are 56.6% likely to have CVD and 20.9% more likely than under 50. 63 years old has the highest incidence.

**2) Analysis between 140 - 193 cm. People shorter than 170 cm (5'7'') have a 5% more chance of CVDs than over 170 cm** - On average people shorter than 170 cm have 4.5% more likely to have CVD than over 170.

**3) Men are 30% more likely than women to develop a CVD** - Although men had more CVD than women, the gap are lesser than 30%. Men had 50,1% of cases of CVD, while women had 49,6%

**4) Analysis between 50 - 130. People over 100 kg (220 lb) have 40% more chance of having a CVD than 100 kg** - On average people with over 100 kg have 19.9% more chance of having a CVD than below 100 kg

**5) People with a BMI above 30 (obese class I) have 25% more chance of having a CVD than below 30** - People with a BMI above than 30 have 26.3% chance of having CVD than BMI below 30

**6) People who do not engage in physical activity are 40% more likely to have CVDs than who engage** - People who engage in physical activity more have 4.6% chance of having CVD

**7) People who regularly consume alcohol have a 10% chance of having CVD than those who do not consume** - People who regularly consume alcohol have 1.9% less chance of having CVD than who don't consume

**8) People who smoke are 20% more likely to have CVD than who do not smoke** - People who smoke have 3% less chance of having CVD than who doesn't

**9) People with well above normal cholesterol have a 50% chance of having CVD than normal** - People with well above normal cholesterol have 33% likely than people with normal

**10) People with well above normal glucose have a 20% chance of having CVD than normal** - People with well above normal glucose have 14.1% more likely than people with normal glucose

**11) People who have hypertension have 40% chance of having CVD than who have normal blood pressure** - People with hypertension 3 have 54.2% more chance of having a CVD than people with normal blood pressure

# 5. Machine Learning Model Applied

Below it is listed the ML models applied:
1) Logistic Regression
2) Random Forest
3) K-NN
4) SVM
5) AdaBoost
6) Decision Tree

# 6. Machine Learning Modelo Performance

**Without Boosting and Bagging**
| ML Model                | Outlier/Normalization   | Feature Selection  | Accuracy           |
|:------------------------|:------------------------|:-------------------|:-------------------|
| Logistic Regression     | No/Yes                  | None               | 0.5773 +/- 0.0414  |
|                         | Yes/No                  | None               | 0.7004 +/- 0.0047  |   
|                         | No/Yes                  | Lasso              | 0.7022 +/- 0.005   | 
|                         | No/Yes                  | Relief             | 0.7135 +/- 0.0056  | 
| Random Forest           | No/Yes                  | None               | 0.7154 +/- 0.0041  |
|                         | Yes/No                  | None               | 0.7212 +/- 0.0053  |   
|                         | No/Yes                  | Lasso              | 0.7145 +/- 0.0049  | 
|                         | No/Yes                  | Relief             | 0.6995 +/- 0.004   |
| K-NN                    | No/Yes                  | None               | 0.5046 +/- 0.002   |
|                         | Yes/No                  | None               | 0.6    +/- 0.0037  |   
|                         | No/Yes                  | Lasso              | 0.6206 +/- 0.0104  | 
|                         | No/Yes                  | Relief             | 0.6311 +/- 0.0025  | 
| SVM                     | No/Yes                  | None               | 0.5    +/- 0.0     |
|                         | Yes/No                  | None               | 0.4975 +/- 0.0063  |   
|                         | No/Yes                  | Lasso              | 0.6957 +/- 0.0061  | 
|                         | No/Yes                  | Relief             | 0.6829 +/- 0.0046  | 


**With Boosting and Bagging**
| ML Model                | Method                | Accuracy               |
|:------------------------|:----------------------|:-----------------------|
| Random Forest           | Bagging               | 0.7281 +/- 0.0065      |
| K-NN                    | Bagging               | 0.709  +/- 0.0028      | 
| AdaBoost                | Boosting              | 0.7221 +/- 0.0073      |
| AdaBoost                | Boosting/With Outlier | **0.7286 +/- 0.0062**  |
| AdaBoost                | Boosting/Lasso        | 0.7145 +/- 0.0055      |
| AdaBoost                | Boosting/Relief       | 0.7225 +/- 0.0072      |
| Decision Tree           | Bagging               | 0.7194 +/- 0.0039      |
| Decision Tree           | Bagging/With Outlier  | 0.7236 +/- 0.0064      |
| Decision Tree           | Bagging/Lasso         | 0.7161 +/- 0.0058      |
| Decision Tree           | Bagging/Relief        | 0.7054 +/- 0.0044	     |

# 7. Business Results

| Exam Accuracy | Price          | Total Exams    | Total                    | 
|:--------------|:---------------|:---------------|:-------------------------|
| Above 50%     | min \$500\.00  | 70.000         | \$35.000.000\.00         |
| Up to 73%     | max \$2000\.00 | 70.000         | \$140.000.000.000\.00    |

# 8. Conclusions
Applying ML model, like AdaBoost in the dataset is possible to obtain a profit 400x than using old method with accuracy up to 73%.

# 9. Lessons Learned

# 10. Next Steps to Improve



