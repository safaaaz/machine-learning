
# Gender Gaps in High-Tech Companies

**Machine Learning**

## Project Overview

This project explores gender disparities among employees in high-tech companies using machine learning techniques. We analyzed various aspects such as gender distribution, working years, age, job roles, and more, to understand how these factors differ between males and females.

## Dataset

We utilized the IBM HR Analytics Employee Attrition & Performance dataset from Kaggle. This dataset includes 1,470 employee records with 35 features, such as:

- Age
- Distance from Home
- Business Travel
- Job Satisfaction
- Monthly Rate
- Marital Status
- Overtime Hours

**Dataset Source:** [IBM HR Analytics - Kaggle](https://www.kaggle.com/datasets/pavansubhasht/ibm-hr-analytics-attrition-dataset)

## Setup and Installation

1. **Install Required Libraries:**

   ```bash
   pip install turicreate matplotlib seaborn
   ```

2. **Download and Prepare the Dataset:**

   ```python
   import json
   import os

   # Set up Kaggle API token
   !mkdir /root/.kaggle/
   api_token = {"username":"safaaazbarqa","key":"cb765b192e6a8751fd22e76f0b39de0a"}
   with open('/root/.kaggle/kaggle.json', 'w') as file:
     json.dump(api_token, file)
   !chmod 600 /root/.kaggle/kaggle.json

   # Create directories
   !mkdir ./datasets
   !mkdir ./datasets/ibm-hr

   # Download and unzip the dataset
   !kaggle datasets download pavansubhasht/ibm-hr-analytics-attrition-dataset -p ./datasets/ibm-hr
   !unzip ./datasets/ibm-hr/*.zip -d ./datasets/ibm-hr/
   ```

## Analysis and Visualizations

1. **Gender Distribution:**

   Visualize the proportion of male and female employees using a pie chart.

2. **Working Years:**

   Analyze and compare the total working years between male and female employees using bar graphs.

3. **Age Differences:**

   Examine age distributions and compare between genders.

4. **Job Role Analysis:**

   Investigate how job roles differ by gender through bar charts.

5. **Marital Status and Overtime:**

   Explore the impact of marital status on overtime work and how it varies between genders.

6. **Education vs. Monthly Rate:**

   Compare average monthly rates based on education level and gender.

7. **Income vs. Monthly Rating:**

   Analyze the relationship between monthly income and rating for each gender.

8. **Business Travel:**

   Examine business travel frequency and how it varies between genders.

9. **Distance from Home:**

   Analyze how distance from home affects the number of employees by gender.

## Example Code

Here’s a snippet to get you started with the analysis:

```python
import turicreate as tc
import matplotlib.pyplot as plt

# Load dataset
dataset_path = "./datasets/ibm-hr/WA_Fn-UseC_-HR-Employee-Attrition.csv"
sf = tc.SFrame.read_csv(dataset_path)

# Gender distribution
import turicreate.aggregate as agg
sf1 = sf['Gender', 'EmployeeCount']
g = sf1.groupby(['Gender'], {'Count': agg.SUM('EmployeeCount')}).sort('Count')
print(g)
```

## Results

For a detailed exploration of the dataset and the results of our analysis, refer to the notebook on [Google Colab](https://colab.research.google.com/drive/1cU_oVhtl1uc5ApHTeS815i6JjV8WJ8DM).

Feel free to explore and adapt the code to suit your needs!
