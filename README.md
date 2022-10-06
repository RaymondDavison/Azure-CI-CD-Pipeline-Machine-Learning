# Overview

This project demonstrates how to build a Machine Learning CI/CD pipeline with Azure DevOps. 
A `Github repository` will be build from scratch alongside a `scaffolding` that will assist in performing both Continuous Integration and Continuous Delivery. 
Continous Integration will be done with `Github Actions` along with a `Makefile`, a `requirements.txt` and `application code` to perform an initial `lint`, `test`, and `install cycle`. The project will then be integrated with `Azure Pipelines` to enable Continuous Delivery to `Azure App Service`.

The application is a Python-based machine learning application that works with Flask web framework. 

A pre-trained, sklearn model that has been trained to predict housing prices in Boston according to several features, such as average rooms in a home and data about highway access, teacher-to-pupil ratios, and so on is presented.![alt](https://github.com/RaymondDavison/Azure-CI-CD-Pipeline-Machine-Learning/blob/main/screenshots/0.1-Architectural%20Diagram.png)

## Project Plan
<TODO: Project Plan

* [A link to a Trello board for the project](https://trello.com/b/xWzUJi8a/build-a-machine-learning-ci-cd-pipeline-with-azure-devops)
* [A link to a spreadsheet that includes the original and final project plan](https://docs.google.com/spreadsheets/d/15L5KgQH1k4cs6h2Azz1qvHVSDlwcPpIN3TNfSySJvT8/edit#gid=1348135932)

## Instructions

Clone the repository on Azure Cloud Shell by running the following command:

`git clone git@github.com:RaymondDavison/Azure-CI-CD-Pipeline-Machine-Learning.git`

Change into the project directory `Azure-CI-CD-Pipeline-Machine-Learning`:

`cd Azure-CI-CD-Pipeline-Machine-Learning`
![alt](https://github.com/RaymondDavison/Azure-CI-CD-Pipeline-Machine-Learning/blob/main/screenshots/Screenshot%20project%20clone%20from%20Azure%20Cloud%20Shell%202022-10-02%20112312.png)

Create and Activate a Python Virtual Environment:

`python3 -m venv ~/.myrepo
 source ~/.myrepo/bin/activate`

Install dependencies in the virtual environment and run the tests:

`make all`

The Output of the tests is as follows:
![alt](https://github.com/RaymondDavison/Azure-CI-CD-Pipeline-Machine-Learning/blob/main/screenshots/2.%20make%20all%20passed%20Screenshot%202022-10-05%20091846.png)
* Output of a test run

Duplicate Azure cloudshell activate the virtual environment.

On one environment run the python application:

`python app.py`

On the other environment run the local prediction:

`./make_prediction.sh`

The output of the local prediction is displayed below:
![alt](https://github.com/RaymondDavison/Azure-CI-CD-Pipeline-Machine-Learning/blob/main/screenshots/make_predict_azure_app.sh%20result%20Screenshot%202022-10-05%20093600.png)

## Deploy the app to an Azure App Service

Create an App Service in Azure with a unique name by running the following command:

`az webapp up -n <app-unique-name>`

Create the pipeline in Azure DevOps as follows: 

- Go to https://dev.azure.com and sign in.
- Create a new private project.
- Under Project Settings create a new service connection to Azure Resource Manager, scoped to your subscription and resource group.
- Create a new pipeline linked to your GitHub repo.
The following screenshots shows the successfull running of the pipeline.
![alt](https://github.com/RaymondDavison/Azure-CI-CD-Pipeline-Machine-Learning/blob/main/screenshots/BuildJob%20Screenshot%202022-10-05%20113742.png)
![alt](https://github.com/RaymondDavison/Azure-CI-CD-Pipeline-Machine-Learning/blob/main/screenshots/DeploymentJob%20Screenshot%202022-10-05%20113857.png)

To test the app running in Azure App Service, replace the URL of the make_predict_azure_app.sh script with that of the app. Then run the following script:

`./make_predict_azure_app.sh`

If it's working the output should look like the following:
![alt](https://github.com/RaymondDavison/Azure-CI-CD-Pipeline-Machine-Learning/blob/main/screenshots/make_predict_azure_app.sh%20result%20Screenshot%202022-10-05%20093600.png)

You can also visit the URL of the App Service via the browser and you should see the following page:
![alt](https://github.com/RaymondDavison/Azure-CI-CD-Pipeline-Machine-Learning/blob/main/screenshots/sklearn%20predictionhome%20Screenshot%202022-10-05%20092900.png)

Also, the app's logs can be viewed by running:

`az webapp tail log`
![alt](https://github.com/RaymondDavison/Azure-CI-CD-Pipeline-Machine-Learning/blob/main/screenshots/1-tail%20logs%20Screenshot%202022-10-05%20103738.png)

## Load testing
We can use locust to do a load test against our application. In this example, the load test is done against the app running locally.

`locust -f locustfile.py --headless -u 20 -r 5 -t 20s`
output 
![alt](https://github.com/RaymondDavison/Azure-CI-CD-Pipeline-Machine-Learning/blob/main/screenshots/locustfile%20output%20Screenshot%202022-10-05%20105013.png)


* Successful deploy of the project in Azure Pipelines.  [Note the official documentation should be referred to and double checked as you setup CI/CD](https://docs.microsoft.com/en-us/azure/devops/pipelines/ecosystems/python-webapp?view=azure-devops).

* Running Azure App Service from Azure Pipelines automatic deployment

* Successful prediction from deployed flask app in Azure Cloud Shell.  [Use this file as a template for the deployed prediction](https://github.com/udacity/nd082-Azure-Cloud-DevOps-Starter-Code/blob/master/C2-AgileDevelopmentwithAzure/project/starter_files/flask-sklearn/make_predict_azure_app.sh).
The output should look similar to this:


## Enhancements

This is so far a great job done. At this moment, one can start thinking about how to deploy to production environments. It would be a nice idea to always create a branch for any modifications which can be tested and deployed to a staging environment before before deploying to production.

## Demo 

<TODO: Add link Screencast on YouTube>


