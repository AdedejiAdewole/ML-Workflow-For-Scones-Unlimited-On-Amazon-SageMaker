# ML-Workflow-For-Scones-Unlimited-On-Amazon-SageMaker
The main objective of this project is to build and deploy a Image Classification ML model for Scones Unlimited, a scone delivery logistics company using Amazon SageMaker.

# Project
Build and Monitor a Machine Learning Workflow For Scones Unlimited On Amazon SageMaker.

## 1. Overview
This project was a part of the project assessment in the 'AWS x Udacity's Machine Learning Engineer Nanodegree Scholarship Program'.

## 2. Getting Started
### 2.1 Project Files

1. starter.ipnyb: This Jupyter notebook contains a machine learning working workflow for Image Classification. This includes the necessary preprocessing of the required scones unlimited image datasets, model training, deployment and monitoring using Amazon SageMaker and other associated AWS Services.
2. starter.html: Web-page displaying 'starter.ipynb'.
3. Lambda.py: assembling the required "lambda.py" scripts for three AWS Lambda functions to build a Step Functions workflow. (Note: The 'lambda_handler' function, normally included in the 'lambda.py' file, serves as the entry point for the Lambda function when it is called by an event like an HTTP request or a scheduled cron job. The 'event' object, which has details about the triggering event, and the 'context' object, which contains details about the current execution environment, are sent to this function. The basic functionality of the Lambda function is carried out in the 'lambda_handler' function, which can also interface with other AWS services, carry out calculations, and process data. The Lambda function may also provide a response to the service or client that called it.)
4. Screenshot showcasing working step function.png: screen shot of working step function.
5. step function.json: Step Function exported to JSON

### 2.2 Dependencies
Python 3 (Data Science) - v3.7.10 kernel
ml.t3.medium instance
Python 3.8 runtime for the AWS Lambda Functions

### 2.3 Installation
- For local development, you will need to setup a jupyter lab instance.

+ Follow the [jupyter install](https://jupyter.org/install.html) link for best practices to install and start a jupyter lab instance.
If you have a python virtual environment already installed you can just pip install it.

  ```
  pip install jupyterlab
  ```

* There are also docker containers containing jupyter lab from [Jupyter Docker Stacks](https://jupyter-docker-stacks.readthedocs.io/en/latest/index.html).

## 3. Approach
With the aid of AWS Step Functions and Lambda functions, the project seeks to create a machine learning model for picture categorization by automating a variety of machine learning activities, including data preparation, model training, deployment, and inference.

### 3.1 Lambda Functions
1. The serializeImageData lambda function ([zipped lambda script](https://github.com/AdedejiAdewole/ML-Workflow-For-Scones-Unlimited-On-Amazon-SageMaker/blob/main/lambda%20functions/serializeImageData.zip))will copy an object from S3, base64 encode it, and then returns it to the step function as a serialized JSON object in an event.
2. The Image-Classification lambda function ([zipped lambda script](https://github.com/AdedejiAdewole/ML-Workflow-For-Scones-Unlimited-On-Amazon-SageMaker/blob/main/lambda%20functions/image-classification.zip)) takes the image output from the previous function, decode it, and then pass inferences back to the the Step Function.
3. The Filter-Low-Confidence-Inference lambda function ([zipped lambda script](https://github.com/AdedejiAdewole/ML-Workflow-For-Scones-Unlimited-On-Amazon-SageMaker/blob/main/lambda%20functions/filter-low-confidence.zip)) takes the inference data from step 2, and filters only the images that meet the pre-defined threshold.

### 3.2 Building a State Machine via AWS Step Functions

#### 3.2.1. Execution Flow of the Step Function

![4B74F74D-785C-4DF7-82E0-D8AB953F1139_1_201_a](https://github.com/AdedejiAdewole/ML-Workflow-For-Scones-Unlimited-On-Amazon-SageMaker/assets/50617984/2be3d93a-f588-49c5-9660-92ab795224f6)

#### 3.2.2. Step Function Graph

![14933091-3BFE-4DD0-8B3F-ADD98D233065_1_201_a](https://github.com/AdedejiAdewole/ML-Workflow-For-Scones-Unlimited-On-Amazon-SageMaker/assets/50617984/d75e71b7-65b8-4662-8347-67f94ece0611)


#### 3.2.3. Step Function Output


![29FD3E53-6FAB-4E59-B378-59DF3F44B5CD_1_201_a](https://github.com/AdedejiAdewole/ML-Workflow-For-Scones-Unlimited-On-Amazon-SageMaker/assets/50617984/b43c4892-1b31-4a99-8d21-4b976a76429b)

## LICENCE
[LICENSE](https://github.com/AdedejiAdewole/ML-Workflow-For-Scones-Unlimited-On-Amazon-SageMaker/blob/main/LICENSE)








