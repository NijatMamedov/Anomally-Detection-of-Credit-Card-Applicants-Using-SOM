# Anomally-Detection-of-Credit-Card-Applicants-Using-SOM

1. Import libraries and data
- I started by importing all the necessary libraries like NumPy, pandas, seaborn, and matplotlib for data manipulation and visualization.

- I also imported modules like MinMaxScaler, MiniSom, TensorFlow, and Optuna for modeling.

- After that, I loaded the credit scoring data from scoring.xlsx.
----------------------------------------------------------------------------------


2. Descriptive Statistics
- I displayed the first few rows of the dataset to understand the structure.

- Then, I ran .describe(include='all') to explore the statistical summary of all columns.
----------------------------------------------------------------------------------

3. Handle Missing Values
- I checked for missing values using .isnull().sum().

- For categorical features, I filled missing values with the mode.

- For numerical features, I filled missing values using the mean.
----------------------------------------------------------------------------------

4. Outlier Treatment
- I visualized each numerical feature using seaborn’s boxplots to detect outliers.

- Then, I calculated the IQR (interquartile range) and used it to filter or cap outliers.
-----------------------------------------------------------------------------------

5. Define Inputs and Target
- I dropped the irrelevant columns like Customer_ID and the target Credit_Score from the input features.

- I defined Credit_Score as my target variable.
------------------------------------------------------------------------------------

6. Scale the Data
- I applied MinMaxScaler to normalize all input features between 0 and 1.

- This was essential before feeding the data into the SOM.
-------------------------------------------------------------------------------------

7. Optimize SOM Parameters with Optuna
- I defined an Optuna objective function to optimize SOM parameters such as grid size (x, y), sigma, and learning_rate.

- I ran the optimization to find the best parameters for training the SOM.
---------------------------------------------------------------------------------------

8. Initialize and Train SOM
- I initialized the SOM using the best parameters obtained from Optuna.

- Then, I trained it using the train_random method on the scaled input data.
----------------------------------------------------------------------------------------

9. Visualize Distance Map
- I plotted the SOM’s distance map using pcolor() and colorbar().

- I used different markers and colors to indicate accepted and rejected customers on the map.
----------------------------------------------------------------------------------------

10. Extract High Distance Nodes
- I calculated the threshold and extracted node positions with distances greater than or equal to 0.9.

- These nodes were identified as anomalies or suspicious applications.
-----------------------------------------------------------------------------------------

11. Train Supervised ANN on Unsupervised Results
- I built a Sequential ANN model with two hidden layers.

- I tuned the number of units in each layer using Optuna as well.

- The model was trained to classify the results based on the SOM output.
------------------------------------------------------------------------------------------

12. Deploy Model on New Data
- I loaded the saved ANN model from disk.

- Then, I imported new applicant data from test_practice.xlsx.

- I scaled the new data using the same scaler and fed it into the trained model to make predictions.
