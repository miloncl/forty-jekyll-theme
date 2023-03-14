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
    <div class="row">
        <div class="6u$ 12u$(small)">
            <h3>Intel Software Development Kit</h3>
            <p> we have learned and written codes for the input libraries using Intel’s Software 
            Development Kit. These input libraries act as data collectors, which allow us to gather 
            information related to the system usage of a user. With data in our hands, we are able 
            to Data Science. In contrast, “Without Data, there is no (Data) Science” [18]. In addition,
            by knowing how to collect data, we have control over how we want our data to be and what 
            should be collected to improve the analysis.</p>
            <h3>Data Acquisition</h3>
            <p>During the data acquisition process, we need to ensure data quality (i.e. collecting the
            desired measurements that we claim we would collect), flexibility (i.e. considering how to 
            quickly adapt the collection process to unseen situations), and data privacy (i.e. protecting 
            the personally identifiable information of the users).</p>
            <h3>Exploratory Data Analysis</h3>
            <p>we input the data collected to conduct Exploratory Data Analysis. For EDA, we discover the 
            “Missing String.” problem and resolve it by imputation. Besides, we observe that Chrome is the
            top frequently used app among all applications that both users use. The major reason is that 
            Chrome allows users to visit other applications/websites quickly; for example, Messenger, Facebook,
            and Netflix. </p>
            <h3>Models + Results</h3>
            <p>Next, as perceived from the result section, our HMM models are working pretty well with some 
            accuracies that go beyond 90%. The accuracy is defined by the percentage of correct predicted 
            transition/emission probabilities. A prediction is deemed correct if it falls within the top n 
            (num_apps) probabilities predicted. As the value of n increases, we receive a higher accuracy.</p>
            <p>Additionally, we develop different experiments for our LSTM models. The prediction accuracies 
            are acceptable as they are all above 50% (the probability of a coin flip), which shows our models’ 
            functionality. Some can reach more than 90%, which seems to be an overfitting problem as we give 
            too much information to the model. We can further improve our models by (1) considering different 
            sets of hyperparameters when tuning our models and (2) re-adjusting our feature engineering process, 
            which allows us to input other types of features that we are able to extract from the data, and avoid
            the overfitting / underfitting problems.</p>
            <h3>Conclusions + Next Steps</h3>
            <p>In short, learning how to collect data and input them into different predictive models helps us 
            vastly in our journey of becoming Data Scientists. In fact, by understanding where the data comes 
            from and how the data are generated, we can recognize the informative and useful data features to 
            feed into our predictive models. This is also what makes us different from other Data Scientists 
            who have not known about data acquisition yet. On the other hand, by observing the results of predictive
            models, we can recognize what features should be collected; then we can come back, re-adjust the input 
            libraries, and generate new data with new features.</p>
            <p>In the future, we will continue collecting more data to improve the patterns that can be learned in
            our predictive models. By applying this data analysis pipeline, we can infer the sequence of application
            usage along with the time used. The analysis will assist us in developing the scripts that process background
            tasks and we can - for example - use the Scheduler to pre-launch the app 2-3 minutes beforehand. That is how 
            we can reduce the initial latency and better user experience. </p>
        </div>
    </div>
    </div>
</section>

</div>