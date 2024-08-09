# MLOPS-Project-Price-Prediction-for-Real-Estate
### Problem Description:
#### 
Predicting the cost of housing per unit area using data from Kaggle is the project's primary goal. Regression machine learning models will be trained in order to accomplish this goal. Metrics from the holdout subset of the data will be used to search for the best hyperparameters, and the best model will be chosen. MLFlow will be used to keep track of these trials. The training metrics will be computed using Evidently reports and kept in PostgreSQL, while the final models will be kept in an AWS S3 bucket. Once the model is trained, CSV files hosted locally or on S3 can be sent to make predictions in batch mode. This procedure will start the file reading, model predictions, results storing in an S3 bucket, and monitoring metrics recording (drift).
The project also entails creating an API that, depending on the parameters specified in the request body, returns the cost of housing per unit area. You can also call the batch process by giving the file's S3 URI.
Grafana will be used to visualize the metrics, and the Prefect platform will be used to coordinate all of the previously described operations.
### About the data:
#### Source: https://www.kaggle.com/datasets/quantbruce/real-estate-price-prediction
### Summary:
#### 
The dataset includes a number of characteristics related to residential properties and the unit area costs that go along with them in a particular area. Using the provided features, the objective of this machine learning task is to create a prediction model that can precisely calculate the cost of a property per unit area.
The dataset consists of the following columns:
-	No: A unique identifier for each record in the dataset.
-	X1 transaction date: The date of the property transaction, likely represented in a year.month format.
-	X2 house age: The age of the house in years, serving as a measure of its condition.
- X3 distance to the nearest MRT station: The distance in meters from the property to the closest Mass Rapid Transit (MRT) station, indicating transportation convenience.
-	X4 number of convenience stores: The count of convenience stores in the vicinity of the property, reflecting the area's amenities and attractiveness.
-	X5 latitude: The geographic latitude coordinate of the property's location.
-	X6 longitude: The geographic longitude coordinate of the property's location.
-	Y house price of unit area: The target variable, representing the price of the property per unit area, which is the value we aim to predict.

The goal variable (Y) will be the value to predict for fresh, unforeseen data points, and the input features (X1 to X6) will be used to train the model. To gauge the model's predictive accuracy on unobserved data, measures like Mean Average Error (MAE), Root Mean Squared Error (RMSE), and Coefficient of Determination (R2) will be used to assess the model's performance.
### Technologies
-	Cloud: AWS via localstack
-	Experiment tracking: MLFlow
-	Workflow orchestration: Prefect
-	Monitoring: Evidently
-	Packaging tool: Pipenv

### Project Diagram
![image](https://github.com/user-attachments/assets/e5f8949e-9cd6-4bc9-abe0-dca66c09f921)

