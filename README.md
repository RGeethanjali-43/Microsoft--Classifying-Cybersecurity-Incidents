# Microsoft-Classifying-Cybersecurity-Incidents
**Objective**:

 To create a classification model that categorizes incidents as true positive (TP), benign positive (BP),   or false positive (FP) based on historical evidence and customer responses.

### **Data Description:**

**Dataset Overview**:

**Source**: Data set was already  given , train data and test data set was given separately

**Format**: The dataset in CSV format, containing both numerical and categorical features related to the threat which was happened before. 

## Features(Columns):

### Numerical Features:

Id: It indicates the normal Id
OrgId: Indicates the Original Id
IncidentId:  Unique Id for the particular incident
AlertId: Id for the Alert
DetectorId :  Unique Id of the detector
DeviceId: The Id of the particular device
Timestamp: It is a datetime type which indicates the hour minute day of the threat

**Categorical Features**:
AlertTitle : Title of the particular alert
Category : Indicates the category of the threat
EntityType :Entity type of the threat
Evidence Role: Role of the Evidence
IpAddress : Ip address of the system
Url : Web link of the site 
AccountSid : Id of the particular Account
AccountUpn : Indicates the UPN of the account
Countrycode : Code of the particular country
State : Indicates the State name 
City : City details

**Target variable**:
IncidentGrade: Which indicates whether it is True positive or false positive of Benign positive

**True positive**: If the result is true positive then it means that there is a threat and cyber security team needs to take action.

**False positive:** If the result is false positive there is no threat happened

**Benign positive**: If the result is Benign positive it needs to be judged and the cyber security team needs to work on this.

## Data Pre processing and  **Data Type conversion:**

Columns like MitreTechniques, EmailClusterid has  mixed with numerical and  alphabets, so it was

pre processed and converted to int data  type and float.

Converted the size of the integers  ex:  int64 to int32

Changed  timestamp  column spitted to new features like year ,month ,day ,minute ,hour separately.

## Data Cleaning:

### Missing Values:

Numerical features like MitreTechniques and EmailClusterid were filled using Iterativeimputer.

Since KNN imputer and mean median imputation causes bias, so Iterativeimputer was better than KNN Imputer.

Categorical features like AlertTitle and Category  were filled with IterativeImputer

Used boxplot , Histogram and Scatterplot for visualizations.

## Feature Enginnering:

### **Correlation**:

Watched the **correlation** carefully and also displayed for visualization  using Heatmap

### Encoding categorical variables:

Used Label Encoder for categorical features like , AlertTitle ,Category, EntityType ,EvidenceRole ,IpAddress, Url ,AccountSid ,AccountUpn,Countrycode,
State ,City

### Feature Importance:

  Found top 15 features using RandomForestClassifier

## Data Splitting:

### Train Test split:

The data was split to 70% training  and  30% of  testing accuracy score was calculated only with the training data, using  train_test_split() from scikit learn.  

Data Cleaning, Pre processing was done for the test data, after that it was concatenated with the train data. 

## Model Development:

### Model Selection:

The Decision Tree algorithm was chosen for ability to handle non linear relationships and complex

interactions between features which makes it suitable for classifying cyber security incidents.

### Model Training:

The  Decision Tree model was trained on the preprocessed  data using DecisionTree

class from **Scikit- Learn**

### Model Hyper Parameters:

n_estimators:  300(number of trees in the forest)

max_depth: none(max depth of each tree)

min_samples_split: 3(minimum number of samples to split mode)

random_state: 42(For reproductivity)

ROCCURVE:

Also visualized ROCcurve to see how the model is working.

## Model Evaluation:

### Metrics:

The following evaluation metrics are used to evaluate the performance of the model

Precision , Recall, F1score
Since F1 score for all the classes are better in DecisonTrees compared to   other  algorithms,

DecisionTree is finally determined as a perfect model for  Microsoft classification
