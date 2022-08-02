# Charity Funding Analysis using Neural Networks

### Overview & Purpose
The purpose of this project was to analyze data from over 34,000 charity organizations. Once this data was cleaned and organized, neural networks were built to predict if funding received through Alphabet Soup would be used effectively.

First the data was imported and preprocessed for machine learning. This included encoding object data types, dropping null values, and putting data into bins to allow maximum efficacy of the machine learning models. Next, the data was split into features and target arays, then split again into training and testing sets,and finally scaled to reduce data imbalance. Lastly, the neural networks were built, trained, and evaluated for accuracy and loss metrics. 

### Results
During data preprocessing the following was determined:
- The target variable to predict is the column `IS_SUCCCESSFUL` which indicates if the particular charity utilized the funding effectively.
- The features that are used to predict the target are a total of 43 columns, which includes the asking amount, application type, income amount, and special considerations, among others.
- Data determined to be potentially unimportant to predicting the target was removed. The columns of `EIN` and `NAME` were removed in the initial model.

While compiling, training, and evaluating the models the following was determined:
- The initial model contained **2** hidden layers, the first with 8 nodes and the second with 5 nodes. Both hidden layers utilized the **RELU** activation function. 