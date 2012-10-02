!SLIDE


<br />
<br />
<br />
<center style="font-size:6em;">
Measure, Don't Just Monitor<br /><br />

image of measure tap plus graph ?
</center>

.notes http://www.ironicsans.com/images/anewhope.png

!SLIDE
# Ohai!

I am Bryan W. Berry

* I am in charge of infrastructure operations for
[http://data.fao.org](http://data.fao.org), and I am the co-host of
the [FoodFightShow](http://foodfightshow.org) the bi-weekly Chef
community podcast
* [UN Food and Agriculture Organization](http://data.fao.org) is a UN
agency base here in Rome. 
image of FAO logo
<br />
You can reach me at bryan.berry@gmail.com

!SLIDE
# Overview

* SOA is complicated
* Monitoring Helps
* But What does it all mean?
* Measure it, don't just monitor it

!SLIDE
# data.fao.org Architecture on Paper 

show image of architecture

!SLIDE
# data.fao.org Architecture in Reality

<center style="font-size:4em;">systematic monitoring is critical to
untangling it</center><br />


<center><img src="images/spaghetti-bolognese.jpg" height="400px" width="600px" /></center>

.notes http://dummyatcooking.files.wordpress.com/2007/10/spaghetti-bolognese.jpg

!SLIDE
# What We use for Monitoring

* Collectd (cpu, disk, network, arbitrary system data)
* JMXtrans to poll JMX data
* Logstash + statsd to gather stats from application logs
* Graphite
* Elasticsearch + Kibana


largely based on [foodfightshow episode 21](http://foodfightshow.org/2012/07/monitoring-for-n00bs-with-jason-dixon.html)

!SLIDE 
# Here is what it looks like
<center>
<img src="images/full_stack.svg"></img>
</center>

!SLIDE
# Let There Be Graphs!

!SLIDE
# But what does it all mean?


!SLIDE
# Do you know What this means?



!SLIDE
# Back to Basics, what is a metric?

* a bucket name
* a value
* a timestamp, typically the UNIX epoch time
<br />

<center  style="font-size:2em;">
bucket.name  <span style="color:blue;">number</span>  TIMESTAMP</center>
<br />
<br />
<center style="font-size:2em;">
&lt;stat_name&gt; &lt;number&gt; &lt;timestamp&gt; 
</center>
<br />

<br />

!SLIDE
# More complex values

* Gauges
* Counters
* Timers

!SLIDE
# Gauges

!SLIDE
# Counters

!SLIDE
# Timers


!SLIDE
# How Statsd does it


!SLIDE
# How Collectd does it

!SLIDE
# How JMX does it

!SLIDE
# Let's look at that graph again

explain request latency

!SLIDE
# Presentation Matters

* Filter out distorting values, or find them (MostDeviant, removeAbovePercentile)
* Check performance after change (timeshift)
* Understand a trend better by smoothing it (smoothing w/ moving averages, holt-winters)


!SLIDE
# Let's See the Average disk latency

!SLIDE
# Compare it w/ last week

timeshift

!SLIDE 
# Let's look at request latency

esb

!SLIDE
# Filter out Worst cases

!SLIDE
# Show me the n worst cases!

!SLIDE
# What's the usage trend?

smoothing

moving averages

!SLIDE
# moving average


!SLIDE
# Holt Winters forecast

!SLIDE
# Confidence Bands

!SLIDE
# Let's Get Funky

holt-winters aberration and a 2nd y-axis

!SLIDE
# How confident are you?

!SLIDE
# More Interesting Graphite Functions

* scale
* removeAbovePercentile
* cumulative
* hitCount
* . . . [and more](http://graphite.readthedocs.org/en/0.9.10/functions.html)!

!SLIDE
# Questions?

<center style="font-size:4em;">Ask away</center>

!SLIDE
# Further Resources

*  [Graphite Functions](http://graphite.readthedocs.org/en/0.9.10/functions.html)
*  [Holt-Winters Approach to Exponential Smoothing](http://forecasters.org/pdfs/foresight/free/Issue19_goodwin.pdf) by Paul Goodwin 
* [Pal Kristian Hamre's](http://blog.pkhamre.com) excellent blog
* [Jason Dixon](http://obfuscurity.com/) of course
* My Chef recipes for collectd, statsd, logstash, and jmxtrans
* Be sure to listen to the [FoodFightShow](http://foodfightshow.org) http://foodfightshow.org
   * [Monitoring for n00bs](http://traffic.libsyn.com/foodfight/ffs21_3.mp3)
   * [Monitoringsucks](http://traffic.libsyn.com/foodfight/ffs18_3.mp3)  

<img src="images/foodfight_banner.png" width="500px" height="210px"></img>

!SLIDE
# Special Thanks to

* Jason Dixon
* Pal Kristian Hamre
* Pete Fritchman
* Matt Leinartas

