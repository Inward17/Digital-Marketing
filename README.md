Problem Statement : 
AI-Driven Media Investment Plan Across Channels for E-commerce.

Introduction :
This project has to do with optimally allocating a fixed marketing budget across advertising channels. The historical performance information can drive a machine learning model to predict the optimal allocation strategy, which predicts a higher ROI(Return on investment) on marketing investment. 

Libraries and Versions :
Pandas - version : 1.3.3
Numpy - version : 1.21.2
Scikit-learn - version : 0.24.2
Matplotlib - version : 3.4.3
Datetime

Approach and Methodology :
Data Processing : 
Analysis of performance data and cleaning : We removed various columns like impressions and refined the data; converted all dates into days for faster and better processing and deleted the dates column. Identify and remove outliers(10%ile - 90%ile) in the data using the Interquartile Range (IQR) method. 
Feature Engineering : Using the given data we made a few new columns named ‘dayofweek’ , ‘cpc’ (Cost per click) and ‘ctr’ (Clicks per impression). 
Feature Selection : In the final processing(correlated features were removed), we used 4 columns : ‘Cost’, ‘dayofweek’, ‘cpc’ and ‘ctr’ were selected as inputs for the model and 5th column ‘conversions’ as output.
Normalization: Normalize the data using Min-Max Scaling to bring all features into a comparable range, which is essential for certain machine learning algorithms.
Analysis of website_landing data : Concatenation of 3 columns ‘source’, ‘channel’ and ‘campaign_type’ to form a new column ‘combined’. Due to this all the entries were combined to 71 entries. Through further processing new features like ‘total_conversions’, ’total_landings’ and ‘conversions_per_landing’ were created. 
Channel assistance : Considering the impact of previous touchpoints, delayed impact was calculated and then the columns were updated accordingly.

Algorithm : 
One-Hot Encoding :  Apply One-Hot Encoding to the DayOfWeek column to convert categorical days into numerical features. Merge the encoded columns back into the original DataFrame and drop the DayOfWeek column.
Model Training and Prediction : The steps for model training and prediction would involve splitting the data into training and test sets, training a random forest regression model to predict conversions, and making predictions on the test set.
Accuracy Calculation : Calculate Mean Absolute Percentage Error (MAPE) to assess the accuracy of the model's predictions. Compute the accuracy by subtracting MAPE from 100%.
Percentage of predicted conversions : Using performance data, we applied ML model individually to the platforms and calculated predicted conversion.
Calculation of average conversions per landing : After data processing which includes the concatenation and delayed impact, we finalized 10 paths which were mentioned in the data description. We calculated mean from different sources of conversions per landing : google, meta, microsoft.
Calculate the Budget Allocation : Using the prediction  conversion of performance data of each platform and using average conversion per landing from website-landing data; We reassign weights to the platform on which basis the budget is calculated, ensuring each receives at least 10% of the total budget. 
Sub-budget allocation : Additionally the  budget of each platform is internally distributed to their respective campaign types.
Plotting : Plotted the actual versus predicted conversions, with accuracy displayed in the plot title for each platform separately. Also final budget allocations are displayed in the form of pie charts.

Assumptions : 
The ROI from each platform is linearly correlated with the amount spent.
Historical performance data is representative of future performance.
To incorporate channel assistance, we added one conversion for each  delayed impact.

Results : 
Input : 
Budget : 200,000 USD
Output : 
Meta Ads : 26042.50 USD. 
Google Ads : 98026.71 USD.
Bing/Microsoft Ads : 75930.78 USD

Conclusion :
The Random Forest model effectively allocates the budget based on historical data, maximizing ROI across different platforms. Future work could involve using more sophisticated models like XGBoost or incorporating more features such as seasonal trends to improve prediction accuracy.

References : 
Pandas Documentation : pandas 2.2.2 documentation 
Matplotlib Documentation : Using Matplotlib — Matplotlib 3.9.2 documentation 
TensorFlow Documentation : API Documentation | TensorFlow v2.16.1 
Scikit-learn Documentation : User Guide — scikit-learn 1.5.1 documentation
Datetime Documentation : datetime — Basic date and time types — Python 3.12.6 documentation 
Note : Before running the code in any notebook change the path of csv files.
