# Credit-Card-Approval-Prediction
1.	Introduction </br>
  The credit card is one of the most significant financial products in our daily life.  In 2019, there were more than one and half billion credit cards in use in the United States. Compared to the debit card or cash, the credit card is safer, especially for online shopping. Since the credit card is a kind of payment card based on the promise between cardholders and card issuers, we have to submit proof that we will have enough ability to pay our bills every month and the issuers will use the information that customers provide to determine whether the applications will be approved or rejected. When we apply for new credit, there are so many aspects that influence final results for our credit card applications, such as income, ages, occupation, and the number of dependents, etc. So, in this project, I am going to use three different classification methods to find the most important parameters that influence the final decisions of credit card applications.
So, in this project, I am going to use the credit card approval prediction data consisting of 18 features in the application dataset, application_record.csv and 3 features in the past record part, credit_record.csv. (https://www.kaggle.com/rikdifos/credit-card-approval-prediction?select=credit_record.csv)
  The 18 features in “application_record.csv”  are “ID”, client number, “CODE_GENDER”,while “F” means female and “M” represents male, ”FLAG_OWN_CAR”, as “T” means owing the car and “F” means no vehicle. “FLAG_OWN_REALITY”, which shows whether there will be a property, “CNT_CHILDREN”, the number of children, “AMT_INCOME_TOTAL”, annual income, “NAME_INCOME_TYPE”, Income category, “NAME_EDUCATION_TYPE”,education level,  “NAME_FAMILY_STATUS”,marital status, “NAME_HOUSING_TYPE”,way of living, whether live alone or with parents, “DAYS_BIRTH”, birthday and counting backward to count the day, “DAYS_EMPLOYED”, the number of employed days using counting backward to represent the days  “FLAG_MOBIL”, if there is mobile phone, “FLAG_WORK_PHONE”,whether there is working phone,  “FLAG_PHONE”,if there is a phone, “FLAG_EMAIL”, if there is an email, “OCCUPATION_TYPE”, the list of occupation, “CNT_FAM_MEMBERS”, the family size. And the three features in “credit_record.csv” are “ID”, client number, the same as the previous one, “MONTH_BALACE”, record months and counting backwards, “STATUS”, which 0: 1-29 days past due 1: 30-59 days past due 2: 60-89 days overdue 3: 90-119 days overdue 4: 120-149 days overdue 5: Overdue or bad debts, write-offs for more than 150 days C: paid off that month X: No loan for the month.
  Since there will be a hard pull record after they submit every application no matter whether they are passed or rejected. Therefore it is significant for card applicants to to use this kind of application to do pre-application and find which issue will influence their results most. So, it is significant to use this to do classification and compare different methods to get higher accuracy.

2.	Feature Selection
  I first use the correlation to filter the features, where if the correlation of the feature is over 0.9 between 0.9, then it will be dropped out. To visualize the relationship among the correlations, I build a heatmap as well. From this heat map, it is easy to find the correlations are all under 0.9. And none of the features was filtered.
  Then, I used the p-value to do the feature selection. For this method, I first use logistic regression with 16 features, where I delete the two features, “OCCUPATION_TYPE” and  “FLAG_MOBIL”, at data cleaning stage since there are so many missing value in “OCCUPATION_TYPE” and only one single value in “FLAG_MOBIL”. So, the logistic coefficients table was built with coefficients, standard deviation, z, p-value, the target we are looking for. I set my confidence level as 99%, so I only need those features with the value of P>|z| smaller than 0.01. Finally, there are thirteen features left. They are 'CODE_GENDER', 'FLAG_OWN_CAR', 'FLAG_OWN_REALTY', 'CNT_CHILDREN', 'AMT_INCOME_TOTAL', 'NAME_EDUCATION_TYPE', 'NAME_FAMILY_STATUS','NAME_HOUSING_TYPE', 'FLAG_WORK_PHONE','FLAG_PHONE','FLAG_EMAIL','CNT_FAM_MEMBERS','RECORD_LENGTH'.

