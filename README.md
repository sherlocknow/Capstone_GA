## Capstone Project - Vikas Kalia DSI-16
### Problem Statement
Palm is a palm oil producing company in Southeast Asia relies heavily on natural elements like rain, soil type, terrain, etc., for a rich harvesting yield of the palm fruit and in return palm oil.  

Palm company needs the ability to accurately predict its palm fruit crop yield in the monthly and yearly horizon to enable forward contract for its product, i.e. Palm Oil. Today, it primarily relies on the experience and expertise of appointed agronomists to make such predictions.

In addition to the experience and expertise of appointed agronomists, Palm Oil company will like to introduce data driven prediction methods for predicting its palm fruit yield and in return, its oil production.

### Approach
- Raw data on daily rain & crop harvesting levels as well as static data on blocks is provided in excel
- Advansed pandas data tranformation techniques are used to fused daily Rain and crop data  with blocks listed in static blocks dataset
- EDA was performed using daily and monthly agreed data at block level
- Modeling is performed use two datasets, one with monthly data at estate level and other with monthly data at block level
- Monthly data between 1-Apr-2011 and 31-Dec-2019 is used for train and validation and data from 1-Jan-2020 to 31-May-2020 will be used as unlabelled test data.
- Linear regression and Decision Tree - Random Forest algorithms from sklearn library are utilized
- Feature engineering includes shifting of rain data by multiple time periods like 6, 12, 24,26 months.
- LassoCV algorithm was used to regularize linear regression model
- Max_depth is used as tuning parameter for Random Forest
- R2 and RMSE metric are used to evaluate the models

### Notebooks
Total of three notebooks are developed for this project:
- '../code/palm1_Main.ipynb' >>> First notebook used for data loading, cleaning & transformation as well as EDA
- '../code/palm2_modeling.ipynb' >>> notebook used for data modeling using Linear Regression
- '../code/palm3_modeling.ipynb' >>> notebook used for data modeling using Random Forest

### Datasets
-  '../data/block_syp_class.xlsx' >>> static blocks data received from the palm company - Confidential
-  '../data/rain_and_crop.xlsx'   >>> daily rain and crop data received from the company -  Confidential
-  '../data/blocks.csv'   >>> blocks static data saved after transformation
-  '../data/final_fused.csv' >>> final fused daily rain and crop data
-  '../data/final_fused_monthly.csv' >>> final fused monthly rain and crop data

**Note: there are many interim files which are created & read during the data transformation process**

### Data Dictionary
|Feature|Type|Dataset|Description|
|---|---|---|---|
| crop | num | rain_crop| palm fruit harvest weight in tonnes|
| rain | num | rain_crop| rain fall in millimeters|
| blk | cat | blocks |name of the block |
| area_ha|num|blocks| Area in heactare for each block|
| no_of_palms|num|blocks| no of palms planted in each block|
| mth_of_plant|num|blocks| date at which palms were planted in each block|
|plant_mat|cat|blocks|type of seeds used to plant for each block|
| syp1_ha|num|blocks| area in hectare of syp class 1 in each block|
| syp1_prop|num|blocks| prop of syp class 1 against total area of each block|
|age|num|blocks|computed between today and mth_of_plant in months|

### Conclusion:
- Only using the lag of rain data did not predict the crop yield very well against the initial assumption
- Age of the palms at the time of crop harvesting is positive predictor
- Granularity is not a always a good for predictive modelling - daily vs monthly data
- Data Cleaning & wrangling does take 75% of the time
- Understanding of data is an ongoing process
### Recommendations
- Present this round of analytics to seek feedback from business
- Compare these predictive results with manual predictions made by the agronomists
- Model for each block and evaluate
- Model for cluster of blocks after clustering those on the basis of yield, age, etc.
- Use other algorithms like XGBoost & Time Series - Arima etc. as well as techniques like ensembling of multiple algorithms and evaluate against performance of linear regression algorithms.
- Use weather APIs to fuse temperature
- Use data on application of fertilisers for predictive modelling
