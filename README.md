# Charity Funding Analysis using Neural Networks

### Overview & Purpose
The purpose of this project was to analyze data from over 34,000 charity organizations. Once this data was cleaned and organized, neural networks were built to predict if funding received through Alphabet Soup would be used effectively.

First the data was imported and preprocessed for machine learning. This included encoding object data types, dropping null values, and putting data into bins to allow maximum efficacy of the machine learning models. Next, the data was split into features and target arays, then split again into training and testing sets,and finally scaled to reduce data imbalance. Lastly, the neural networks were built, trained, and evaluated for accuracy and loss metrics. The target accuracy was set at **75 %**.

### Results
During data preprocessing the following was determined:
- The target variable to predict is the column `IS_SUCCCESSFUL` which indicates if the particular charity utilized the funding effectively.
- The features that are used to predict the target are a total of 43 columns, which includes the asking amount, application type, income amount, and special considerations, among others.
- Data determined to be potentially unimportant to predicting the target were removed. The columns of `EIN` and `NAME` were removed in the initial model, since the employee identification number and the name of the organization didn't seem likely to assist in predicting effective funding use.

While compiling, training, and evaluating the models the following was determined:
- The initial model contained **2** hidden layers, the first with 8 nodes and the second with 5 nodes. 2 hidden layers were chosen because keeping the hidden layers 2-3 times the number of inputs seemed a sufficient place to begin. Both hidden layers utilized the **RELU** activation function. The output layer utilized the **Sigmoid** activation function because the purpose was to predict whether or not an organization would use funds effectively (the sigmoid output of 0 to 1 fits this exactly).
- The initial model did **not** achieve target performance, falling just short with an accuracy of **72.7 %**.

![initial_model](https://github.com/conorwhanson/Neural_Network_Charity_Analysis/blob/main/resources/initial_model.png)

- After running the initial model 2 more models were created in an attempt to optimize model performance.
    - **Optimization attempt # 1:** While dropping the `EIN` and `NAME` columns as in the initial model, this attempt also binned the `ASK_AMT` column so as to group together the amount of funding requested by each organization. 
    
    ![ask_bins](https://github.com/conorwhanson/Neural_Network_Charity_Analysis/blob/main/resources/ask_bins.png)
    
    Seven bins were created (a significant reduction from 8747 independent amounts requested) and then fed into the initial model (2 hidden layers both with **RELU**; 8 neurons in first layer, 5 neurons in the second, sigmoid activation function for the output layer). The results were clear by 23 epochs: the optimization failed and achieved only **53 %** accuracy with a high loss metric of **.69**.

    - **Optimization attempt # 2:** Upon further exploration of the data it was decided that this attempt would bin the `NAME` column. This brought the number of features in the column down from 19568 to 793, a siginificant reduction. Further, it was thought that if the same organizations requested various amounts of funds many times, then perhaps if they're successful that would help classify them more easily. The names were binned that occurred 1 time or less.

    ![name_bins](https://github.com/conorwhanson/Neural_Network_Charity_Analysis/blob/main/resources/names_list.png)

    Slight modifications were also made to the model itself, reducing the amount of neurons in both hidden layers. The first layer was reduced to 6 neurons, the second was reduced to 4 neurons. The reasoning behind this was that if the resulting accuracy was low, it was likely due to the input data and no amount of model manipulation would improve it. The activation functions, both in the hidden layers and output layer, remained unchanged.

    ![opt_model_2_structure](https://github.com/conorwhanson/Neural_Network_Charity_Analysis/blob/main/resources/optimized_model_2.png)