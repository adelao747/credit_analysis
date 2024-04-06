# Analysis Introduction: Bank of America Credit Analysis

In this challenge, you'll use various techniques to train and evaluate a model based loan risk. You'll use a dataset of historical lending activity from a peer-to-peer lending services company to build a model than can identify creditworthiness of borrowers.

## Before You Begin

1. Create a new repository for this project called `credit-risk-classification`. Do not add this homework to an existing repository.

2. Clone the new repository to your computer.

3. Insude your `credit-risk-classification` repository, create a new folder titled "Credit_Risk".

4. Inside the "Credit_Risk" folder, add the `credit_risk_classification.ipynb` and `lending_data.csv` files found in the "Start_Code.zip" file.

5. Push your changes to GitHub.

## Instructions

The instructions for this challenge are divided into the following subsections:

- Split the Data into Training and Test Sets

- Create a Logistic Regression Model with the Original Data

- Write a Credit Risk Analysis Report



<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>loan_size</th>
      <th>interest_rate</th>
      <th>borrower_income</th>
      <th>debt_to_income</th>
      <th>num_of_accounts</th>
      <th>derogatory_marks</th>
      <th>total_debt</th>
      <th>loan_status</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>77536.00</td>
      <td>77536.00</td>
      <td>77536.00</td>
      <td>77536.00</td>
      <td>77536.00</td>
      <td>77536.00</td>
      <td>77536.00</td>
      <td>77536.00</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>9805.56</td>
      <td>7.29</td>
      <td>49221.95</td>
      <td>0.38</td>
      <td>3.83</td>
      <td>0.39</td>
      <td>19221.95</td>
      <td>0.03</td>
    </tr>
    <tr>
      <th>std</th>
      <td>2093.22</td>
      <td>0.89</td>
      <td>8371.64</td>
      <td>0.08</td>
      <td>1.90</td>
      <td>0.58</td>
      <td>8371.64</td>
      <td>0.18</td>
    </tr>
    <tr>
      <th>min</th>
      <td>5000.00</td>
      <td>5.25</td>
      <td>30000.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>8700.00</td>
      <td>6.82</td>
      <td>44800.00</td>
      <td>0.33</td>
      <td>3.00</td>
      <td>0.00</td>
      <td>14800.00</td>
      <td>0.00</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>9500.00</td>
      <td>7.17</td>
      <td>48100.00</td>
      <td>0.38</td>
      <td>4.00</td>
      <td>0.00</td>
      <td>18100.00</td>
      <td>0.00</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>10400.00</td>
      <td>7.53</td>
      <td>51400.00</td>
      <td>0.42</td>
      <td>4.00</td>
      <td>1.00</td>
      <td>21400.00</td>
      <td>0.00</td>
    </tr>
    <tr>
      <th>max</th>
      <td>23800.00</td>
      <td>13.24</td>
      <td>105200.00</td>
      <td>0.71</td>
      <td>16.00</td>
      <td>3.00</td>
      <td>75200.00</td>
      <td>1.00</td>
    </tr>
  </tbody>
</table>
</div>






<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>loan_size</th>
      <th>interest_rate</th>
      <th>borrower_income</th>
      <th>debt_to_income</th>
      <th>num_of_accounts</th>
      <th>derogatory_marks</th>
      <th>total_debt</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>10700.0</td>
      <td>7.672</td>
      <td>52800</td>
      <td>0.431818</td>
      <td>5</td>
      <td>1</td>
      <td>22800</td>
    </tr>
    <tr>
      <th>1</th>
      <td>8400.0</td>
      <td>6.692</td>
      <td>43600</td>
      <td>0.311927</td>
      <td>3</td>
      <td>0</td>
      <td>13600</td>
    </tr>
    <tr>
      <th>2</th>
      <td>9000.0</td>
      <td>6.963</td>
      <td>46100</td>
      <td>0.349241</td>
      <td>3</td>
      <td>0</td>
      <td>16100</td>
    </tr>
    <tr>
      <th>3</th>
      <td>10700.0</td>
      <td>7.664</td>
      <td>52700</td>
      <td>0.430740</td>
      <td>5</td>
      <td>1</td>
      <td>22700</td>
    </tr>
    <tr>
      <th>4</th>
      <td>10800.0</td>
      <td>7.698</td>
      <td>53000</td>
      <td>0.433962</td>
      <td>5</td>
      <td>1</td>
      <td>23000</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>77531</th>
      <td>19100.0</td>
      <td>11.261</td>
      <td>86600</td>
      <td>0.653580</td>
      <td>12</td>
      <td>2</td>
      <td>56600</td>
    </tr>
    <tr>
      <th>77532</th>
      <td>17700.0</td>
      <td>10.662</td>
      <td>80900</td>
      <td>0.629172</td>
      <td>11</td>
      <td>2</td>
      <td>50900</td>
    </tr>
    <tr>
      <th>77533</th>
      <td>17600.0</td>
      <td>10.595</td>
      <td>80300</td>
      <td>0.626401</td>
      <td>11</td>
      <td>2</td>
      <td>50300</td>
    </tr>
    <tr>
      <th>77534</th>
      <td>16300.0</td>
      <td>10.068</td>
      <td>75300</td>
      <td>0.601594</td>
      <td>10</td>
      <td>2</td>
      <td>45300</td>
    </tr>
    <tr>
      <th>77535</th>
      <td>15600.0</td>
      <td>9.742</td>
      <td>72300</td>
      <td>0.585062</td>
      <td>9</td>
      <td>2</td>
      <td>42300</td>
    </tr>
  </tbody>
</table>










    loan_status
    0    75036
    1     2500




# Split the Data into Training and Testing Sets

Open the starter code notebook and use it to complete the following steps:

1. Read the `lending_data.csv` data from the Resources folder into a `Pandas` dataframe.

2. Create the labels set (`y`) from the 'loan_status' column, and then create the feature (`x`) dataframe from the remaining columns.

Note: A value of 0 in the 'loan_status' column means that the loan is healthy. A value of 1 means that the loan has a high risk of defaulting.

3. Split the data into training and testing datasets by using `train_test_split`.







    loan_status
    0    56277
    1     1875




# Create a Logistic Regression Model with the Original Data

Use your knowledge of logistic regression to complete the following steps:

1. Fit a logistic regression model by using the training data (`X_train`) and (`y_train`).

2. Save the predictions for the testing data labels by using the testing feature data (`X_test`) and the fitted model.

3. Evalluate the model's performance by doing the following:

    - Generate a confusion matrix
    
    - Print the classification report
    
4. Answer the following question: How well does the logistic regression model predict both the 0 (healthy loan) and 1 (high-risk loan) labels?














<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Prediction</th>
      <th>Actual</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>36831</th>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>75818</th>
      <td>0</td>
      <td>1</td>
    </tr>
    <tr>
      <th>36563</th>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>13237</th>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>43292</th>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>38069</th>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>36892</th>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>5035</th>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>40821</th>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>35030</th>
      <td>0</td>
      <td>0</td>
    </tr>
  </tbody>
</table>












                  precision    recall  f1-score   support
    
               0       1.00      1.00      1.00     18759
               1       0.87      0.89      0.88       625
    
        accuracy                           0.99     19384
       macro avg       0.94      0.94      0.94     19384
    weighted avg       0.99      0.99      0.99     19384
    








    loan_status
    0    56277
    1    56277






<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Prediction</th>
      <th>Actual</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>36831</th>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>75818</th>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>36563</th>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>13237</th>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>43292</th>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>38069</th>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>36892</th>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>5035</th>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>40821</th>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>35030</th>
      <td>0</td>
      <td>0</td>
    </tr>
  </tbody>
</table>







                  precision    recall  f1-score   support
    
               0       1.00      1.00      1.00     18759
               1       0.87      1.00      0.93       625
    
        accuracy                           1.00     19384
       macro avg       0.94      1.00      0.96     19384
    weighted avg       1.00      1.00      1.00     19384
    


# Write a Credit Risk Analysis Report

Write a brief report that includes a summary and analysis of the performance of the machine learning methods that you used in this homework. You should write this report as the `README.md` file included in your GitHub repository.

Structure your report by using the report template that `Starter_Code.zip` includes, ensuring that it contains the following:

1. An overview of the analysis: Explain the purpose of this analysis.

2. The results: Using a bulleted list, describe the accuracy score, the precision score, and recall score of the machine learning model.

3. A summary: Summarize the results from the machine learning method. Include your justification for recommending the model for use by the company. If you don't recommend the model, justify your reasoning.



