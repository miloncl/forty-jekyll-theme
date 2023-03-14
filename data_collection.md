---
layout: page
title: Data Collection
image: assets/images/pic01.jpg
nav-menu: true
---

<!-- Main -->
<div id="main" class="alt">

<!-- One -->
<section id="one">
	<div class="inner">
		<header class="major">
			<h1>Data Collection</h1>
		</header>

<h2 id="content">Overview</h2>
<p>During the first 10 weeks, we constantly wrote code to record different kinds of data from our 
individual desktops in relation to our system usage data. To accomplish this, we first familiarized 
ourselves with the Intel® System Usage Report (SUR), a data-collection and analysis framework that 
enables us to anonymously gather data usage from each device and analyze such data from multiple 
devices. <a href="zzreference.html">[5]</a> Accompanying the Intel® SUR collector, the ESRV (environment server) toolchain was 
also introduced and got set up on the machine on which we collected the data. We then studied the 
XLSDK User Guide to develop various input libraries (ILs) such as: 
</p>
<div class="row">
	<!-- Break -->
	<div class="4u 12u$(medium)">
		<h3> </h3>
		<p> </p>
	</div>
	<div class="4u 12u$(medium)">
		<ul>
		    <b>
            <li>Mouse-Input IL</li>
            <li>User-Wait IL</li>
            <li>Mouse-Hook IL</li>
            <li>Foreground Window IL</li>
            <li>Desktop Mapper IL</li>
            </b>
        </ul>
    </div>
	<div class="4u$ 12u$(medium)">
		<h3> </h3>
		<p> </p>
	</div>
</div>
<p></p>
<p>In general, each one of these input libraries extracts data alongside the timestamps, and we will 
further explain these input libraries as well as their functions in the below section.</p>


<h2 id="content">Mouse-Input IL</h2>
<p> The Mouse-Input IL was used to familiarize ourselves with the Windows machine and help us delve 
into understanding ESRV plus SUR using XLSDK. We incorporated static_standard_input sample template 
and step by step instructions provided by the Intel team to build this input library. The main 
purpose of Mouse-Input IL is to capture the mouse (X, Y) positions in pixels, with or without noise. 
<a href="zzreference.html">[11]</a> We control the intervals in which we collect the data. Furthermore, we update the Mouse-Input 
to also track the noise in the X and Y positions by applying a 1D Kalman predictor per dimension.
</p>

<span class="image fit">
    <img src="/system-usage-analysis-website/assets/images/mouseInputSample.png" alt="Mouse Data Sample" />
</span>

<p>In the above sample <b>Mouse(0)</b> and <b>Mouse(1)</b> are the X and Y position of the mouse in 
pixels. <b>Mouse(2)</b> and <b>Mouse(3)</b> are the noisy X and Y position of the mouse in pixels. 
<b>Mouse(4)</b> and <b>Mouse(5)</b> are the X and Y Kalman predicted positions in pixels. Using the 
data collected we can create scatter plots. Below is two sample scatter plots of the mouse movements 
when captured at a frequency of 1 Hz (left) and 100 Hz (right) 
</p>

<span class="image fit">
    <img src="/system-usage-analysis-website/assets/images/mouseInputScatterplot.png" alt="Mouse Data Scatterplot" />
</span>

<h2 id="content">User-Wait IL</h2>
<p>The User-Wait is the next input library we implemented. The User-Wait IL is used to retrieve 
the cursor type and its timestamp. We had to build a collector thread that monitored the state 
of the cursor icon during intervals. Once again, the span of these intervals can be controlled 
by us, which allows adjustment in the amount of data collected. The collected data – which 
describes the cursor – can vary from a standard arrow to an arrow with a spinning wheel. We also 
collected data using this input library on whether the mouse is static or dynamic. A few examples of 
the loading icons that our IL records is seen below.</p>

<span class="image center">
    <img src="/system-usage-analysis-website/assets/images/userWaitLoadingIcons.png" alt="Loading Icons" />
</span>


<h2 id="content">Mouse-Hook IL</h2>
<p>The general purpose of this input library is to use a system hook that can track the UI objects 
clicked by the mouse. Whenever we use the mouse, it generates a message, and the hook will notify 
the operating system about this information. Some inputs that we collect from the mouse hook 
are the X, and Y positions in pixels, the clicked UI object’s name, ID, root ID, class name, style, 
extended style, and the clicked UI object’s owning process image. We incorporate this IL in the 
Foreground Window IL.</p>


<h2 id="content">Foreground Window IL</h2>
<p>We use the Foreground Window input library to extract and log the application's name that sits 
the furthest up front, along with its position, size, and other information. We implemented two 
events as triggers for this input library; they are the mouse click and the time tick. We detect 
a change in the foreground window using the mouse click, and we use the time tick in cases where 
there is no mouse click, but there exists a change to the foreground window, such as when using 
the task manager. While collecting the data, we make sure that no private information about the user
is being recorded. We collect the module name (.exe), the window's class name while making sure we 
don't collect the path information to keep the privacy of the user. In addition, the window 
rectangle’s dimensions are recorded by retrieving the X, and Y coordinates on the upper-left and 
lower-right corners using the API named GetWindowRect() and the object type RECT (which is short 
for “rectangle”). Lastly, we can verify if the window app is immersive and is hung or not by using 
IsImmersiveProcess() and IsHungAppWindow() functions. In particular, “is_immersive” checks if the 
application is a Window Store application, and we capture “is_hung”, which checks if the 
application is responsive or not. An example of the data collected and the schema of the input library
is shown below.</p>

<div class="row">
	<div class="6u 12u$(small)">
		<span class="image fit">
            <img src="/system-usage-analysis-website/assets/images/foregroundExample.png" alt="Top Used Apps" />
        </span>
	</div>
	<div class="6u$ 12u$(small)">
		<span class="image fit">
            <img src="/system-usage-analysis-website/assets/images/foregroundSchema.png" alt="Top Used Apps" />
        </span>
	</div>
</div>
<p></p>


<h2 id="content">Desktop Mapper</h2>
<p>This input library when triggered, maps all the open application windows in z-order and stores 
information about each one of them, such as their position on the screen and their individual sizes 
as well. More specifically, the z-order “shows a window's position when given a list of overlapping 
windows. The z-axis points outward from the screen, where the top window of the z-order overlaps all 
other windows, and the bottom window is overlapped by all other windows on the z-order axis. 
Additionally, just like the Foreground Window IL, we capture if the window “is_immersive” and 
“is_hung”.</p>

<span class="image center">
    <img src="/system-usage-analysis-website/assets/images/zOrder.png" alt="Top Used Apps" />
</span>

<hr class="major" />

<p>The data collected from these ILs are crucial factors in keeping track of user-app interactions, 
with specific records of the mouse locations, changes in the user interface, as well as user 
activities. Consequently, we will be able to understand the overall patterns of using the Windows 
machine of a user; then, we can predict when a user opens an app, make comparisons and understand 
which apps take the longest time to launch, and make precise predictions in app launching time.</p>

</div>
</section>

</div>
