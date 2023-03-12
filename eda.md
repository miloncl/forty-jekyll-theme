---
layout: page
title: EDA
description:
image: assets/images/pic11.jpg
nav-menu: true
---

<!-- Main -->
<div id="main" class="alt">

<!-- One -->
<section id="one">
	<div class="inner">
		<header class="major">
			<h1>Exploratory Data Analysis</h1>
		</header>
		
<p>The first step in EDA is to clean the data that we have collected. This step requires us to drop 
undesired columns and check for null values in each existing column. Upon looking further into the 
data that was collected, we discerned that the data from our Foreground-Window IL would be best 
suited for our prediction model. To understand the data collected, we look at the schema of the 
data that was collected as shown in the below figure.</p>

<p>We then made sure that each value of the data was of the correct data type. Further evaluating 
the data, we noticed there were instances where our data contained “Missing String.” in a few rows 
in relation to a few applications as shown in the figure below.</p>

<p> After our thorough investigation, we came to realize that this was because we were not saving 
the name of the window in Unicode, and therefore, special characters were not being recorded; 
instead, it was showing us the “Missing String.”  However, upon fixing this, there were still 
instances where the file explorer tab returned an empty string when it was accessed	as shown below.
</p>

<p>To keep everything consistent, we decided to impute both the “Missing String.” and the empty 
entries (related to the File Explorer) with empty strings. Imputation allowed these rows to be 
used without affecting the overall distribution of the data. Even though there were imputations 
implemented in our pre-processing step, they did not affect our data as we mainly worked with 
application names.</p>

<p>Next, we looked at the spread of the data and calculated the use time for each instance of 
the recorded data. We looked into the top 10 most used applications in terms of time spent on 
them and created a scatter plot to see if there were any outliers.</p>

<p>It can be seen that chrome.exe has two instances of time recorded that are about 20000 seconds. 
We did not consider this to be something wrong with the data, but rather it seemed to be aligned 
with a student’s usage of Chrome. We also draw bar charts to explore and summarize the trend of 
the user’s usage time across the top 5 used apps.</p>


<hr class="major" />

</div>
</section>

</div>