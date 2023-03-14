---
layout: page
title: Conclusion
image: assets/images/pic10.jpg
nav-menu: true
---

<!-- Main -->
<div id="main">

<!-- One -->
<section id="one">
	<div class="inner">
		<header class="major">
			<h2>Conclusion</h2>
		</header>
    <p>As the two-quarter project comes to an end, we wish to recapitulate what we have learned over 
    the last six months</p>
    <p> We have learned and written codes for the input libraries using Intel’s Software 
    Development Kit. These input libraries act as data collectors, which allow us to gather 
    information related to the system usage of a user. With data in our hands, we are able 
    to Data Science. In contrast, “Without Data, there is no (Data) Science”. <a href="zzreference.html">[18]</a> In addition,
    by knowing how to collect data, we have control over how we want our data to be and what 
    should be collected to improve the analysis.</p>
    <p>As perceived from the result section, our HMM models are working pretty well with some 
    accuracies that go beyond 90%. The accuracy is defined by the percentage of correct predicted 
    transition/emission probabilities. A prediction is deemed correct if it falls within the top <b><i>n</i></b> 
    (number of apps) probabilities predicted. As the value of <b><i>n</i></b> increases, we receive a higher accuracy.</p>
    <p>Additionally, we develop different experiments for our LSTM models. The prediction accuracies 
    are acceptable as they are all above 50% (the probability of a coin flip), which shows our models’ 
    functionality. Some can reach more than 90%, which seems to be an overfitting problem as we give 
    too much information to the model.</p>
    <p>In short, learning how to collect data and input them into different predictive models helps us 
    vastly in our journey of becoming Data Scientists. In fact, by understanding where the data comes 
    from and how the data are generated, we can recognize the informative and useful data features to 
    feed into our predictive models. This is also what makes us different from other Data Scientists 
    who have not known about data acquisition yet. On the other hand, by observing the results of predictive
    models, we can recognize what features should be collected; then we can come back, re-adjust the input 
    libraries, and generate new data with new features.</p>
	<h2>Further Steps</h2>
	<p>We can further improve our models by (1) considering different sets of hyperparameters when 
    tuning our models and (2) re-adjusting our feature engineering process, which allows us to input 
    other types of features that we are able to extract from the data, and avoid the overfitting / 
    underfitting problems. In the future, we will continue collecting more data to improve the patterns that can be learned in
    our predictive models. By applying this data analysis pipeline, we can infer the sequence of application
    usage along with the time used. The analysis will assist us in developing the scripts that process background
    tasks and we can - for example - use the Scheduler to pre-launch the app 2-3 minutes beforehand. That is how 
    we can reduce the initial latency and better user experience.</p>
    </div>
</section>

</div>