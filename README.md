Kelvin Nguyen 
CIS 3920
Term Research Report
Anti-Lgbtq Hatecrimes and Anti-Lgbtq Legislation in 2021

How to view code: 

code is under the IPYNB file as 'cis2920project'

Problem

Does the number of anti-lgbtq hate crimes correlate to number of anti-lgbtq legislation passed within the same year?
What contributes to such high lgbtq hate crimes? 

Introduction

Within the past couple of years, there has been a huge anti-lgbtq movement mainly from right-wing / religious groups. In addition, with the Supreme Court’s overturning of Roe v.Wade, Supreme Court Justice Samuel Alito referred to overturning Obergefell v. Hodges (legalizing gay marriage). In addition, in 2022 and 2023, there has been a huge wave of not only anti-lgbtq legislation being passed, but huge turnovers of gender-affirming care. An alarming example was on April 19th of 2023, Florida’s senate passed bill CS/SB 254 to the house with 82 YEAS and 31 NAYS. This law grants the state of Florida temporary emergency custody over a child that had recently been subjected to sex-reassignment prescriptions or procedures, thus removing custody of a transgender child from their parents. Out of concern, we thought it would be interesting to see if there is a correlation between the number of hate crime incidents that occur and are correlated respective to one’s state’s government / legislation. Thus we would need a total number of laws per state and hate crimes per state that pertain to anti-gender/ non-gender conforming/ gender identity related crimes. 

Project Description/ Abstract
 
We decided to do this project because it has been a politically stigmatizing topic even though it shouldn’t be political. This project would steer a path towards human rights and experiment to see if these laws contribute to such discrimination and eventually towards an increased crime rate towards these groups of people. We trained regression, support vector machines, and random forest models in order to test this hypothesis. 

Dataset 

The datasets we used are from the FBI’s 2021 hate crime database and the ACLU’s 2021 anti-lgbtq legislation tracker as well as Ballotpedia’s state level government majorities. Such contained information such as: 
State 		Incidents 		Crime Type		
Bill Number 		Bill Type 		Date
Incident Bias 		Victim Type 		Percent Democratic
Percent Republican 		Senate Majority	House Majority

Literature Survey

Although there are many companies that keep track of anti-lgbtq legislation, yet anyone has tested the hypothesis of whether or not these laws actually contribute to increased hatecrimes. Given that it would seemingly be obvious, it can be argued that most of those who ideologically align as anti-lgbtq would not keep up with all legislation being passed so there is a high possibility of no correlation, which companies would be hesitant to enact upon. Yet, here our goal was to do this, even if it would be either ‘obvious’ or common knowledge purely for analytical purposes. Most activism companies such as the ACLU make sure to spread awareness on these types of bills in order for citizens to use their voices towards their local congressmen and women. Most of these bills do in fact restrict the freedom of those who have sought gender-affirming care or went through gender-reassignment procedures. For instance, many transgender people are unable to compete in sports or use public restrooms or even be allowed to express themselves if they are a minor. Such behavior could lead to conversion therapy which is incredibly mentally taxing upon the youth to dismiss their expression. However our project does not consider this into our scope, we purely are just testing for a relationship between the number of legislation and the number of anti-lgtbq hate crimes in the 50 states of America. 

Project Methodology
1.	We analyzed the data provided within all 14 FBI tables, using mainly table 13’s hate crime per bias motivation per state. 
2.	We grouped said data by state. 
3.	We used webscraping to retrieve the ACLU's anti-lgbtq legislation tracker from the following website: https://www.aclu.org/legislation-affecting-lgbtq-rights-across-country-2021.
4.	Again, we grouped by state and made a count per state, then aggregated both data frames into 1 big one. 
5.	Then we took the Ballotpedia’s federal election and state government statistics into the dataframe:
a.	Number voted for democrats
b.	Number voted for republicans 
c.	Percent democrats 
d.	Percent republican 
e.	Senate majority (categorical of rep or dem)
f.	House majority (categorical of rep or dem)
6.	In Regression we used libraries: 
a.	Ggplot2
b.	tidyverse
7.	In SVM we used Libraries:
a.	e1071
b.	caTools
8.	In Random Forest we used libraries: 
a.	randomForest
b.	Datasets
c.	Tidyverse
d.	Corrplot
e.	Caret
f.	Grid
g.	grid  extra
h.	caTools
i.	Rpart
j.	Rpart.plot
k.	GGally
l.	dyplr

Analysis and Results

![Screenshot 2023-06-30 194548](https://github.com/kelvinnn25/antilgbtqlegislationandcrimes/assets/80852728/62da1852-26d5-4b7b-a8a3-55f5d2fa0e9b)

This is the summary of the dataset when fully aggregated and named merged. This includes hate crime data per state, total laws (and types), population, # and % of either democrat or republican per state, and senate/house majority. 

Total anti-lgbtq hatecrimes equate to 1590, and 170 anti-lgbtq laws passed. 
There is an average of 31.8 anti-lgbtq hatecrimes per state and 3.4 anti-lgbtq legislation passed. 

![Screenshot 2023-06-30 194609](https://github.com/kelvinnn25/antilgbtqlegislationandcrimes/assets/80852728/849a520b-e819-4542-8dcb-f890a63a273d)

above is the graph of number of anti-lgbtq hatecrimes

![Screenshot 2023-06-30 194619](https://github.com/kelvinnn25/antilgbtqlegislationandcrimes/assets/80852728/b96d7188-60bd-4e8b-9e9e-21ed823a0054)

above is the graph of number of anti-lgbtq legislation 
Regression: 

![Screenshot 2023-06-30 194632](https://github.com/kelvinnn25/antilgbtqlegislationandcrimes/assets/80852728/928781c7-232b-4c09-b724-093a9488c00d)


In the image above, it is evident that linear regression was not successful given that there was a very high value of p of 0.14 and low correlation coefficient of .207. Therefore it is safe to assume that there is no linear correlation between the number of anti-lgbtq laws passed and anti-lgbtq hatecrimes. Below are the residuals and Q-Q plot.

![Screenshot 2023-06-30 194643](https://github.com/kelvinnn25/antilgbtqlegislationandcrimes/assets/80852728/8eabf8dd-d321-414c-a4f0-ccb3d6be63e5)

As we can see here, simple linear regression is too sensitive to the data here to outliers. In addition, the Q-Q plot has data points that somewhat fall on the line but there is too much data that simply do not fit into this distribution with high outliers. Considering this model had an RSE of 33.29 on 48 degrees of freedom, this model performed poorly.

So we thought of a solution using lgbtq crime as a percentage of all hate crimes per state and modeled it. 

![Screenshot 2023-06-30 194654](https://github.com/kelvinnn25/antilgbtqlegislationandcrimes/assets/80852728/06fd5354-deb9-46e3-a90e-d533e1246f0e)


It performed poorly too. The correlation coefficient came out to be .055 and here is the summary of the model. Therefore it was concluded that there is no linear correlation for this dataset. 


![Screenshot 2023-06-30 194707](https://github.com/kelvinnn25/antilgbtqlegislationandcrimes/assets/80852728/d17da76c-f7c7-4983-879e-d8ffc95048d8)


Support Vector machines: 

First I labeled each state based on their senate majority. 0=democrat 1= republican 
Using hate crimes as response variable and total anti-lgbtq as predictor variable:

![Screenshot 2023-06-30 194720](https://github.com/kelvinnn25/antilgbtqlegislationandcrimes/assets/80852728/3e15e6be-723f-4d65-b6c9-48c796f91717)

Now we split the data with a .75, .25 ratio


![Screenshot 2023-06-30 194739](https://github.com/kelvinnn25/antilgbtqlegislationandcrimes/assets/80852728/09e2b28f-3952-45fd-ac7f-315b0a80b88e)

Train set using strictly 0= democrat and 1= republican, crimeSum as response variable.
Test set results:
![Screenshot 2023-06-30 194752](https://github.com/kelvinnn25/antilgbtqlegislationandcrimes/assets/80852728/cad7d9e8-cd5a-49ff-b753-694da28eb9c5)

Confusion matrix for test set: 

![Screenshot 2023-06-30 194804](https://github.com/kelvinnn25/antilgbtqlegislationandcrimes/assets/80852728/d7a52b0f-47c5-4d48-a981-fc53011abceb)

In the confusion matrix above:

![Screenshot 2023-06-30 194814](https://github.com/kelvinnn25/antilgbtqlegislationandcrimes/assets/80852728/034df646-4828-44bb-ae7d-a87fa793182a)

remember that 0 is Democrat and 1 is Republican majority Senate
- 2 false Democratic
- 1 false Republican
- 3 correct for Democratic
- 6 correct for Republican


- 75% accuracy rate
- 8.33% false republican rate
- 16.67% false democratic


I will discuss these results in the next section of the paper, but I still need to present the results for the random forest model. 


Random Forest, plot of actual DEM vs REP senate counts

![Screenshot 2023-06-30 194824](https://github.com/kelvinnn25/antilgbtqlegislationandcrimes/assets/80852728/0b39fd75-9171-4482-98e4-dff0a4bd2e5b)

Dataset used to predict, removed Democratic count for 2020 election, Republican count, to avoid better predictions.

![Screenshot 2023-06-30 194835](https://github.com/kelvinnn25/antilgbtqlegislationandcrimes/assets/80852728/aeec0376-37d8-42b3-ad8b-21c7b1b4031d)


Prediction for train: 100% accuracy 

![Screenshot 2023-06-30 194845](https://github.com/kelvinnn25/antilgbtqlegislationandcrimes/assets/80852728/28264325-4944-436e-b0e9-b5dae898abeb)


Prediction for test 87.5% accuracy rate
![Screenshot 2023-06-30 194856](https://github.com/kelvinnn25/antilgbtqlegislationandcrimes/assets/80852728/afd1de90-0e99-49f1-b978-0ad326641ab3)

Random forest graph
![Screenshot 2023-06-30 194907](https://github.com/kelvinnn25/antilgbtqlegislationandcrimes/assets/80852728/bdeb460e-1c06-4a50-a217-b71f077752d4)

![Screenshot 2023-06-30 194919](https://github.com/kelvinnn25/antilgbtqlegislationandcrimes/assets/80852728/2a471504-c107-41e2-92f1-95c2300ff667)


![Screenshot 2023-06-30 194929](https://github.com/kelvinnn25/antilgbtqlegislationandcrimes/assets/80852728/0f8d1d28-9323-4591-bf88-d38b19c68cef)

As we can see from the results, Anti-Freq laws had the most importance when splitting the data into democratic/republican majority states.

Summary: 

Out of the three models, the only one with success was random forest in order to classify senate majority of the state, which contributes to the state’s laws. It was able to have a 100% training set prediction rate and 87.5% testing set prediction rate. Else, regression and SVM models performed very poor. In the random forest, predictors included total anti-lgbtq hate crimes and total anti-lgbtq legislation grouped by state, ass well as population and a number of presidential democratic and republican voter count, and lastly, LGBTQ hate crime percentage compared to cumulative hate crimes. This is considered a success, being that the most influential variable according to the GINI index would be antiFreq which was the count of anti-LGBTQ laws. 

Struggles and Roadblocks:

My main priority with this project was assessing the years 2022 and 2023, for having back-to-back record-breaking anti-LGBTQ legislation. Prior to 2021, we experienced a pandemic that significantly decreased hate crimes for that year due to quarantine. In addition, just within the first quarter of 2023, there have been over 400 anti-LGBTQ legislation, where in 2021 there were 158, and in 2022 there were 180, according to the ACLU’s data depicted by CNN below.
 
However, when I requested datasets from the FBI for either 2022 or whatever was recorded of 2023 hatecrimes, they were unable to give me the information. In addition, a major roadblock encountered was the ACLU’s data for 2021, stating that they were unable to give me datasets for that too, therefore a significant portion of my efforts on this project included data scraping off of their public archives. 
Also, it is important to mention that there is a potential huge margin of error for hatecrimes based on how state agencies report them. You can find more information at this link. There could be a huge number of crimes that go unreported each year due to intimidation or overlooking certain aspects. There is potential that one’s own ideological beliefs or tolerance for the acknowledgement of other’s beliefs may have led to either overreported or underreported crimes. For instance when running the regression for total crime sums I ran into many outliers. 


 
Some major outliers included Ohio and Washington. Both of which had very little anti-lgbtq laws passed that year yet a significantly high number of anti-lgbtq hatecrimes.
Texas as well had the second most hatecrimes at 566 (Washington at first), yet Texas was also an outlier due to how high the laws were and how high the crime was. 
But the most interesting state was Florida.
 
 
Florida had no anti-lgbtq laws and no hatecrimes of any type reported. For such large population state:
 
The FBI database actually shows us that only 2 agencies reported for Florida whereas you could see other states having significantly more. Therefore Florida created a huge problem for all my models and such poor reporting. Perhaps these issues must be addressed in the future. 

Conclusion:

To conclude: there is no direct relationship as of 2021’s lgbtq hatecrime’s and anti-lgbtq legislation. Therefore my original hypothesis was wrong and H0 correct. However, in the experiment with running random forest, it is at least relevant in the context that there is a correlation between increased rate of anti-lgbtq laws and increased number of lgbtq hate crimes. Although I was not able to experiment with 2022’s data, this could potentially attribute to future experiments. I definitely will return to this project, in an expected two years when the data is publicized by both the ACLU and FBI. Regardless of these results, it is clear that many will propose this project to be too politically aligned. However, in the context of human rights, anti-lgbtq and specifically this new wave of anti-transgenderism within American government creates no benefit towards anyone in any form. People should be free to express themselves in a form that does not harm others. In addition, this project shows the flaws within Florida’s hate crime reporting, which should be addressed for the benefit of those harmed. Without the necessary data, more problems will build on without knowing its root. Perhaps in the future a potential project could be using politicians’ themselves as a source of crime rate or legislation passed. For instance, many of those in congress are heavily present on media outlets such as Twitter. Therefore, their activity could determine potential laws to be passed or a trend in certain legislation and how it affects crime rate. 

Contributions:

Though many corporations and media outlets heavily follow anti-lgbtq legislation, work has yet to be done on the relationship between hate crimes and lgbtq legislation passed. 

References:

https://www.aclu.org/legislation-affecting-lgbtq-rights-across-country-2021 
https://www.aclu.org/legislative-attacks-on-lgbtq-rights
https://www.cnn.com/2023/04/06/politics/anti-lgbtq-plus-state-bill-rights-dg/index.html
https://www.r-bloggers.com/2021/04/random-forest-in-r/
https://www.kaggle.com/datasets/paultimothymooney/percent-voting-for-democratic-party-by-state

Appendix:
https://www.kaggle.com/code/kelvinnn25/cis3920project
