# Health Insurance Cross Sell

<img src="https://user-images.githubusercontent.com/87786119/161869633-52e5e00e-759a-47dd-ab91-698382e0df6d.png" width="800">

#### Disclaimer.
This project is based on the dataset available in kaggle website and the context is fictitious.

The datasets used can be acessed by the link below: 

https://www.kaggle.com/anmolkumar/health-insurance-cross-sell-prediction

# 1. Business Problem.

The Insurance All company sell actually health insurance and the business team are planning to start sell vehicle insurance to their clients. 

Last year the marketing team consulted 380000 clients about their interest in vehicle insurance, and they responded if they like or not to take the vehicle insurance. To realize the project the company will provide the dataset with the results of this search.

By now, the company has acumulated about 127000 new clients and the business team wants to offer the vehicle insurance to this new clients. The problem is that the campaign will be made in the shortest period possible and the capacity of calls of the marketing team is limited to 20000 call during the period of the campaing.

This data science project will provide a classified list with the clients that are more prone to accept the offer of vehicle insurance. So the number of calls will be made more eficiently than a random call selection and the revenue of the campaing will be more optimized.

# 2. Business Assumptions.

The features provided by the dataset are described below and the target feature is **Response**.

- **id:** Unique ID for the customer
- **Gender:** Gender of the customer
- **Age:** Age of the customer
- **Driving_License:** 0 -> Customer does not have DL, 1 -> Customer already has DL
- **Region_Code:** Unique code for the region of the customer
- **Previously_Insured:** 1 -> Customer already has Vehicle Insurance, 0 -> Customer doesn't have Vehicle Insurance
- **Vehicle_Age:** Age of the Vehicle
- **Vehicle_Damage:** 1 -> Customer got his/her vehicle damaged in the past, 0 -> Customer didn't get his/her vehicle damaged in the past
- **Annual_Premium:** The amount customer needs to pay as premium in the year
- **PolicySalesChannel:** Anonymized Code for the channel of outreaching to the customer ie. Different Agents, Over Mail, Over Phone, In Person, etc
- **Vintage:** Number of Days, Customer has been associated with the company
- **Response:** 1 -> Customer is interested, 0 -> Customer is not interested

# 3. Solution Strategy

## 3.1 Final Product

It will be delivered a google sheet with a classifier button so the marketing team need only to upload the list of clients and prees the button to classificate the best contacts to call.

## 3.2 Tools

- Python 3.8.0

- Jupyter Notebook

- Google Sheets

- Git and Github

## 3.3 Process

**Step 01. Data Description:** in this step some adaptations are made in the dataset so it is possible to identify dimension, types, presence of nan values and change types. Identify numerical and categorical features and appply some statistical metrics to analyze mean, median, maximum, minimum, range, skew, kurtosis and standard deviation.

**Step 02. Feature Engineering:** in this step new features are created and some are modified to better understand the columns.

**Step 03. Data Filtering:** in this step some rows and columns are dropped if it doesn’t make sense for the project scope or there isn’t enough information to deal with that feature.

**Step 04. Exploratory Data Analysis:** in this step the data is analyzed to better understand the impact of the features in the project and model learn, and get insights from results.

**Step 05. Data Preparation:** in this step some transformations such as numerical and nature transformation are made to prepare the data for the machine learning model.

**Step 06. Feature Selection:** in this step some algorithms used to select the attributes that better represents the target feature (positive interest) and use them to train the model.

**Step 07. Machine Learning Modelling:** in this step the machine learning model training is made and based in the precision@k and recall@k metrics the best model is selected.

**Step 08. Hyperparameter Fine Tunning:** in this step the machine learning model choosed in step 07 is tuned with some aditional hyperparameters to get the final model.

**Step 09. Understang Model Performance for Business Results:** this is the most important step where the model performance is translated to a business results.

**Step 10. Deploy Model to Production:** in this step the model is published in a cloud platform for other peoples or devices access the solution proposed. The cloud platform choosed was Heroku.

**Step 11. Google sheet:** in this step the already online tool is made available for the user from the Google Sheets. The user will be able to request the beste classified list by pressing the classifier button in the sheet.

# 4. Top 3 Data Insights

**Hypothesis 01:**

Customers with higher annual premium payments are more insterested in the vehicle insurance.

**False:** The hypothesis is FALSE. There is a concentration of positive answers around of 35000.

![image](https://user-images.githubusercontent.com/87786119/161855751-352a70b3-eb47-47e7-a426-ba3775806f93.png)


**Hypothesis 02:**

People with newer vehicles are more interested in car insurance.

**False:** The interest in car insurance is larger among clients with vehicles with 1 and 2 years old.

![image](https://user-images.githubusercontent.com/87786119/161856743-9220cba2-a516-4634-b95c-7c6abb27aeac.png)


**Hypothesis 03:**

Older people are more interested in vehicle insurance.

**False:** There are more clients interested in vehicle insurance with age between 38 and 49 years.

![image](https://user-images.githubusercontent.com/87786119/161857066-803e661a-cd4f-415f-b064-1773a1491c20.png)


# 5. Machine Learning Model Applied

For this classification project was used the following machine learn algorithms: KNN, Logistic Regression, Extra Trees, Random Forest and XGBoost. For performance analysis purpose was used the Cumulative Gain and Lift curves, as shown next.

## KNN Classifier
![image](https://user-images.githubusercontent.com/87786119/161858557-a349b76a-f531-421d-9867-0d16f26e5550.png)

## Logistic Regression
![image](https://user-images.githubusercontent.com/87786119/161858762-346d8119-1ad9-484f-865d-3f3d2962b3c3.png)

## Extra Trees Classifier
![image](https://user-images.githubusercontent.com/87786119/161858854-b4af419c-b343-4f79-826d-074576263fe8.png)

## Random Forest
![image](https://user-images.githubusercontent.com/87786119/161858985-1c128bef-6b4f-4769-a4a7-9853553c454c.png)

## XGBoost Classifier
![image](https://user-images.githubusercontent.com/87786119/161859055-6169b104-2151-4a03-be68-48eb1901b5de.png)

As can be seen, the cumulative gain curve of XGBoost is the one with faster growing, so with this classifier its possible to get the most of interested clients with lower percentage of the base. Compared to the random model (baseline), XGBoost has the best performance.

# 6. Machine Learning Model Performance

The next tables ilustrate the performance of the models applied considering the Precision@k and Recall@k parameters.

For single performance:

| Model Name  |	Precision_at_k | Recall_at_k |
|:-----------:|:--------------:|:-----------:|
| XGB 	      | 0.310 	       | 0.832       | 
| LRegression |	0.294 	       | 0.788       |
| Etrees 	    | 0.289 	       | 0.773       |
| RForest 	  | 0.288 	       | 0.771       |
| KNN 	      | 0.277 	       | 0.742       |

After Cross Validation:

| Model Name  |	Precision_at_k | Recall_at_k     |
|:-----------:|:--------------:|:---------------:|
| XGB CV      | 0.309 +/- 0.001| 0.828 +/- 0.003 | 
| LRegression |	0.294 +/- 0.003| 0.787 +/- 0.007 |
| RForest 	  | 0.292 +/- 0.002| 0.78 +/- 0.006  |
| Etrees 	    | 0.285 +/- 0.001| 0.763 +/- 0.005 |
| KNN 	      | 0.278 +/- 0.001| 0.743 +/- 0.002 |

Because XGBoost had the best performance this algorithm was selected and after been tuned, the cumulative gain and lift curve is now like the next figure:

![image](https://user-images.githubusercontent.com/87786119/161862120-224c8dd3-0766-4fb3-96f6-bb6e8c3cc89b.png)

# 7. Business Results
- The most relevant attributes of clients with interest in vehicle insurance are vehicle_damage, policy_sales_channel, vehicle_age, previously_insured, vintage, annual_premium, age, region_code and damage_per_rcode

- The percentage of clients interested in vehicle insurance that will be contacted with 20.000 calls are 47.9%

![image](https://user-images.githubusercontent.com/87786119/161866494-3acabf6a-05a3-455e-9156-85cd90b1487d.png)

- The percentage of clients interested in vehicle insurance that will be contacted with 40.000 calls are 81.3%

![image](https://user-images.githubusercontent.com/87786119/161866517-6f24747f-30e7-459b-a4c8-e83a455ab94a.png)

- To contact 80% of clients interested in vehicle insurance the marketing team needs to make 23369 calls

Accordingly to the next figure, to get the maximum ROI the company needs to make contact with 28% of the clients in the base.

![image](https://user-images.githubusercontent.com/87786119/161866711-fecd6f7f-872b-4b75-b143-a6bc657288a5.png)

# 8. Conclusions

For analyse the performance of the model the most commom classification metrics, like precision@k and recall@k, was used. A button was added to a google sheet table (apenddix) so the sell team can classifcate the leads just by pressing the button and select the best clients to call.

# 9. Lessons Learned

After the study of the problem it was identified a classification data science project, with the objective of classifie the leads with more probabilitie to accept the offer of a vehicle insurance. After applying some machine learning models the XGBoost model was selected and applied to make the classification. 

# 10. Next Steps to Improve

- Implement others algorithm
- Analyse others classification metrics

## Apendix

Get Prediction button added to the menu of the table.

![image](https://user-images.githubusercontent.com/87786119/161868802-22762daf-4adc-48f7-abda-362fb74aa0bc.png)

### LICENSE

### All Rights Reserved - Comunidade DS 2022
