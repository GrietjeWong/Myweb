---
layout: post
title: "如何运用Tableau做敏感性分析"
date: 2016-12-20
categories:
  - DataAnalysis数据分析
description:
image: https://unsplash.it/2000/1200?image=1003
image-sm:
---
最近闲来无事，做了个小型的数据分析研究。数据来源于在职选修的一门课程，属于Capstone的一个研究课题。数据量不大，工具也很简单。个人感觉，要做好数据分析，更重要的是解决问题的思路，流畅的算法，对整体流程要有清晰的思路。<br/>
分析工具：EXCEL Solver, Tableau Dashboard

<h3>About the Case Study</h3><br/>
<h4>Background:</h4>
XXX Properties is a residential property management company. As Short-term Rentals like Airbnb are becoming more and more popular, some of its property owners want to term some long-term rental properties into short-term rentals. The task is to evaluate whether the conversions are necessary and profitable.

<h4>Methods:</h4>Excel to build models& Tableau to visualize data

<h4>Data Given by Relevant Stakeholders:</h4>
<ol>
<li>Tested data include 244 properties owned by the one client.</li>
<li>The occupancy rate of those 244 properties is 97.3% (or 36/37 months) when they are managed as long-term rentals.</li>
<li>The initial capital required to convert a long-term rental property to a short-term rental property is $30,000 (for furnishings, linens, etc.), which will depreciate over 5 years.</li>
<li>$6000 in cash will be needed for each property each year after the first (conversion) year to cover items that wear out quickly. This amount is treated as an expense and is not depreciated.</li>
<li>Utilities will be $300 a month for each property, or $3600 a year.</li>
<li>The hospitality fee (variable cost) for each visit (for key service, cleaning, etc.) will be $100, regardless of the actual number of days of a visit.</li>
<li>The average short-term stay is 3 nights.</li>
<li>All the properties have the same capital expenditure and fixed costs.</li>
<li>The total default transaction fee is 30%, including 10% for potential regulatory and legal fees and 20% for online short-term rental provider (like Airbnb).</li>
<li>All clients pay their rent on time.</li>
<li>Comparable Examples are short-term rental properties with same type and in the same locations.</li>
</ol>

<h4>Ignore the impact of any:</h4>
<ul>
  <li>weekly or seasonal changes in rent or occupancy rate.</li>
  <li>marketing strategies, like discounts or coupons.</li>
  <li>special events during the year that might affect the rentals in one specific location.</li>
  <li>loss in rent during the time interval when properties are being converted to short-term rental properties.</li>
</ul>


<h3>Data Cleansing Before Analyzing Them</h3>
Data put into Tableau, and Tableau Filter used to exclude outliers.

<h4>Raw Forecast Model</h4>
In my first model(the first best-fit line), I tried to find the correlation between short-term occupancy rate and rental price.

<figure>
  <img src="/img/1.png" alt=""/>
</figure>

<h4>Normalized Forecast Model</h4>
It seems that all the points are scattering around. It was hard to find the correlation. Hence in my second model(the normalized best-fit line), I was to minimize the differenced.I assumed that no rent can be set lower than 10th percentile or higher than 90th. Hence:<br/>Sample property Percentile rent = .1 + .8*[((sample rent) – (10th percentile [low] rent)) / ((90th percentile [high] rent) – (10th percentile [low] rent))].

<figure>
  <img src="/img/2.png" alt=""/>
</figure>

Base on the Excel Calculation, then I have:<br/>
Slope Beta = -0.7914<br/>
Y-Intercept Alpha = 0.8506<br/>
So that each maximized rental price of those 244 short-term properties can be calculated using "MS Solver".

<h4>Alternative to SOLVER</h4>
Calculating the best rental price one by one can be time-consuming. We want it to be efficient and can be applied to Tableau. The altanative way to calculate the maximized price can also be performed as:<br/>
 Nightly rent in $$ = [(Beta*((10th - ((90th – 10th)/8)))/(1.25*(90th – 10th)) – Alpha] *[(1.25*(90th – 10th))/(2*Beta)]
Base on that, calculations can be created via Tableau.

<h4>Financial Model in Tableau</h4>
I created some parameters(measurable variables) in Tableau, add some calculations, so that i have my dashboard like this:
<img src="/img/watershed.png" alt="">
It did took some time to generate the jittered map. But by changing the number in the box(parameters), it can me much easier for people to see whether the investment would be profitable.
