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

![counters](counters.svg)


!SLIDE
# Metric Types for Statsd

* Gauges
* Counters*
* Timers
<br /><br />
Counters* different than counters in collectd

![counters](counters.svg)

!SLIDE
# Really Basic

![basic transport](sending_metrics.svg)

!SLIDE
# collectd in action

![collectd](collectd-monitoring.svg)

!SLIDE
# statsd in action 

![statsd](statsd.svg)

!SLIDE
# Gauges

!SLIDE
# Derive metric type (collectd only)


!SLIDE
# Counters (statsd)


!SLIDE
# Gauges


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


