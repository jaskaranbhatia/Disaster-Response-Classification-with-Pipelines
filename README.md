## Disaster Response Classification with Pipelines

### 1. Deployment Link
https://project-disaster-response.herokuapp.com/

### 2. Instructions to run locally:
1. Run the following commands in the project's root directory to set up your database and model.

    - To run ETL pipeline that cleans data and stores in database
        `python data/process_data.py data/disaster_messages.csv data/disaster_categories.csv data/DisasterResponse.db`
    - To run ML pipeline that trains classifier and saves
        `python models/train_classifier.py data/DisasterResponse.db models/classifier.pkl`
    
2. Run the following command in the app's directory to run your web app.
    `python run.py`

3. Go to http://127.0.0.1:5500/

### 3. Project Overview
In this project, I applied data engineering to analyze disaster data from Figure Eight to build a model for an API that classifies disaster messages.

_data_ directory contains a data set which are real messages that were sent during disaster events. I created a machine learning pipeline to categorize these events so that appropriate disaster relief agency can be reached out for help.

This project will include a web app where an emergency worker can input a new message and get classification results in several categories. The web app will also display visualizations of the data.

### 4. Project Components
There are three components of this project:

#### 4.1. ETL Pipeline

File _data/process_data.py_ contains data cleaning pipeline that:

- Loads the `messages` and `categories` dataset
- Merges the two datasets
- Cleans the data
- Stores it in a **SQLite database**

#### 4.2. ML Pipeline

File _models/train_classifier.py_ contains machine learning pipeline that:

- Loads data from the **SQLite database**
- Splits the data into training and testing sets
- Builds a text processing and machine learning pipeline
- Trains and tunes a model using GridSearchCV
- Outputs result on the test set
- Exports the final model as a pickle file

#### 4.3. Flask Web App

Running `python run.py` **from app directory** will start the web app where users can enter their query, i.e., a request message sent during a natural disaster, e.g. _"Please, we need tents and water. We are in Washington, Thank you!".

### 5. Files and structure of Project

<pre>
├── app
│   ├── run.py------------------------# FLASK FILE THAT RUNS APP
│   ├── static
│   │   └── favicon.ico---------------# FAVICON FOR THE WEB APP
│   └── templates
│       ├── go.html-------------------# CLASSIFICATION RESULT PAGE OF WEB APP
│       └── master.html---------------# MAIN PAGE OF WEB APP
├── data
│   ├── DisasterResponse.db-----------# DATABASE TO SAVE CLEANED DATA TO
│   ├── disaster_categories.csv-------# DATA TO PROCESS
│   ├── disaster_messages.csv---------# DATA TO PROCESS
│   └── process_data.py---------------# PERFORMS ETL PROCESS
├── img-------------------------------# PLOTS FOR USE IN README AND THE WEB APP
├── models
│   └── train_classifier.py-----------# PERFORMS CLASSIFICATION TASK
</pre>

### 6. Required Modules and Softwares
This project uses Python 3 and the necessary libraries are mentioned in requirements.txt. The standard libraries which are not mentioned in requirements.txt are collections, json, operator, pickle, pprint, re, sys, time and warnings.


### 7. Novelty of Project
1. The project is a NLP based project and required a lot of research. The data from figure eight was available as an SQL database, so I created an ETL Pipeline to perform data engineering and create data in csv format.

2. Further created a ML Pipeline which automated the process of model building and evaluation along with exporting the model as a pickle model.

3. Further, I used the pickle model to predict the class of disaster messages in a flask app which is further exported on Heroku. 

4. This is a unique app and can be used with twitter data to classify hashtags and predict calamities in a particular region as well. This has great application and can be a great tool for disaster classification 

### Screenshots

![screenshot_1](https://user-images.githubusercontent.com/43378659/142759729-07ee8800-2851-448f-bb7c-50f13a51538f.JPG)
![screenshot_2](https://user-images.githubusercontent.com/43378659/142759730-ad3c3d0b-18b7-4ecd-9e86-59b078dd756e.JPG)
![screenshot_3](https://user-images.githubusercontent.com/43378659/142759731-c53ce6fa-3f4f-4cbf-af11-cb5c8d873625.JPG)
![screenshot_4](https://user-images.githubusercontent.com/43378659/142759732-62cc06fc-d45e-4ae9-9eb4-d34fba94daf4.JPG)
![screenshot_5](https://user-images.githubusercontent.com/43378659/142759733-6e58fa97-9e22-455a-ace2-fd2a23124156.JPG)
![screenshots_6](https://user-images.githubusercontent.com/43378659/142759735-baf28213-a4b8-4b12-a830-8975c1276071.JPG)

