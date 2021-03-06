---
title: "Machine Learning vs Traditional Programming"
date: 2022-07-16T11:30:03+00:00
# weight: 1
# aliases: ["/first"]
tags: ["machine learning","AI"]
categories: ["Machine Learning","ML","AI","Technical"]
author: "Me"
# author: ["Me", "You"] # multiple authors
showToc: true
TocOpen: true
draft: false
hidemeta: true
comments: false
# description: "Desc Text."
canonicalURL: "https://canonical.url/to/page"
disableHLJS: true # to disable highlightjs
disableShare: true
disableHLJS: false
hideSummary: false
searchHidden: false
ShowReadingTime: true
ShowBreadCrumbs: true
ShowPostNavLinks: true
ShowWordCount: true
ShowRssButtonInSectionTermList: true
UseHugoToc: true
cover:
    image: "<image path/url>" # image path/url
    alt: "<alt text>" # alt text
    caption: "<text>" # display caption under cover
    relative: false # when using page bundles set this to true
    hidden: true # only hide on current single page
editPost:
    URL: "https://github.com/<path_to_repo>/content"
    Text: "Suggest Changes" # edit text
    appendFilePath: true # to append file path to Edit link
---
<!-- # Machine Learning vs Traditional Programming -->

So, In case of **Supervised Learning ,**  how an algorithm learns by itself ? To understand it , lets first understand difference between Rule based and Data based algorithms.

![ML vs Traditional Programming](images/1_ml-vs-tp.png)

**Traditional Programming** paradigm focusses more on creating task specific algorithms, by coding a rule engine. The best example is *if-else  *****statements in a program:

```python
if age <= 10:
	print("Infant")
elif age > 10 & age < 20:
	print("Teenage")
else:
	print("Adult")
```

In above code, we are providing a standard rule for the program to work, it takes input as **age (*data)*** and through coded rules, it outputs the result.

While, in case of **Machine learning**, the rules or algorithms are calculated/determined by the data itself, provided along with the historical result, pertaining to the data input.

```python
|Country  |City   |Ethnicity   |Age   |Category
India      Pune   Indian        31     Adult
India      Mumbai Indian        32     Adult
USA        NYCity American      16     Teenage
```

The data provided can be an input to our computation machine (responsible for creating an algorithm). Within that dataset, *Country, City, Ethnicity & Age (Data)* are independent variables, based on which a dependent variable ***Category (Results)*** is determined.

Based on a some algorithm finding techniques and skills, we automatically create an algorithm which on receiving inputs as provided in the training data, will automatically determine the Category (Result) . In this we case, we do not explicitly code the rules as we do in traditional programming.

***Example***: 
I have a thermometer which can display temperatures in degree Celsius as well as in Fahrenheit, but unfortunately, Fahrenheit display has stopped working, but Celsius is showing data correctly. There are 2 ways I can solve this problem:

1. *Traditional programming way:*   By using the Celsius to Fahrenheit conversion formula as mentioned:

![ML vs Traditional Programming](images/1_celsius.png)

1. *Machine learning way:*   Assuming data from the thermometer is being collected, we have data in Celsius and Fahrenheit both before malfunctioning of the meter. And after that, we only have data in Celsius.

```python
# data generated by thermometer
|Celsius  |Fahrenheit |Date      |Time
39         102.2       01-03-22   13.00
26         78.8        01-03-22   19.00
39         102.2       02-03-22   13.00
39         102.2       02-03-22   19.00
39         102.2       03-03-22   13.00
39         102.2       03-03-22   19.00
39         102.2       04-03-22   13.00
39         102.2       05-03-22   19.00
.          .           .          .
.          .           .          .
.          .           .          .
.          .           .          .
36         _           31-03-22   19.00
40         _           01-04-22   13.00
23         _           01-04-22   19.00
.          .           .          .
.          .           .          .
.          .           .          .
```

As you can see in above sampled data, we have data in Fahrenheit till 30-03-22, after that thermometer malfunctioned and stopped recording data in Fahrenheit.

We will utilize the data till 30-06-22 for training our machine learning model and we will run the model to predict the temperature in Fahrenheit.

For that. we will require below steps:

```python
# 1. Define input and target variables
	input=data['Celsius']
	target=data['Fahrenheit']

# 2. Divide the data into test and train dataset 
	x_train=input[:len(input)*0.80]
	y_train=target[:len(target)*0.80]

	# 80 % train data and 20 % test data

	x_test=input[len(input)*0.80:]
	y_test=target[len(target)*0.80:]

# 3.  Create a Machine Learning Hypothesis
	y = w1*x+ w0

# 4. Define a loss function RMSE
	loss=((y-target)**2).mean().sqrt()

# 5. Train and test the model to minimize the loss for both train and test data
# to get final model

	y = 1.7999*x +32
```

Above psuedo code represents some very basic steps performed in ML. Not going into detail, listing down the steps with one liner explainations:

1. **Defining Input & Target :** So essentially, ML is driven by some training data which represents the algorithm that is to be generated. From a corpus of the available data, major part is extracted as training data which contains two parts Features and Target variables (Output). 

2. **Splitting data into Train and Test**
To validate the efficiency of our trained model, we set aside some proportion of test data taken from the corpus, we pass known features from test data to the model, model predicts the target variable (say *y_pred*). Finally this value compared with the actual value present in the target variable of test data (*y_actual*), **comparison tells us how good or bad our model is.
3. **Hypothesis**
Before we start training ML model, we need to do some exploratory data analysis to understand the relationship between features and targets, based on this study, we can make a guess of a rough hypothesis of ML algorithm (Linear vs Non Linear relationship). This can be repetitive process which means, we might have to experiment with multiple hypothesis to get the best to give best results.
4. **Loss**
Machine Learning model training is an iterative process, which means we attach inputs to hypothesis and calculate the output and then calculate the difference between the actual output (***y_pred - y_actual***). The goal of the training process is to make this loss as low as possible so that the model???s output matches with the actual training data target values. To achieve that we define different loss functions (Ex: RMSE (Root Mean Square Error) )

![ML vs Traditional Programming](images/1_rmse.png)

1. **Training**
Now, based on the input data, hypothesis, and loss functions, training process starts, which is an iterative process (Repeat the process of updating the weights (w0,w1,w2???.) until the loss value reaches minimum). At the end of training, we get values of weights , which can then be attached to our hypothesis to get our final model.

Of course, there are lot of elements involved in entire machine learning model determination process, above is just a conceptual / broad overview of the process.