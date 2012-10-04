!SLIDE
# Back to Basics, what is a metric?

* a bucket
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
# Metric Types for Collectd

* Gauges
* Derive 
* Counters
* Absolute

Gauges are the most commonly used metric type

![counters](counters.png)


!SLIDE
# Metric Types for Statsd

* Gauges
* Counters*
* Timers
<br /><br />
Counters* different than counters in collectd

![counters](counters.png)

!SLIDE
# Really Basic

![basic transport](sending_metrics.png)

!SLIDE
# collectd in action

![collectd](collectd-monitoring.png)

!SLIDE
# statsd in action 

![statsd](statsd.png)

!SLIDE
# Gauges

<center style="font-size:4em;">
A gauge simply indicates <br />
an arbitrary value at a point <br />
in time and is the <br />
simplest type in StatsD and collectd
</center>

<img src="DigitaLink_Tachometer.png" height="140px" width="200px"></img>

.notes http://blog.pkhamre.com/2012/07/24/understanding-statsd-and-graphite/

!SLIDE
# Derive metric type (collectd only)

* Computes the delta of an underlying counter for a period of time
* Very useful for measuring network traffic

<center style="font-size:3em;">
<math xmlns='http://www.w3.org/1998/Math/MathML'>
 value = <mfrac>
     <mrow>
         <msub><mi>value</mi><mn>new</mn></msub>
             <mo>-</mo>
         <msub><mi>value</mi><mn>old</mn></msub>
     </mrow>
     <mrow>
         <msub><mi>time</mi><mn>new</mn></msub>
             <mo>-</mo>
         <msub><mi>time</mi><mn>old</mn></msub>
     </mrow>
 </mfrac>
</math>
</center>


!SLIDE
# Counters (statsd)

* A counter adds a value to a bucket and stays in memory until the
  flush interval
* it sends two numbers for each bucket, a total count for the flush
  interval and a value per second
  
 ![counter](counter.png)

.notes http://blog.pkhamre.com/2012/07/24/understanding-statsd-and-graphite/

!SLIDE
# Statsd Timers

* Collect series of values
  * raw count
  * lower - minimum value for flush interval
  * mean
  * upper - maximum value for flush interval
  * 90th percentile, value at 90th percentile
  
![timer](timer.png)

!SLIDE
# Let's take a look that JVM

![jmxtrans](jmxtrans.png)

!SLIDE
# JMXtrans 

* JMXTrans polls each JVM each 60 seconds, by default
* As far as I can tell, values returned from a JMX query are Gauges

!SLIDE
# Let's look at that graph again

<img src="request_latency.png"></img>

That's horrible!

!SLIDE
# Means are Nasty, dirty things

* Let's look at that 90th Percentile

<img src="request_90th.png"></img>

!SLIDE
# Let's remove the 90th Percentile

<img src="filtered_mean.png"></img>

!SLIDE
# learn it Love it

* removeAbovePercentile, along with other filtering functions, is
freaking awesome
* other filtering functions
  * removeAboveValue
  * removeBelowPercentile
  * removeBelowValue
  * mostDeviant
  
The average isn't all it's cracked up to be

* These functions are broken in Graphite 0.9.10 but fixed in master

!SLIDE
# Show me the worst!

<img src="most_deviant.png"></img>



!SLIDE
# Measure it

* Know your data
* Filter out distorting data
* Smooth the Savage Graph to reveal trends
* Maximize the power of Graphite

