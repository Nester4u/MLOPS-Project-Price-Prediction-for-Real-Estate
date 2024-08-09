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

### How to set up the project

1.	Clone the project repository:
git clone https://github.com/Nester4u/MLOPS-Project-Price-Prediction-for-Real-Estate.git
2.	Install docker-compose version 3.
3.	Navigate to the project directory:
cd ml-ops-zoomcamp-project/
4.	Build the project using the Makefile:
make build
5.	The process of building will automatically run the unit tests. If all the tests pass, the project will be ready to run. However, if the tests fail, the project will not be built.
6.	If the image is built and the service is up, the following services will be available:
   
service	port	Interface	url	description

API	5010	127.0.0.1	http://127.0.0.1:5010 API prediction service

Prefect	4200	127.0.0.1	http://127.0.0.1:4200 Prefect UI

MLFlow	5000	127.0.0.1	http://127.0.0.1:5000 MLFlow UI

Grafana	3000	127.0.0.1	http://127.0.0.1:3000 Grafana UI

PostgreSQL	5432	127.0.0.1	http://127.0.0.1:5432 Postgres database

7.	Access Prefect Deployments and run the model_training flow with Quick run.

![image](https://github.com/user-attachments/assets/5f4a37b7-aba0-4056-85bb-1fee4dcc8247)

8.	-Optional- Inorder to examine the experiments, access MLFlow UI.
9.	Alternative you can trigger the model_training flow on prefect through the /trigger-training endpoint (default http://127.0.0.1:5010/trigger-training).
-	The JSON schema should be as follows:
  
        {
	    "s3_file_path": "s3://some_bucket/train_data.csv"
        }

-	If you sent a logic false in the s3_file_path key, model will be trained with the default training data.

        {
        "s3_file_path": false
        }

10.	-Optional- Run the following command, to exit the project:
make kill

### Creating Predictions
1.	Following model training, there are three methods by which you can start making predictions:
   
a.	Batch predictions through Prefect with the batch_prediction flow.   
     -	The project will simulate 100 records by sampling values from the training dataset if you do not supply the S3 URI of the data.     
     -	As an alternative, you can supply a file path for the prediction; however, the file path format must to match that of the training data.




