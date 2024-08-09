# MLOPS-Project-Price-Prediction-for-Real-Estate
### Problem Description:
#### Predicting the cost of housing per unit area using data from Kaggle is the project's primary goal. Regression machine learning models will be trained in order to accomplish this goal. Metrics from the holdout subset of the data will be used to search for the best hyperparameters, and the best model will be chosen. MLFlow will be used to keep track of these trials. The training metrics will be computed using Evidently reports and kept in PostgreSQL, while the final models will be kept in an AWS S3 bucket. Once the model is trained, CSV files hosted locally or on S3 can be sent to make predictions in batch mode. This procedure will start the file reading, model predictions, results storing in an S3 bucket, and monitoring metrics recording (drift).
The project also entails creating an API that, depending on the parameters specified in the request body, returns the cost of housing per unit area. You can also call the batch process by giving the file's S3 URI.
Grafana will be used to visualize the metrics, and the Prefect platform will be used to coordinate all of the previously described operations.
### About the data:
#### Source: https://www.kaggle.com/datasets/quantbruce/real-estate-price-prediction
### Summary:


