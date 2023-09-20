# Bike Sharing Assignment
> To build a multiple linear regression model for the prediction of demand for shared bikes


## Table of Contents
* [General Info](#general-information)
* [Technologies Used](#technologies-used)
* [Conclusions](#conclusions)
* [Acknowledgements](#acknowledgements)
* [Miscellaneous](#miscellaneous)

<!-- You can include any other section that is pertinent to your problem -->

## General Information
A bike-sharing system is a service in which bikes are made available for shared use to individuals on a short term basis for a price or free. Many bike share systems allow people to borrow a bike from a "dock" which is usually computer-controlled wherein the user enters the payment information, and the system unlocks it. This bike can then be returned to another dock belonging to the same system.


A US bike-sharing provider BoomBikes has recently suffered considerable dips in their revenues due to the ongoing Corona pandemic. The company is finding it very difficult to sustain in the current market scenario. So, it has decided to come up with a mindful business plan to be able to accelerate its revenue as soon as the ongoing lockdown comes to an end, and the economy restores to a healthy state. 


In such an attempt, BoomBikes aspires to understand the demand for shared bikes among the people after this ongoing quarantine situation ends across the nation due to Covid-19. They have planned this to prepare themselves to cater to the people's needs once the situation gets better all around and stand out from other service providers and make huge profits.


They have contracted a consulting company to understand the factors on which the demand for these shared bikes depends. Specifically, they want to understand the factors affecting the demand for these shared bikes in the American market. The company wants to know:

    Which variables are significant in predicting the demand for shared bikes.
    How well those variables describe the bike demands

Based on various meteorological surveys and people's styles, the service provider firm has gathered a large dataset on daily bike demands across the American market based on some factors.

Business Goal:

You are required to model the demand for shared bikes with the available independent variables. It will be used by the management to understand how exactly the demands vary with different features. They can accordingly manipulate the business strategy to meet the demand levels and meet the customer's expectations. Further, the model will be a good way for management to understand the demand dynamics of a new market. 

<!-- You don't have to answer all the questions - just the ones relevant to your project. -->

## Conclusions
### Observations
 
-   provided data has no null, no duplicate values, no outliers to be considered for removal
-   'temp' and 'atemp' are correlated with the target variable 'cnt'
-   'temp' and 'atemp' are almost perfectly correlated hence 'atemp' will be ignored 
-   More for the Year 2019 compared to Year 2018. {Based on box plot and bar plot}
-   Most in clear/ less cloudy weather and least in light snow weather. {Based on box plot and bar plot}
-   With respect to seasons: 
    -   Much in the fall and Least in the Spring 
    -   Increases from spring to summer to fall and decreases from fall to winter. {Based on box plot and bar plot}
-   With respect to months: 
    -   The month September has highest, and Jan has lowest.
    -   Increases from Jan to Jun, there is a dip in July then increase till September (peaked)     decreases  till the year end December. {Based on box plot and bar plot}
-   With respect to weekdays
    -   Saturday, Wednesday, and Thursday bit more than other days however not much significant {Based on box plot – median}
    -   There is an upward trend from Sun to Saturday (approximately) based on the bar plot visualization.
-   Average and Median of non-holidays rental is more than holidays {Based on box plot and bar plot}
-   Working day and non-working day shows almost same {Based on box plot and bar plot}
-   All variables exhibit upward trend from 2018 to 2019

### Results

#### R-Square of Train and Test

|          | Score |
| -------- | ------- |
| Train Data R-Square  | 0.826   |
| Train Data Adjusted R-Square |    0.822  |
| Test Data R-Square    | 0.812    |

#### Coefficients of each variables in the final model

|                           |  Coefficient |
----------------------      |------------
|const                      |   0.090189 |
|workingday                 |   0.056551 |
|temp                       |   0.491382 |
|season_spring              |  -0.064952 |
|season_summer              |   0.052659 |
|season_winter              |   0.096999 |
|mnth_Sep                   |   0.091602 |
|weekday_Sat                |   0.064533 |
|weathersit_LightSnow       |  -0.304122 |
|weathersit_Mist            |  -0.078644 |
|yr_2019                    |   0.233358 |

### Final Model

#### **y** =  **(0.0902)** x *const* + **(0.0566)** x *workingday* + **(0.4914)** x *temp* + **(-0.0650)** x *season_spring* + **(0.0527)** x *season_summer* + **(0.0970)** x *season_winter* + **(0.0916)** x *mnth_Sep* + **(0.0645)** x *weekday_Sat* + **(-0.3041)** x *weathersit_LightSnow* + **(-0.0786)** x *weathersit_Mist* + **(0.2334)** x *yr_2019*

- temp indicator is a prime factor
- 2019 yr has more rental than 2018
- impact of winter season is more
- If it is a light snow/ light rain time the demand goes down

## Technologies Used

- matplotlib 3.7.2
- sklearn 1.3.0
- pandas 2.1.0
- numpy 1.25.2
- seaborn 0.12.2
- statsmodels 0.14.0
- python 3.10 

## Acknowledgements
- Thanks to upgrad/ IIITB and also to the instructors for providing this assignment. Good learning experience

## Contact
- Created by [@jithendrian] (https://github.com/Jithendrian/LinearRegressionAssignment) 
- jithendrian@gmail.com 
- Assignment
    - Main folder : https://github.com/Jithendrian/LinearRegressionAssignment
    - Python/ ipynb : https://github.com/Jithendrian/LinearRegressionAssignment/blob/main/BikeSharingAssignment_Jithendrian.ipynb
    - Subjective questions : https://github.com/Jithendrian/LinearRegressionAssignment/blob/main/LinearRegressionSubjectiveQuestionsAnswers.pdf

### Miscellaneous

- If we provide train size as 0.7 and test size as 0.3 in split, we may land up in 510 and 219 which is not the sum of 730, so either we should provide test size or train size, the library will deduce from the total rows. This is due to the python floating point handling, 0.7 * 730 instead of 511.0 it will compute as 510.99999999999994 and sklearn floors this value hence we get 510 instead of 511
- I ran this assignment in two machines, RFE elimination is not consistent. While manual elimination if i hardcode (expected) to remove a particular indicator, due to this inconsistency I get key error, so I stick to one machine. In that machine, It is very consistent and same set of RFE support variables are there everytime I run. 
- Latest Matplotlib is not rendering heatmap properly