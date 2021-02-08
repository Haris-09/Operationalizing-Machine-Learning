


# Operationalizing Machine Learning

This is the second project of Machine Learning Engineer with Microsoft Azure Nanodegree. In this project we used the bankmarketing dataset to predict wheter the customer will subscribe to fixed-term deposit or not. Which means this is a Binary Classification problem.

In this project we create, publish and consume the pipeline. The project starts with authenticating to Azure Machine Learning services, then we created an AutoML Experiment, then we deployed the best model, then we enable logging and application insights to review important information. After deploying model endpoint is created which we consumed. Finally we create and publish the pipeline to Automate the whole process.

## Architectural Diagram

![Alt text](images/Architecture-Diagram.png?raw=true "Architectural Diagram")

## Key Steps

### 1-Dataset Registration

First we upload and register the bankmarketing dataset in the AzureML Studio. the screenshots shows the detials of the bankmarketing dataset 

![Alt text](images/Dataset_1.PNG?raw=true "Dataset Detail")

![Alt text](images/Dataset_2.PNG?raw=true "Dataset Explore")

### 2-AutoML Experiment

In this step we created the AutoML Experiment. First we choose the bankmarketing dataset, then we name our experiment "AutoML-Experiment" choose y as target column and created Standard_DS12_v2 compute cluster with maximum 4 number of nodes. In the next step we choose exit criterion 1 and concurrency 5, choose classification and enabled deeplearning. Finally we finised and after about half an hour Experiment is completed.

Bleow screenshots shows the whole steps

![Alt text](images/AutoMLRun_1.PNG?raw=true "AutoML Steps")

![Alt text](images/AutoMLRun_2.PNG?raw=true "AutoML Steps")

![Alt text](images/ComputeCluster_1.PNG?raw=true "Compute Cluster setp 1")

![Alt text](images/ComputeCluster_2.PNG?raw=true "Compute Cluster step 2")

![Alt text](images/AutoMLRun_3.PNG?raw=true "AutoML Steps")

![Alt text](images/AutoMLRun_5.PNG?raw=true "AutoML Steps")

![Alt text](images/ExperimentRun-Completed.PNG?raw=true "AutoML Steps")

### 3-Best Model Deployment

Now that our Experiment is completed and we can see that the best model is SparseNormalizer, LightGBM with an Accuracy of 0.92079. we clicked the deploy model button to deploy the model and the green check marked shows that the deployment is succeeded. After the deployment in the endpoints section we can see that the endpoint is created and in the consume tab URI and Key is available which we can use to consume the model.

![Alt text](images/BestModel-new.PNG?raw=true "AutoML Models")

![Alt text](images/BestModel-details-new.PNG?raw=true "AutoML Best Model details")

![Alt text](images/DeployBestModel-Succeeded-new.PNG?raw=true "Deployment Succeeded")

![Alt text](images/Endpoint-Consume.PNG?raw=true "Endpoint URI and Key")

### 4-Enable Application Insights

Now our model is deployed and endpoint is available which we can counsume to enable Application Insights. In order to do that we need config.json file which we downloaded form the Azure Machine Learning Workspace. Then we opened git bash and login to Azure using az login command and inside the logs.py file we added a one line code to enable application insights and run logs.py in our git bash using python logs.py and we can also see in endpoint section that Application Insights are enabled.

![Alt text](images/Run-logs-py.PNG?raw=true "bash ")

![Alt text](images/Enabled-Application-Insights-new.PNG?raw=true "Insights Enabled")

### 5-Swagger Documentation

To enable swagger documentation and to see what the request looks like. we first downloaded the swagger.json file from the link available under the details of endpoint. we have to put the swagger.json file with the serve.py and swagger.sh in the swagger folder. in the swagger.sh i replaced port 80 with 9000 and in serve.py i used 8000. then i first run the swagger.sh using "bash swagger.sh" in the git bash and after that i was able to access the swagger at http://localhost:9000 and in parallel i ran my serve.py file in new git bash window which is then accessible at http://localhost:8000 . then i added link http://localhost:8000/swagger.json in the explore section of swagger to see the swagger documentation and how the request looks like.

![Alt text](images/Swagger-running.PNG?raw=true "Swagger-running")

![Alt text](images/running-serve-py.PNG?raw=true "Serve.py Running")

![Alt text](images/Swagger-localhost8000.PNG?raw=true "Swagger documentation")

![Alt text](images/Swagger-RunMLService.PNG?raw=true "Swagger Post Request")

### 6-Consume Model Endpoint

To consume model endpoint first we edit endpoint.py and replace URI and Key with the one that are provided in the consume section of endpoint in AzureML Studio. then we ran endpoint.py in the git bash and it shows the result as expected.

![Alt text](images/Endpoint-py-result.PNG?raw=true "endpoint.py result")

### 7-Create, Publish and Consume Pipeline

Above all explained steps can be published as a pipeline by using the Jupyter Notebook. After running all the cells we can see that the pipeline is created using AutoML module and endpoint is also available.

![Alt text](images/Pipeline-Run-Completed.PNG?raw=true "Pipeline-Run-Completed")

![Alt text](images/Pipeline-Runs.PNG?raw=true "Pipeline-Runs")

![Alt text](images/Pipeline-Graph.PNG?raw=true "Pipeline-Graph")

![Alt text](images/Pipeline-endpoints.PNG?raw=true "Pipeline-endpoints")

![Alt text](images/Pipeline-RestEndpoint.PNG?raw=true "Pipeline-RestEndpoint")

## Screen Recording

https://youtu.be/ImEkwWRtr30

## Standout Suggestions
*TODO (Optional):* This is where you can provide information about any standout suggestions that you have attempted.
