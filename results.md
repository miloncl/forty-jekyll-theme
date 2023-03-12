---
title: Model & Results
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
event. [13] To be able to mimic this, we create a transition and emission matrix.
</p>
<div class="row">
	<div class="6u 12u$(small)">
		<h3>Transition Matrix</h3>
		<p>A transition matrix consists of the probabilities of going from one executable file 
		to another. For example the probability of the user going from <b><i>chrome.exe</i></b> to 
		<b><i>cmd.exe</i></b> can be calculated as shown below.</p>
		<span class="image fit">
		    <img src="/system-usage-analysis-website/assets/images/transition.png" alt="Transition" />
		</span>
	</div>
	<div class="6u$ 12u$(small)">
		<h3>Emission Matrix</h3>
		<p>An emission matrix consists of the probabilities of going from one executable file to 
		another app or tab. For example the probability of the user going from <b><i>chrome.exe</i></b> to 
		<b><i>google docs</i></b> can be calculated as shown below.</p>
		<span class="image fit">
		    <img src="/system-usage-analysis-website/assets/images/emission.jpg" alt="Emission" />
        </span>
	</div>
</div>

<h2 id="content">Long Short-term Memory Model</h2>
<p>The Long Short-Term Memory (LSTM) model is a type of recurrent neural network (RNN) 
that is designed to overcome the vanishing gradient problem, which is a common issue with 
traditional RNNs. LSTMs are widely used in natural language processing, speech recognition, and image recognition tasks.</p>
<div class="row">
	<div class="6u 12u$(small)">
		<h3>Memory Cells</h3>
		<p>At the core of the LSTM model are memory cells, which can store information for a long 
            time. The model uses a combination of three gates - input, forget, and output gates - to 
            regulate the flow of information into and out of the memory cells. The input gate controls
            how much new information is added to the memory cells, the forget gate determines which information 
            is removed from the memory cells, and the output gate controls how much information is read from the
            memory cells.</p>
	</div>
	<div class="6u$ 12u$(small)">
		<h3>Cell State</h3>
		<p>The LSTM model also has a cell state that runs along with the memory cells. The cell state
            carries information across different time steps and can be modified through the use of the
            gates. The model's ability to selectively add or remove information from the memory cells 
            and cell state, as well as its ability to remember information over long periods of time, 
            makes it well-suited for handling sequential data.</p>
	</div>
	<div class="6u$ 12u$(small)">
		<h3>Training + Back Propagation</h3>
		<p>During the training process, the model learns to optimize the weights of the gates and memory
            cells through backpropagation, where the error from the output is propagated back through time.
            This allows the model to make more accurate predictions over time as it learns to capture the 
            patterns and relationships in the input data..</p>
	</div>
	<div class="6u$ 12u$(small)">
		<h3>Implementation</h3>
		<p>Applying this model to our collected data proved to provide very powerful insights. Using the 
            collected data and some data manipulation, we are capable of providing predictions regarding
            the total amount of time a particular user spends using a particular process on any given day.
            Being able to predict this information greatly assists in the optimization of the user's interface
            overall and furthermore can assist in the overall goal of predicting the user's next used application.
        </p>
        <h4>Input Matrix</h4>
        <p>The input matrix used to predict the total time a user spends on a given application on a given day looks 
            similar to this:</p>
		<span class="image fit">
		    <img src="/system-usage-analysis-website/assets/images/Screenshot 2023-03-12 at 8.13.42 AM.jpg" alt="Input Matrix" />
        </span>
        <p>Where each record of the input matrix refers to an application on a particular day. The columns 0 - 23 
            each refer to the usage of the application in that given hour. The Application column is the numeric 
            identifier for the process being used and the Total_Usage column is the total time the user spent using
            the given process on that particular day. The Total_Usage column will serve as the true value column for 
            the model.</p>
        <h4>Model Setup</h4>
        <p>The neural net we chose to utilize to produce insights from the input matrix looks like the following:</p>
		<span class="image fit">
		    <img src="/system-usage-analysis-website/assets/images/Screenshot 2023-03-12 at 8.40.42 AM.jpg" alt="Model Structure" />
        </span>
        <h4>Results</h4>
        <p>Using the above model, predictions can be made regarding the Total_Usage column. the prediction values are 
            continuous in nature thus to properly understand the accuracy of the model a binning process was conducted 
            based on thresholds that were determined through analysis of the distribution of the true and predicted values.
            The distribution of these values can be seen below. Through the binning process we were able to determine that the 
            model performs at about 70% accuracy</p>
        <span class="image fit">
		    <img src="/system-usage-analysis-website/assets/images/Screenshot 2023-03-12 at 9.52.40 AM.jpg" alt="Result Distribution" />
        </span>
	</div>
</div>

</div>
</section>

<!-- Two -->
<section id="two" class="spotlights">
	<section>
		<a href="generic.html" class="image">
			<img src="{% link assets/images/pic08.jpg %}" alt="" data-position="center center" />
		</a>
		<div class="content">
			<div class="inner">
				<header class="major">
					<h3>Orci maecenas</h3>
				</header>
				<p>Nullam et orci eu lorem consequat tincidunt vivamus et sagittis magna sed nunc rhoncus condimentum sem. In efficitur ligula tate urna. Maecenas massa sed magna lacinia magna pellentesque lorem ipsum dolor. Nullam et orci eu lorem consequat tincidunt. Vivamus et sagittis tempus.</p>
				<ul class="actions">
					<li><a href="generic.html" class="button">Learn more</a></li>
				</ul>
			</div>
		</div>
	</section>
	<section>
		<a href="generic.html" class="image">
			<img src="{% link assets/images/pic09.jpg %}" alt="" data-position="top center" />
		</a>
		<div class="content">
			<div class="inner">
				<header class="major">
					<h3>Rhoncus magna</h3>
				</header>
				<p>Nullam et orci eu lorem consequat tincidunt vivamus et sagittis magna sed nunc rhoncus condimentum sem. In efficitur ligula tate urna. Maecenas massa sed magna lacinia magna pellentesque lorem ipsum dolor. Nullam et orci eu lorem consequat tincidunt. Vivamus et sagittis tempus.</p>
				<ul class="actions">
					<li><a href="generic.html" class="button">Learn more</a></li>
				</ul>
			</div>
		</div>
	</section>
	<section>
		<a href="generic.html" class="image">
			<img src="{% link assets/images/pic10.jpg %}" alt="" data-position="25% 25%" />
		</a>
		<div class="content">
			<div class="inner">
				<header class="major">
					<h3>Sed nunc ligula</h3>
				</header>
				<p>Nullam et orci eu lorem consequat tincidunt vivamus et sagittis magna sed nunc rhoncus condimentum sem. In efficitur ligula tate urna. Maecenas massa sed magna lacinia magna pellentesque lorem ipsum dolor. Nullam et orci eu lorem consequat tincidunt. Vivamus et sagittis tempus.</p>
				<ul class="actions">
					<li><a href="generic.html" class="button">Learn more</a></li>
				</ul>
			</div>
		</div>
	</section>
</section>

<!-- Three -->
<section id="three">
	<div class="inner">
		<header class="major">
			<h2>Massa libero</h2>
		</header>
		<p>Nullam et orci eu lorem consequat tincidunt vivamus et sagittis libero. Mauris aliquet magna magna sed nunc rhoncus pharetra. Pellentesque condimentum sem. In efficitur ligula tate urna. Maecenas laoreet massa vel lacinia pellentesque lorem ipsum dolor. Nullam et orci eu lorem consequat tincidunt. Vivamus et sagittis libero. Mauris aliquet magna magna sed nunc rhoncus amet pharetra et feugiat tempus.</p>
		<ul class="actions">
			<li><a href="generic.html" class="button next">Get Started</a></li>
		</ul>
	</div>
</section>

</div>
