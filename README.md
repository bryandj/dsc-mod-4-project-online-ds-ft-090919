# Module 4 -  Final Project

> what are the top 5 best zipcodes for us to invest in?

Section 1: Load Data & Import Libraries
- Define functions
- import helper functions

Section 2: Exploratory Data Analysis - Georgia zipcodes
Section 2a: Change 'dates' column to datetime format & set 'dates' column as the index

<img src="images/Top5_ATL.png"/>
<img src="images/avg_price_ga_counties.png"/>

Section 3: Zip Code Selection
- Real estate investment firm criteria

1) Urbanization - Zip Code must be in top 50% according to sizerank variable.
** In the Greater Atlanta area, commuting is tough with traffic, so living in a suburb/area within 45min driving distance is essential.
** I hypothesize that the best investment opportunities will be found just outside the perimeter in growing suburbs. 

2) Average House price
** House price should be close to the average house price for that zipcode, preferably lower.
** Range - 1.5 decile below and 1 decile above.

3) ROI (Return on investment)
** Investment Company wants to know which zipcodes will have the greatest 10 year ROI.

4) Risk
** Risk averse investment company. Want zip codes to be selected according to a coefficient of variation below 70th percentile.

<img src="images/t5_zips.png"/>


## Top 5 Zipcodes

#### Zipcode 30080 - Smyrna, GA
#### Zipcode 30066 - Marietta, GA
#### Zipcode 30064 - Marietta, GA
#### Zipcode 30152 - Kennesaw, GA 
#### Zipcode 30101 - Acworth, GA


Section 4: Time Series Analysis
Section 4a: Reshaped data from wide to long format
Section 4b: Set 'time' column as index

<img src="images/ga_t5_ts.png"/>

Monthly Returns
<img src="images/mr_30080.png"/>

Rolling Mean
<img src="images/rolling_30080.png"/>

ADF
<img src="images/adf.png"/>

## ARIMA Modeling

<img src="images/acf.png"/>


## SARIMA

<img src="images/sarima_30080.png"/>

Train
<img src="images/train_30080.png"/>
Test
<img src="images/test_30080.png"/>
Forcast
<img src="images/forcast_30080.png"/>

Results
<img src="images/results.png"/>


## Reccomendations

#### After performing time series analysis on the top 5 zipcodes in the greater atlanta area, I recommend investing in 3:

#### 1) 30080 (Smyrna, GA) -> 10-yr return = 430.62%
#### 2) 30101 (Acworth, GA) -> 10-yr return = 141.87%
#### 3) 30066 (Marietta, GA) -> 10-yr return = 124.46%

#### The predicted return on investment for zipcode 30080 is much higher than the other, look in Smyrna, GA first.












## Introduction

In this lesson, we'll review all the guidelines and specifications for the final project for Module 4.

## Objectives

* Understand all required aspects of the Final Project for Module 4
* Understand all required deliverables
* Understand what constitutes a successful project


### Final Project Summary

Another module down--you're absolutely crushing it! For this project, you'll get to flex your **_Time-Series_** muscles!

<img src='https://raw.githubusercontent.com/learn-co-curriculum/dsc-mod-4-project/master/images/timegif.gif'>

For this module's final project, we're going to put your newfound **_Time Series Analysis_** skills to the test. You will be forecasting real estate prices of various zipcodes using data from [Zillow](https://www.zillow.com/research/data/). However, this won't be as straightforward as just running a time-series analysis--you're going to have to make some data-driven decisions and think critically along the way!

### The Project

For this project, you will be acting as a consultant for a fictional real-estate investment firm. The firm has asked you what seems like a simple question:

> what are the top 5 best zipcodes for us to invest in?

This may seem like a simple question at first glance, but there's more than a little ambiguity here that you'll have to think through in order to provide a solid recommendation. Should your recommendation be focused on profit margins only? What about risk? What sort of time horizon are you predicting against?  Your recommendation will need to detail your rationale and answer any sort of lingering questions like these in order to demonstrate how you define "best".

As mentioned previously, the data you'll be working with comes from the [Zillow Research Page](https://www.zillow.com/research/data/). However, there are many options on that page, and making sure you have exactly what you need can be a bit confusing. For simplicity's sake, we have already provided the dataset for you in this repo--you will find it in the file `zillow_data.csv`.

## The Deliverables

The goal of this project is to have you complete a very common real-world task in regard to Time-Series Modeling. However, real world problems often come with a significant degree of ambiguity, which requires you to use your knowledge of statistics and data science to think critically about and answer. While the main task in this project is Time-Series Modeling, that isn't the overall goal--it is important to understand that Time-Series Modeling is a tool in your toolbox, and the forecasts it provides you are what you'll use to answer important questions.

In short, to pass this project, demonstrating the quality and thoughtfulness of your overall recommendation is at least as important as successfully building a Time-Series model!

Online students should complete the following 4 deliverables for this project:

* A well-documented **_Jupyter Notebook_** containing any code you've written for this project (use the notebook in this repo, `mod_4_starter_notebook.ipynb`). This work will need to be pushed to your GitHub repository in order to submit your project.
* An organized **README.md** file in the GitHub repository that describes the contents of the repository. This file should be the source of information for navigating through the repository.
* A **_[Blog post](https://github.com/learn-co-curriculum/dsc-welcome-blogging)_**.
* An **_'Executive Summary' PowerPoint Presentation_** that explains your rationale and methodology for determining the best zipcodes for investment.

Note: On-campus students may have different deliverables, please speak with your instructor.

### Jupyter Notebook Must-Haves

For this project, you will be provided with a jupyter notebook containing some starter code. If you inspect the zillow dataset file, you'll notice that the datetimes for each sale are the actual column names--this is a format you probably haven't seen before. To ensure that you're not blocked by preprocessing, we've provided some helper functions to help simplify getting the data into the correct format. You're not required to use this notebook or keep it in its current format, but we strongly recommend you consider making use of the helper functions so you can spend your time working on the parts of the project that matter.

#### Organization/Code Cleanliness

The notebook should be well organized, easy to follow, and code is modularized and commented where appropriate.

* Level Up: The notebook contains well-formatted, professional looking markdown cells explaining any substantial code. All functions have docstrings that act as professional-quality documentation.
* The notebook is written to technical audiences with a way to both understand your approach and reproduce your results. The target audience for this deliverable is other data scientists looking to validate your findings.
* Data visualizations you create should be clearly labeled and contextualized--that is, they fit with the surrounding code or problems you're trying to solve. No dropping data visualizations randomly around your notebook without any context!

#### Findings

Your notebook should briefly mention the metrics you have defined as "best", so that any readers understand what technical metrics you are trying to optimize for (for instance, risk vs profitability, ROI yield, etc.). You do **not** need to explain or defend your your choices in the notebook--the blog post and executive summary presentation are both better suited to that sort of content. However, the notebook should provide enough context about your definition for "best investment" so that they understand what the code you are writing is trying to solve.

#### Visualizations

Time-Series Analysis is an area of data science that lends itself well to intuitive data visualizations. Whereas we may not be able to visualize the best choice in a classification or clustering problem with a high-dimensional dataset, that isn't an issue with Time Series data. As such, **_any findings worth mentioning in this problem are probably also worth visualizing_**. Your notebook should make use of data visualizations as appropriate to make your findings obvious to any readers.

Also, remember that if a visualization is worth creating, then it's also worth taking the extra few minutes to make sure that it is easily understandable and well-formatted. When creating visualizations, make sure that they have:

* A title
* Clearly labeled X and Y axes, with appropriate scale for each
* A legend, when necessary
* No overlapping text that makes it hard to read
* An intelligent use of color--multiple lines should have different colors and/or symbols to make them easily differentiable to the eye
* An appropriate amount of information--avoid creating graphs that are "too busy"--for instance, don't create a line graph with 25 different lines on it

<center><img src='images/bad-graph-1.png' height=100% width=100%>
There's just too much going on in this graph for it to be readable--don't make the same mistake! (<a href='http://genywealth.com/wp-content/uploads/2010/03/line-graph.php_.png'>Source</a>)</center>

### Blog Post Must-Haves

Refer back to the [Blogging Guidelines](https://github.com/learn-co-curriculum/dsc-welcome-blogging) for the technical requirements and blog ideas.


### Executive Summary Must-Haves

Your presentation should:

Contain between 5-10 professional quality slides detailing:

* A high-level overview of your methodology and findings, including the 5 zipcodes you recommend investing in
* A brief explanation of what metrics you defined as "best" in order complete this project

As always, this prresentation should also:

* Take no more than 5 minutes to present
* Avoid technical jargon and explain results in a clear, actionable way for non-technical audiences.

## Grading Rubric 

Online students can find a PDF of the grading rubric for the project [here](https://github.com/learn-co-curriculum/dsc-mod-4-project/blob/master/module4_project_rubric.pdf). _Note: On-campus students may have different requirements, please speak with your instructor._
