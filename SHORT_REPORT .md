----------------------------------------------------------------FILE DETAILS---------------------------------------------------------------
Dataset shape: 10,000 rows × 21 columns
Target variable: target_default_risk — binary (0 = No Default, 1 = Default)
Duplicate rows: 0 — no duplicate records found
Total missing cells: 1,280
Numerical variables: 14
Categorical variables: 6
------------------------------------------------------Plot distributions of numeric features-----------------------------------------------
                                                                (histograms, boxplots)
                                                                
The histograms were used to understand the distribution of the numerical variables. 
Some variables show approximately symmetric distributions, while others are skewed.
BOXPLOT are mainly used to detect the outliers.
In the observations of boxplot the financial features are having beyong outliers.these all are considered in the preprocessing of data.
But also we cant blindly fix that all outlers are errors we need to process them with different techniques.

--------------------------------------------------------Bargraphs for categorical columns--------------------------------------------------
                                                        value_counts to know unique values 
                                                         
According to the bar graphs on categorical columns it showed how the data  is distributed with count values
using seaborn countplot i made all the four categories within the a cell for analysing.

-------------------------------------------------------Corelation of HEAT MAP/PAIR PLOT----------------------------------------------------

A correlation heatmap is used to visualize the strength and direction of relationships between numerical variables.
Correlation values range from -1 to +1, where positive values indicate a positive relationship and negative values indicate a negative relationship.
Pairplot: Used to visually examine pairwise relationships, distributions, outliers, and potential separation between default and non-default classes.
---------------------------------------------------------CLASS BALANCE---------------------------------------------------------------------
According to the class balance of "target_default_risk" the class is almost balnaced with close values so their is no need of smote.
In "target_default_risk" we got  [1-->51.32 "default"] [0-->48.68 "no default"] percentage value.
I visualised with bat graph also .They are almost same
----------------------------------------------------------DATA PROCESSING------------------------------------------------------------------
HANDLING MISSING VALUES: I have calculated total missing values from the dataset the columns of [income,savings,monthly expenses,credit score,]these four coloumns are having null values or missing values.
Now we got all the null values in the numerical coulumns so ,we can replace them with finding median of the dataset.
And i checked whole columns by extracting value counts and checking the unique values only bachelors are having spelling typo i fixed it with function "replace()".
Changed the signupdate into to_date() which is used for easy extraction of data .
ONE HOT ENCODING: converting categorical columns into numerical coloumns.
In one hot encoding it divides every category into a separate coloumn which gives binary values(0,1).
Before doing one hot encoding we need to split the data into train and test to stop the "DATA LEAKAGE".
Standard scaler for numerical columns ,By using column transformer i transformed all numeric,categorical_col into binary values through creating more columns.splited 8 columns into 21 columns through columntransformer.
After i have combined income and no.of dependents and divided the salary with no.of dependents to get a new column "salary_per_dependent".
In the  code "1" is added because some people are having "0" dependents which will give wrong values.
Then i have made "signup_recency_date" which subracts recent signup_date with first signup_date.
OUTLIER TREATMENT:Outliers in selected numerical variables were identified using the IQR method. Extreme values were capped at the lower and upper IQR boundaries using winsorization/capping. The boxplots after treatment show that extreme observations have been reduced while retaining the majority of the data.
---------------------------------------------------------MODEL BUILDING AND TUNING---------------------------------------------------------
Made five types of different models to find the best model for datset and prediction.
	Model	            Accuracy
0	Logistic Regression	 93.90
1	Decision Tree	     92.40
2	SVM	                 93.75
3	Random Forest	     93.80
4	XGBoost	             95.85
These are the accuracy of all models.
---------------------------------------------------------FINAL CONCLUSION------------------------------------------------------------------
-->Five machine learning models—Logistic Regression, Decision Tree, SVM, Random Forest, and XGBoost—were trained and evaluated for predicting default risk. 
-->The models were compared using accuracy, precision, recall, and F1-score.
-->The results show that model performance varies depending on the algorithm and its ability to capture relationships in the data.
-->Hyperparameter tuning was also performed for Random Forest and XGBoost.  
-->According to the final predictions of models all models have predicted almost correct values.