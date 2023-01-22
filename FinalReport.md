# Final Report

- Our Customers: Real estate agencies, insurance companies
- Team Members: Daniel Sabba - Data Scientist, Jonathan Erell, Project Leader, Yossi Gavriel - Customer Support

## Overview
Our company specializes in providing ML pipeline solutions to insurance companies and real estate agencies. Our goal is to help these businesses increase their income through the use of advanced ML techniques. Our solution includes a ML pipeline that addresses the common problems of unfairness and bias in models, as well as reducing the prediction runtime process and increasing overall performance.

Our pipeline includes several features that are designed to combat bias and unfairness in models. We use state-of-the-art techniques and tools to ensure that the models we provide are fair and unbiased. Additionally, our pipeline is designed to reduce the prediction runtime process, which means that our models can provide predictions much faster than traditional models. This can lead to significant improvements in the performance of the companies that use our solution. <br>

Overall, our solution is designed to help insurance companies and real estate agencies improve their performance and increase their income.
By addressing the common problems of unfairness and bias in models, reducing prediction runtime process, and increasing overall performance, our solution provides a powerful tool that businesses can use to achieve their goals.
Business clients in the field of insurance that use machine learning typically do so to improve their underwriting processes, fraud detection, and claims management.

## Business Domain

The business domain of our customer is the insurance and real estate industries. The insurance industry is a highly regulated and competitive market, in which companies provide financial protection against risks such as accidents, illnesses, and natural disasters. The real estate industry, on the other hand, involves the buying, selling, and renting of properties.

The insurance industry is a vital part of the economy, providing financial protection to individuals and businesses in the event of unexpected losses. Insurance companies use various types of models to underwrite risks and price policies, as well as to identify fraud and predict claims. The use of ML models in the insurance industry can help companies improve their underwriting and pricing processes, as well as detect fraud more efficiently.

The real estate industry is also a vital part of the economy, with the buying and selling of properties representing a significant part of GDP. The use of ML models in the real estate industry can help companies improve their property valuations, predict property prices, and assist with property management.

Our solution will be beneficial for the insurance companies and real estate agencies, as it will help them to improve their pricing and underwriting process, detect fraud and predict claims, property valuations, and assist with property management.

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
