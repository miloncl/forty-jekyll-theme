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
		    <img src="{% link system-usage-analysis-website/assets/images/transition.png %}" alt="Transition" />
		</span>
	</div>
	<div class="6u$ 12u$(small)">
		<h3>Emission Matrix</h3>
		<p>An emission matrix consists of the probabilities of going from one executable file to 
		another app or tab. For example the probability of the user going from <b><i>chrome.exe</i></b> to 
		<b><i>google docs</i></b> can be calculated as shown below.</p>
		<span class="image fit">
		    <img src="{% link system-usage-analysis-website/assets/images/emission.jpg %}" alt="Emission" />
        </span>
	</div>
</div>

<hr class="major" />

</div>
</section>

</div>