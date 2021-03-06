!SLIDE
# I see spikes, but no trend

![spikes](hit_count_spikes.png)

!SLIDE 
# Smoothing 

Massage the Numbers to reveal the trend and to make useful forecasts

* Moving Average
* Moving Weighted Averages
* Holt-Winters

!SLIDE
# Let's Move that Average

![moving average](hit_count_moving_average.png)

<center style="font-size:3em;">
erm, a little better
</center>

!SLIDE
# Show me the Math!

<center style="font-size:3em;">
For value M at time t and N number of points, calculate the average
based on the last 10 points <br /><br />
<math xmlns='http://www.w3.org/1998/Math/MathML'>
<msub>M<mn>t</mn></msub> =
[ <msub>X<mn>t</mn></msub> + <msub>X<mn>t-1</mn></msub> + ... + <msub>X<mn>t-N+1</mn></msub>] / N
</math>

<br />
<br />
</center>

<center style="font-size:3em;">
Moving Averages are OK at reflecting trend, <br /> but  have no notion of
<em>seasonality</em>
</center>

!SLIDE
# Got Seasonality?

![more hw](graph-sum.png)

.notes http://blog.pkhamre.com/2012/07/05/visualizing-logdata-with-logstash-statsd-and-graphite/

!SLIDE
# Holt-Winters forecast

Let's Factor in:

* How smooth do we want the data to be, i.e. not spiky
* Trend
* Seasonality

!SLIDE
# Now with Seasoning!

![more hw](graph-holtWintersAverage.png)
<br />
Graph credit: Pal Kristian Hamre


.notes http://blog.pkhamre.com/2012/07/05/visualizing-logdata-with-logstash-statsd-and-graphite/

!SLIDE
# Show me the Math!

<center>
<img src="holt-winters-bigger.png"></img>
</center>

!SLIDE full-page
<center>
<img src="the-scream-bigger.jpg"></img>
</center>

!SLIDE
# Idiot's guide to Holt Winters

* 4 Equations
  * Overrall Smoothing
  * Trend Smoothing
  * Seasonal Smoothing
  * Actual Forecast
* 3 Constants
  * α - overrall
  * β - Trend
  * γ - Seasonality

.notes http://www.itl.nist.gov/div898/handbook/pmc/section4/pmc435.htm

!SLIDE
# Confidence Bands

![confidence bands](basic.png)
<br />
Graph credit: R.I. Pienaar

.notes https://github.com/ripienaar/graphite-graph-dsl/wiki/Creating-Holt-Winters-Forecasts

!SLIDE
# Aberration

![aberration](basic-with-aberration-on-y.png)
<br />
Graph credit: R.I. Pienaar

!SLIDE
# Great potential in Holt-Winters

* Intelligent capacity planning!
* More intelligent alerting
* Problems
  * Buggy implementation
  * Need to null outage data

!SLIDE full-page

<center>
<img src="deming-quality.jpeg.jpg"></img>
<br />
<div style="font-size:4em;">Deming Matters</div>

</center>



!SLIDE full-page

<br />
<center style="font-size:3em">
<img src="1000px-ControlChart.png"></img>
<br />
Deming invented the Control Chart <br />
100 years ago

</center>


!SLIDE
# Presentation matters

* Maximize Data-ink Ratio
* Maximize data density
* Use _words_ and colors (to a lesser extent) to add context to your graph

!SLIDE
# Edward Tufte, Data Visualization Guru

<center>
<img src="photo_tufte.jpeg"></img>
</center>

<center style="font-size:3em;">
"Graphics should do more than present the obvious to idiots"
</center>

!SLIDE
# More wisdom

<center>
<img src="photo_tufte.jpeg"></img>
</center>

<center style="font-size:3em;">
"The task of the designer is to give visual access to the subtle and
the difficult -- that is, the revelation of the complex"
</center>

!SLIDE
# Maximize Data-ink Ratio

Drop Unnecessary Grid lines 

<center>
<img src="no-grid-lines.png"></img>
</center>

Ah, much better!

!SLIDE
# Colors and Text can Illuminate

<center>
<img src="db_cpu_usage.png"></img>
</center>

!SLIDE
# More Interesting Graphite Functions

* scale
* removeAbovePercentile
* cumulative
* summarize
* hitCount
* . . . [and many more!](http://graphite.readthedocs.org/en/0.9.10/functions.html)!

!SLIDE 
# John Rauser - look at your data

<center>
<a href="http://www.youtube.com/watch?v=coNDCIMH8bk">
<img src="john_rauser.png"></img>
<br />
Keep your logs, ideally in elasticsearch
</a>
</center>

!SLIDE
# The Power of Chef

* I couldn't have put together this stack w/out Chef
* cookbooks online and available
  * [collectd](https://github.com/bryanwb/chef-jmxtrans)
  * [graphite](https://github.com/bryanwb/chef-graphite)
  * [logstash](https://github.com/bryanwb/chef-logstash)
  * [ruby-statsd](https://github.com/bryanwb/chef-ruby-statsd)
* Checkout [monigusto](http://www.youtube.com/embed/oHg5SJYRHA0)!

![chef](oc-chef-logo.png)

!SLIDE
# Further Resources

*  [Graphite Functions](http://graphite.readthedocs.org/en/0.9.10/functions.html)
*  [Holt-Winters Approach to Exponential Smoothing](http://faculty.wiu.edu/F-Dehkordi/DS-533/Lectures/Moving-average-methods.ppt)
by F. Dekhordi 
* [The Visual Display of Quantitative Information](http://www.edwardtufte.com/tufte/books_vdqi) by Edward Tufte
* [Pal Kristian Hamre's](http://blog.pkhamre.com) blog
* [Jason Dixon](http://obfuscurity.com/) of course
* Listen to the [FoodFightShow](http://foodfightshow.org) Podcast
   * [Monitoring for n00bs](http://traffic.libsyn.com/foodfight/ffs21_3.mp3)
   * [Monitoringsucks](http://traffic.libsyn.com/foodfight/ffs18_3.mp3)  


!SLIDE
# Special Thanks to

* Jason Dixon
* Chris Davis
* Pal Kristian Hamre
* Pete Fritchman
* Michael Leinartas

[This presentation](https://github.com/bryanwb/monitoring-measurement-preso)
is available on github in showoff format (html,css,etc.), and diagrams done in SVG

Copyright 2012, Bryan W. Berry License: CC-By 3.0
