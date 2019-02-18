---
layout: post
title: Prison Recidivism
---


If considered as a single entity, the American prison population, which comes in at over two million people, would rank as the fifth most populous city, just behind Houston.<sup>1</sup>&nbsp; Each year, approximately 600,000 people, a population approaching that of Portland, are released back into the community.<sup>2</sup> It goes without saying that these are embarrassing numbers for the country often esteemed as the leader of the free world.  Recidivism is an important contributing factor to these large numnbers. Within three years of their release, two out of three prisoners are rearrested.<sup>3</sup>&nbsp; My third project for the Metis Data Science Bootcamp, discussed at length below, attempts to use supervised learning algorithms to shed some light on the main factors contributing to recidivism.

![Prison Cell](images/2-16-19/prison.jpg)

For the project, I needed a dataset that included information broken down by offender.  Luckily, the Iowa department of corrections offers a public dataset of over 26,000 records.<sup>4</sup> &nbsp;  The Iowa study tracked released ex-offenders over a three-year perior from 2013 until 2018, and includes demographic such as race and age, release type, and several layers of detail about the crime each person was sentenced for.  After dropping records with null values, I had 24,150 rows of data to analyze.  The data was imbalanced: it included a ratio of about 1 recidivist to 2 non-recidivist.  It also included a heavy racial imbalance of over 16000 caucasian prisoners. The latter distribution is not representative of the racial breakdown of general prison population of the US.<sup>5</sup> 

![Age Distribution](images/2-16-19/AgeDist.svg)
![Racial Distribution](images/2-16-19/RaceDist.svg)

Prior to modeling, I broke the dataset down into handpicked subsets.  One of which dropped the "year released", "reporting year", and "target population" features. While modeling, this subset consistently outperformed the others.  The best performing models were logistic regression with a C of approximately 1.21, random forest classifer with a max depth of 8, and the naive-bayes bernouli classifier.  They all returned an auc_roc score around .65.  I adjusted the threshold to .4 to reduce false negatives, i.e. released persons the model predicted would not be rearrested but were.  False negatives are important since, when considering resource allocation, they represent ex-offenders who may have benefitted from more support.


Footnotes
<sup>1</sup>The official number from the Bureau of Justice Statistics is. 2,131,000 people incarcerated in prison or local jail as of 12/31/16.
<sup>2</sup> In 2014, the official number of released prisoners was 636,000: https://www.bjs.gov/content/pub/pdf/p14.pdf
<sup>3</sup>https://www.nij.gov/topics/corrections/recidivism/pages/welcome.aspx
<sup>4</sup>https://data.iowa.gov/Public-Safety/3-Year-Recidivism-for-Offenders-Released-from-Pris/mw8r-vqy4
<sup>5</sup>"In 2016, blacks represented 12% of the U.S. adult population but 33% of the sentenced prison population. Whites accounted for 64% of adults but 30% of prisoners. And while Hispanics represented 16% of the adult population, they accounted for 23% of inmates." (http://www.pewresearch.org/fact-tank/2018/01/12/shrinking-gap-between-number-of-blacks-and-whites-in-prison/)



