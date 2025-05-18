## Multi-Class Classification Data Science Projects on Diabetes
#### Case Descriptions
This project focuses on patients biological information to discover features most correlated the most to the diabetic status such as non-diabetics, diabetics and pre-diabetics. Machine learning models to predict the diabetic status would be built for prediction purposes. Last but not the least, a K Means Cluster model would be built to better treatment for each cluster of patients.
#### Dataset Descriptions
There are 14 columns and 1000 rows. Most of the features are numerical values.
![image](https://github.com/user-attachments/assets/bae2c049-dd68-40b4-bb54-90b72fc46335)
#### Table of Content
* part 1: EDA Findings
* Part 2.1: Logistic Regression
* Part 2.2: Supporting Vector Classification
* Part 2.3: Decision Tree
* Part 3: KMeans Clustering
* Part 4: Conclusions & Recommendations
#### EDA Findings
* The age of the patiens range from 20 to 79 years old with the average age of 53 years old.
* Out of the 1000 patients, the number of non-diabetic patients is 103 or 10.3%; the number of pre-diabetic patients is 53 or 5.3%; the number of diabetic patients is 844 or 84.4%.
* The distributions of Cr, TG, HDL are right skewed.
* The distribution of HbA1c, Chol, and BNI are normally distributed.
![image](https://github.com/user-attachments/assets/ace1999a-e641-4c1f-8038-955074a10994)

* Prediabetics 
* Most of diabetics and pre-diabetics are males; most of non-diabetics are females.
* Diabets patients tend to be seniors.
* Diabetics have the most chemicals such as Urea, Cr, HbA1c, Chol, TG, VLDL, and BMI.
* Non-dibetics have the lowest chemical elements except HDL and LDL.

![image](https://github.com/user-attachments/assets/a44d8124-89db-489d-8256-28075b66ef94)

* Correlation Analysis. Age is positively correlated with HbA1c, BMI, and CLASS. Urea is very correlated with Cr. HbA1c is positively correlated with TG, BMI, CLASS. Chol is positivelt Correlated with TG and LDL. BMI is correlated with CLASS.
* When people are getting old, their weight and HbA1c tend to go up. Part of the aging experience. Age, weight, and increase level of HbA1c or blood sugar level tend to cause diabetic.
![image](https://github.com/user-attachments/assets/39d66425-4fd2-4786-a1b1-b06610cc8b46)

* Majority of people who are non-diabetic are young people. After age of 50, it's very rare to have someone who are not non-diabetic.
* Pre-diabetics are not very common, it happens to people after 30.
* For diabetics, it almost has people at all ages, young people at their 20s started having diabetes as well. 

![image](https://github.com/user-attachments/assets/22d9ca30-103f-4e99-a208-e5cd4473d2bb)

* Each gender has lots of diabetic patients. However, female has more non-diabetic and pre-diabetic patients than males.

![image](https://github.com/user-attachments/assets/e901e557-1f5c-4e93-a437-0d855a1460c6)

* The observation of the kde analysis is very similar to the correlation analysis.
* For age, the diabetics tend to be older.
* For HbA1c, the distribution for each class is very distinctive as the non-diabetics have the lowest level, pre-diabetic have the medium level, and the diabetics dominate the high level of the HbA1c.
* The distribution for BMI is also very similar. Non-diabetics have the lowest BMI, and the pre-diabetics have the medium level, and the diabetics have the highest level of BMI.

![image](https://github.com/user-attachments/assets/74846104-77d7-41f1-99b2-9ee3b135bb58)

#### Part 2.1: Logistic Regression
* Model Tuning: {C : np.logspcae(0,4,10), penalty : [l1,l2]}. The best params are {C: 1, penalty: l1}.
* Training accuracy was 91.5%; testing accuracy was 94.5%. Precision and recall are the best for Diabeitc Class. However, they are low for pre-diabetc cases. The model better atr predicting diabetic cases.

![image](https://github.com/user-attachments/assets/c490f180-bfef-42f7-9988-5b1ec118b26a)
![image](https://github.com/user-attachments/assets/30836593-1f1a-4a89-a064-741fcb1350c7)
![image](https://github.com/user-attachments/assets/324d95ae-c6fc-4be5-ac7a-0869598cb409)


#### Part 2.2: Supporting Vector Classification
* Model Tuning: {"C": [0.001,0.01, 0.1, 0.5, 1], "kernel": ["linear","rbf", "poly"], "gamma":["scale","auto"]}.
* Best Params are {'C': 0.5, 'gamma': 'scale', 'kernel': 'linear'}.
* The training accuracy is 93.87%, and the testing accuracy is 93.5%. The precision and recall are high for diabetic cases.

![image](https://github.com/user-attachments/assets/9316daae-711b-476e-b6b6-753a0415ab46)
![image](https://github.com/user-attachments/assets/c3b87a8e-970d-49af-9131-933b71932e34)


#### Part 2.3: Decision Tree
* Model Tuning: { "max_depth":[5,10,15,20], "min_samples_leaf":np.arange(2,21,1), "criterion":["entropy","gini"]}
* Best Model is {'criterion': 'entropy', 'max_depth': 5, 'min_samples_leaf': np.int64(2)}.
* The training accuracy is 99%; the testing accuracy is 99%.
* The most import features are HbA1c, Age, TG, BMI, and Chol.

![image](https://github.com/user-attachments/assets/4a766e08-baf8-427f-abed-aad104c3cf39)
![image](https://github.com/user-attachments/assets/21828dd6-fbb9-433a-807a-5eb537eb7817)

#### Part 3: KMeans Clustering
* Set clusters between 2 and 20. It turns out when cluster is 5, it has the highest silhouette scores. Therefore the prime cluster is set as 5.
![image](https://github.com/user-attachments/assets/c15cb862-fc8a-46be-ba1f-7bff69549285)
* By looking at each cluster's center. Each cluster is labeled as such:
Cluster 0: High in Urea and Cr.
Cluster 1: High in seniors and HbA1c.
Cluster 2: High in seniors and HbA1c BMI.
Cluster 3: High in Age and HbA1c.
Cluster 4: High in youth, VLDL, nd BMI.
![image](https://github.com/user-attachments/assets/15a75835-a9df-4c86-bf43-2ef312f1ffa8)

* PCA Visualization. Component 1: High: Age, HbA1c, Chol, TG, BMI; Component 2: High: Urea, Cr; Low: Chol, HDL.
* Along the x-axis positive, the data point tends to be more senior, high in HbA1c, Chol, TG, BMI;
* Along the y-axis positive, it's high in Urea;
* Along the y-axis negative, it's high on chol, HDL.

![image](https://github.com/user-attachments/assets/c5c9543d-755d-4bd0-850a-4b72bec3cf14)


#### Conclusions & Recommendations
* Diabetics are assocated with over weights, high blood sugar and aging. So to stay healthy, patients need to watch out their sugar intakes and weights.
* Healthy diets and frequent exercises shhould be in order.
* For elders, they should have their HbA1c measured frequently to be able to detect diabete in early stage.

#### Recommendations

* Diabetics are in each group. For cluster 0, 1, and 3, there are lots of overweighted seniors. They also have a high HbA1c. So they need to be the priority for the treatment. They need to exercise and lower their HbA1c by reducing sugar in their diet.
* For cluster 4. They are younger than cluster 0, 1, and 3; however, they are overweight and have a high HbA1c. They need to exercise and reduce blood sugar level in their systems.
* For cluster 2, They are the most healthy bunch, they have low blood sugar level and the lowest weight. Keep up the good work . Exercise and keep low blood sugar level.

![image](https://github.com/user-attachments/assets/06b760f6-a791-43e2-b364-f5aabda604b5)

#### The End!
#### Thanks For Reading


