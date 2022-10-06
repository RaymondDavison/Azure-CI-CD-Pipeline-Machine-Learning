# Overview

This project demonstrates how to build a Machine Learning CI/CD pipeline with Azure DevOps. 
A `Github repository` will be build from scratch alongside a `scaffolding` that will assist in performing both Continuous Integration and Continuous Delivery. 
Continous Integration will be done with `Github Actions` along with a `Makefile`, a `requirements.txt` and `application code` to perform an initial `lint`, `test`, and `install cycle`. The project will then be integrated with `Azure Pipelines` to enable Continuous Delivery to `Azure App Service`.

The application is a Python-based machine learning application that works with Flask web framework. 

A pre-trained, sklearn model that has been trained to predict housing prices in Boston according to several features, such as average rooms in a home and data about highway access, teacher-to-pupil ratios, and so on is presented.


## Project Plan
<TODO: Project Plan

* A link to a Trello board for the project
* A link to a spreadsheet that includes the original and final project plan>

## Instructions

![alt](https://github.com/RaymondDavison/Azure-CI-CD-Pipeline-Machine-Learning/blob/main/screenshots/0.1-Architectural%20Diagram.png)

<TODO:  Instructions for running the Python project.  How could a user with no context run this project without asking you for any help.  Include screenshots with explicit steps to create that work. Be sure to at least include the following screenshots:

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

* Successful deploy of the project in Azure Pipelines.  [Note the official documentation should be referred to and double checked as you setup CI/CD](https://docs.microsoft.com/en-us/azure/devops/pipelines/ecosystems/python-webapp?view=azure-devops).

* Running Azure App Service from Azure Pipelines automatic deployment

* Successful prediction from deployed flask app in Azure Cloud Shell.  [Use this file as a template for the deployed prediction](https://github.com/udacity/nd082-Azure-Cloud-DevOps-Starter-Code/blob/master/C2-AgileDevelopmentwithAzure/project/starter_files/flask-sklearn/make_predict_azure_app.sh).
The output should look similar to this:

```bash
udacity@Azure:~$ ./make_predict_azure_app.sh
Port: 443
{"prediction":[20.35373177134412]}
```

* Output of streamed log files from deployed application

> 

## Enhancements

<TODO: A short description of how to improve the project in the future>

## Demo 

<TODO: Add link Screencast on YouTube>


