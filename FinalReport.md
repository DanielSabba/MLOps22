# Final Report

- Our Customers: Real estate agencies, insurance companies
- Team Members: Daniel Sabba - Data Scientist, Jonathan Erell, Project Leader, Yossi Gavriel - Customer Support

## Overview
Our company specializes in providing ML pipeline solutions to insurance companies and real estate agencies. Our goal is to help these businesses increase their income through the use of advanced ML techniques. Our solution includes a ML pipeline that addresses the common problems of unfairness and bias in models, as well as reducing the prediction runtime process and increasing overall performance.

Our pipeline includes several features that are designed to combat bias and unfairness in models. We use state-of-the-art techniques and tools to ensure that the models we provide are fair and unbiased. Additionally, our pipeline is designed to reduce the prediction runtime process, which means that our models can provide predictions much faster than traditional models. This can lead to significant improvements in the performance of the companies that use our solution.

Overall, our solution is designed to help insurance companies and real estate agencies improve their performance and increase their income. By addressing the common problems of unfairness and bias in models, reducing prediction runtime process, and increasing overall performance, our solution provides a powerful tool that businesses can use to achieve their goals.
Business clients in the field of insurance that use machine learning typically do so to improve their underwriting processes, fraud detection, and claims management.<br> By analyzing large amounts of data, insurance companies can build machine learning models that can identify patterns and trends that might not be immediately obvious to humans.<br> These models can then be used to make more accurate predictions about the likelihood of certain events occurring, such as the probability of a claim being filed or the likelihood of a policyholder experiencing a loss.<br> This can help insurance companies to make more informed decisions about which risks to insure and at what cost, ultimately leading to more efficient and effective operations.

## Scope
**What data science solutions are we trying to build?**<br>
As a solution to our research question, we aim to develop generic pipeline that will clean, preprocess and transform all data types.<br>
further more we wish to imporve our data with feature selection techniques and data resampling/reweighting in order to imporve our baselines.<br>
**What will we do?**   <br>

In our pipeline, we will also check the fairness of the model. The data we use for modeling is mostly a reflection of the real world, and the real world can be biased, so the data and therefore the model will likely reflect that bias. To check the fairness of the model, we will examine each feature of our dataset to see if it is biased by a subclass of that feature. For example, we might define a group based on the sex of the sample, and a subgroup based on age. We might then define the privileged subgroup as old males, who may be privileged in cases of house pricing.

To check for bias in each feature, we will use the Dalex package to measure fairness, where fairness check is being checked as follows:
- Defining epsilon = 0.8 as default
- Calculate separation (R ⊥ A | Y), independence (R ⊥ A) and sufficieny (Y ⊥ A | R), where R is the model's predictions, A is te protected group, and Y is the target.
- Check for each term mentioned above, whether a model is not in the range of (epsilon, 1 / epsilon)
- If two conditions are not met, the model is said to be biased towards such feature

If we detected unfairness, we will try one or both of the following options:

 - Reweighting the data: We will obtain weights for the model training pipeline and mitigate bias in statistical parity. This method will produce weights for the given subgroup for each class.

 - Resampling the data: We will return indices of observations for the data. Similar to reweighting, this method computes the desired number of observations as if the protected variable were independent of the outcome variable (y), and based on this, it determines if the subgroup with a certain class (favorable or not) should be more or less numerous. It then performs oversampling or undersampling, depending on the case.

By using one or both of these options, we can build a more balanced dataset for the model training pipeline.

We'll also use outliers detection and removal.
Outliers are data points significantly different from most of the other data points in a dataset.
The outlier's detection is performed per feature separately and is possible only in continuous values. If some feature of the data point is detected as an outlier, this data point will be determined as an outlier.
Once we have identified the outliers in our dataset, we will choose to remove them if they are causing problems with the predictions.
For example, removing outliers may be appropriate if they skew the results. However, we should be careful about removing outliers, as they may contain valuable information about our data.

So, we'll check whether removing the outliers improves results in the pipeline. 
There are a few different ways to identify and remove outliers from a dataset.

We'll examine two well-known methods for outliers' detection and use the one that will give us the best results: 
1. Z-score: The z-score measures how many standard deviations a value is from the mean. If the z-score of a value is greater than a certain threshold (commonly 3 or 4), it can be considered an outlier.
2. Interquartile range (IQR): 
The IQR is a measure of the dispersion of a dataset and can be used to identify values that fall outside the range of "typical" values.
To calculate the quartiles of a dataset, we first need to arrange the values in numerical order.
Quartiles are values that divide a dataset into four equal parts. The first quartile (Q1) is the value that separates the lowest 25% of the data from the highest 75%. The second quartile, or median, is the value that separates the lowest 50% of the data from the highest 50%. The third quartile (Q3) is the value that separates the lowest 75% of the data from the highest 25%.

	So, we'll use the following formulas to calculate the quartiles:

	Q1 = (n+1) * (1/4)

	Median = (n+1) * (1/2)

	Q3 = (n+1) * (3/4)

	Where n is the number of values in the dataset.
	Outliers can then be identified as values that are more than x times the IQR below Q1 or above Q3.

In addition to the formulas previously mentioned, we will utilize the PyOD module to identify outliers for later removal.


**How is it going to be consumed by the customer?**<br>
To all of our cool customers, you can simply copy our pipeline implementation and run it in your environments.<br>
Playing with different pipeline params is advised !<br>

## Personnel
* **Data scientist (Daniel)** - A data scientist plays a crucial role in a project by using their skills in data
analysis, machine learning, and statistical modeling to extract valuable insights and knowledge from
data. They are responsible for collecting, cleaning, and organizing data from various sources, and
using this data to build predictive models and make data-driven decisions. In addition to analyzing
data, a data scientist may also be involved in communicating their findings to stakeholders and
collaborating with other team members to implement data-driven solutions.<br>
* **Project Lead (Jonathan)** - A project lead plays a crucial role in a project by providing direction,
leadership, and guidance to the team. They are responsible for managing the project from start to
finish, including setting project goals and objectives, developing a project plan, and ensuring that
the project is completed on time and within budget. The project lead works closely with team
members to delegate tasks, monitor progress, and address any issues or challenges that arise. They
also communicate with stakeholders, including clients, customers, and upper management, to keep
them informed of the project's progress and to address any concerns or feedback.<br>
* **Customer support (Yossi)** - Customer support plays a crucial role in a project by providing assistance
and support to customers or users of the product or service being developed. They are responsible
for answering questions, troubleshooting issues, and helping customers to resolve problems.
Customer support team members may also be responsible for gathering feedback and suggestions
from customers, and providing this information to the project team to inform product development
and improvement. They may work closely with other team members, such as product managers and
developers, to ensure that customer needs and concerns are being addressed.
The client for the dataset freMTPL2freq is a french insurance company. The client for the housing
dataset is a real estate broker.
	
## Metrics
**What are the qualitative objectives?**<br>
We will provide number of possible qualitative objectives: <br>
* Providing a more scalable ML framework <br>
* Less biased predictor <br>

**What are the quantifiable metric?** <br>
We will provide number of possible qualitative metrics: <br>
* Reducing machine learning research time <br>
* Improvement of your baselines scores by providing generic pipelines <br>
* Increase baseline models' MAE <br>
* Quantify what improvement in the values of the metrics are useful for the customer scenario <br>
* Performing generic feature-selection, data reweighting and cleaning will ensure reduced deployment time and increase model scores <br>

**What is the baseline (current) value of the metric?**<br>
We benchmark xgb regressor with two datasets, boston house price (2.87 MAE) and french motor (0.003 MAE) <br>
In regards to the fairness of the baseline model, we discovered certain features that the model is unfair towards. Specifically, for the Boston dataset, the "Indus" feature resulted in bias, as both the "independence" and "seperation" terms of the "Dalex" module exceeded the epsilon range of 0.8 - 1.25 (the default range). This indicates that the model is biased. Similarly, for the French Motor dataset, the "exposure" feature caused an unfair model, with both the "independence" and "seperation" terms again exceeding the epsilon range of 0.8 - 1.25 <br>

**How will we measure the metric?**<br>
We will compare our improved baseline with market common implementations with several datasets.<br>

## Plan
* Phase 1 - Explenatory data analysis. deadline - 24/12
  * Understand data features, behaviour, missing values and statistics.
  * Clean and log postprocessed data.
* Phase 2 - Creating baseline models. deadline - 28/12
  * What are the common models used on our dataset
  * Benchmark common models performance (MAE) 
* Phase 3 - Benchmark our propesed approches for improving client's ML. deadline - 5/1
  * Data preprocess (outlier removal).
  * Feature selection - best models to use.
  * Implement Dalex package to measure fairness.
* Phase 4 - Create a pipeline with best approaches. deadline - 31/1
  * Figure out the best tools to use (iguazio platform).
  * Encapsulate our methods in one generic pipeline.

## Architecture
* **What data do we expect? Raw data in the customer data sources (e.g. on-prem files, SQL, on-prem Hadoop etc.)**
  * We are expecting that the clients data will be on-prem csv files (structured).
  * Sampled data enough for modeling 

* **What tools and data storage/analytics resources will be used in the solution**
  * Pandas for data storage
  * SKlearn's stat filters and models
  * SKlearn's pipeline for pipeline creation
  * Dalex package
  * PyOD package
  
* **How will the score or operationalized web service(s) (RRS and/or BES) be consumed in the business workflow of the customer? If applicable, write down pseudo code for the APIs of the web service calls.**
  * Our pipeline will be fused in each of the data-scientists day-to-day work, with easy implementation and customization, providing better performance than common base model with plug-and-evaluate approach
* **How will the customer use the model results to make decisions**
  * The customer will view model scores and will decide whether to choose different pipeline params or not.
* **Data movement pipeline in production**
  * In production, a serving function / serving graph holding the pipeline implementation for easy data manipulation in production.
  * When files are stored on cloud providers, proper credentials has to be declared. ()
* **Make a 1 slide diagram showing the end to end data flow and decision architecture**
  ![my diagram](my_diagram.jpg)
    * If there is a substantial change in the customer's business workflow, make a before/after diagram showing the data flow.

## Communication
**Our team for this project:**<br>

* Daniel Sabba
* Yossi Gavriel
* Jonathan Erell

<br>
As a providers of ML pipelines for companies, we regularly meet with clients from various industries, such as insurance companies and real estate agencies. During these meetings, we typically meet with the client's point-of-contact, who is often a member of the management team or a department head. The purpose of these meetings is to discuss the client's specific needs and how my company can help improve their success through the use of ML models. During the meeting, we will discuss the client's current business challenges, their data availability and the specific areas where they are looking to improve their performance. We will also present examples of how our company has helped similar companies in the past and the potential benefits they could expect from working with us. We will also discuss the scope of the project, timelines and budgets. These meetings are an opportunity for us to understand the client's business and to tailor our solutions to their specific requirements.
