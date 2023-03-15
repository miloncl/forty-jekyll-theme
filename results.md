---
title: Models & Results
layout: page
description:
image: assets/images/pic07.jpg
nav-menu: true
---

<!-- Main -->
<div id="main">

<!-- One -->
<section id="one">
	<div class="inner">
		<header class="major">
			<h2>Models & Results</h2>
		</header>

<h2 id="content">Hidden Markov Model</h2>
<p>Hidden Markov Model (HMM) is a statistical model to predict the next value based on the 
sequence of the previous states. It uses the Markov chain which is a sequence of possible 
events where the probability of each event only depends on the state attained in the previous 
event. <a href="zzreference.html">[13]</a> It also uses Output Independence which is the probability
of observing an event relies on the state that directly produced this event. <a href="zzreference.html">[14]</a>
 To be able to mimic this, we create a transition and emission matrix.
</p>
<div class="row">
	<div class="6u 12u$(small)">
		<h3>Transition Matrix</h3>
		<p>A transition matrix consists of the probabilities of going from one executable to another. For example the probability of the user going from <b><i>chrome.exe</i></b> to 
		<b><i>cmd.exe</i></b> can be calculated as shown below.</p>
		<span class="image fit">
		    <img src="/system-usage-analysis-website/assets/images/transition.png" alt="Transition" />
		</span>
	</div>
	<div class="6u$ 12u$(small)">
		<h3>Emission Matrix</h3>
		<p>An emission matrix consists of the probabilities of going from one executable to 
		another app or tab. For example the probability of the user going from <b><i>chrome.exe</i></b> to 
		<b><i>google docs</i></b> can be calculated as shown below.</p>
		<span class="image fit">
		    <img src="/system-usage-analysis-website/assets/images/emission.jpg" alt="Emission" />
        </span>
	</div>
</div>
<p></p>
<p>In this model, we first split the data into training and testing sets - each representing 80% 
and 20% of the entire dataset, respectively. We then input these data into our program that learns 
the Markov chain and creates a transition matrix as shown below. Once we train the data on our training set, we 
then run it on our test set and calculate the accuracy of the model. To calculate the accuracy, we 
decide if the prediction is considered accurate as long as the prediction falls in the top <b><i>n</i></b> 
probabilities for that application. As the value of <b><i>n</i></b> increases, the prediction accuracy increases 
as well.</p>

<span class="image center">
    <img src="/system-usage-analysis-website/assets/images/emmisionmatrix.png" alt="Emission Matrix" />
</span>

<h3>Results</h3>
<p>The accuracy of HMM models is calculated based on whether or not the prediction falls in the top <b><i>n</i></b> 
probabilities for that application. As the value of <b><i>n</i></b> (the number of applications) increases, the 
prediction accuracy increases as well. However, when reaching a particular value of <b><i>n</i></b> such as <b><i>n</i></b> = 10, 
the amount of accuracy increase starts to plateau and does not fluctuate much. Continuing to 
increment <b><i>n</i></b> won’t produce new interesting results or help us visualize the significant increase in 
the transition matrix’s accuracy. Thus, we conclude the optimal <b><i>n</i></b> should be <b><i>n</i></b> = 5 in our case.</p>

<span class="image center">
    <img src="/system-usage-analysis-website/assets/images/accuracyChart.png" alt="Accuracy" />
</span>

<hr class="major" />

<h2 id="content">Long Short-term Memory Model</h2>
<p>The Long Short-Term Memory (LSTM) model is a type of recurrent neural network (RNN) 
that is designed to overcome the vanishing gradient problem, which is a common issue with 
traditional RNNs. LSTMs are widely used in natural language processing, speech recognition, and image recognition tasks.</p>
<div class="row">
	<div class="4u 12u$(small)">
		<h3>Memory Cells</h3>
		<p>At the core of the LSTM model are memory cells, which can store information for a long 
            time. The model uses a combination of three gates - input, forget, and output gates - to 
            regulate the flow of information into and out of the memory cells. The input gate controls
            how much new information is added to the memory cells, the forget gate determines which information 
            is removed from the memory cells, and the output gate controls how much information is read from the
            memory cells.</p>
	</div>
	<div class="4u 12u$(small)">
		<h3>Cell State</h3>
		<p>The LSTM model also has a cell state that runs along with the memory cells. The cell state
            carries information across different time steps and can be modified through the use of the
            gates. The model's ability to selectively add or remove information from the memory cells 
            and cell state, as well as its ability to remember information over long periods of time, 
            makes it well-suited for handling sequential data.</p>
	</div>
	<div class="4u 12u$(small)">
		<h3>Training + Back Propagation</h3>
		<p>During the training process, the model learns to optimize the weights of the gates and memory
            cells through backpropagation, where the error from the output is propagated back through time.
            This allows the model to make more accurate predictions over time as it learns to capture the 
            patterns and relationships in the input data..</p>
	</div>
</div>
<p></p>
<p>Applying this model to our collected data proved to provide very powerful insights. Using the 
    collected data and some data manipulation, we are capable of tackling two prediction problems:
    <ol>
		    <b>
            <li>Predict the duration a user spends on an app <i>within an hour</i>, given the past time-series data.</li>
            <li>Predict the total amount of time a particular user spends using a particular app on any given <i>day</i>.</li>
            </b>
        </ol>
    Being able to predict this information greatly assists in the optimization of the user's interface
    overall and furthermore can assist in the overall goal of predicting the user's next used application.
</p>
<h3>Results</h3>
<p>After trying different models and feature engineering techniques, we conclude that the Bidirectional
 LSTM provides the best possible result for our first prediction problem. It can capture both the peaks and
  the low values of the time usage as shown in the figure below. In fact, the bidirectional characteristics allow the model to 
  learn in both forward and backward directions. <a href="zzreference.html">[17]</a></p>

<span class="image center">
    <img src="/system-usage-analysis-website/assets/images/biLSTM.png" alt="Bidirectional LSTM" />
</span>  
 
<p> As for the second prediciton problem. We use a different model consisting of the usage time used of each application
in a day split into each hour of the day, the total usage of that app during that day, and a value to differentiate
each application. Using this model, we make predictions on the total usage. The prediction values are 
    continuous in nature. Thus, to properly understand the accuracy of the model a binning process was conducted 
    based on thresholds that were determined through analysis of the distribution of the true and predicted values.
    The distribution of these values can be seen below. Through the binning process we were able to determine that the 
    model performs at about 70% accuracy.</p>
<span class="image center">
    <img src="/system-usage-analysis-website/assets/images/Screenshot 2023-03-12 at 9.52.40 AM.jpg" alt="Result Distribution" />
</span>
	</div>
</section>
</div>