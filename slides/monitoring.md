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
# Collectd for system metrics
<center>
<img src="images/collectd-monitoring.svg"></img>
</center>


!SLIDE
# Collectd is good

* lightweight C daemon
* monitors continuously, not once every 5 minutes
* Best for OS-level metrics such as CPU, Disk, Memory, etc. 

!SLIDE
# What's Graphite?

* Time Series Database (Whisper)
* Rendering Engine 
* Dashboard (Graphite-Web)
* data relay and aggregation (Carbon)
<br />

!SLIDE
# What is a metric?

* a name
* a value
* a timestamp, typically the UNIX epoch time
<br />

<center  style="font-size:2em;">
stats.haproxy.data_fao_org.request_duration  <span style="color:blue;">330</span>  74857843</center>
<br />
<br />
<center style="font-size:2em;">
&lt;stat_name&gt; &lt;number&gt; &lt;timestamp&gt; 
</center>
<br />

<br />


!SLIDE
# JMXTrans

* Is just a connector for transporting JMX data
* No agent involved

!SLIDE
# What about those logs?

<img style="float:right;" src="image/images/logstash.png"></img>

<center  style="font-size:3em;">We don't only care about metrics, we also care about important
events<br /><br /> Scraping metrics from logs would be nice</center>

!SLIDE
# Show me the graphic already!

![logstash](images/logstash.svg)

!SLIDE
# Logstash can more than just ship logs

* Win
  * index by field
  * shape data
  * add new fields and tags to entries
  * Elasticsearch backend is awwwes0me

* Con - The agent is not light on resource usage

!SLIDE
# Logs don't have to be Ugly

![logstash](images/basic-kibana.png)

!SLIDE
# We can filter the data

![logstash](images/kibana-select-fields.png)

!SLIDE
# UNIX Tail in your browser

![logstash](images/kibana-tail.png)

!SLIDE
# Elasticsearch Rocks

* We can use [Lucene Parser
  Syntax](https://lucene.apache.org/core/old_versioned_docs/versions/3_5_0/queryparsersyntax.html)
  to construct queries
* Watch out though, don't use quotes, the 1st example here works, the
  second doesn't
<br />
<div style="font-size:2em;"><em>> status_code:40* AND request_header_host:*fao_org</em></div>
<br />
<br />
<div  style="font-size:2em;"><em>> status_code:"40*" AND request_header_host:"*fao_org"</em></div>

!SLIDE
# But this is not really enough

<br />
<br />
<center style="font-size:4em;"> Ideally, your application should be
instrumented from the inside
<br />
<br />
No one knows your code better than you
</center>

!SLIDE
# Use the Force, Luke

<br />
<br />
<img style="float:right;" src="image/images/luke_skywalker.jpg"></img>
<br />
<br />
<center style="font-size:4em;">Use Statsd</center>

.notes http://www.alexandgregory.com/images/luke%20skywalker.jpg

!SLIDE
# Show me a graphic     

![Statsd](images/statsd.svg)

!SLIDE
# Enter Statsd

* a small local daemon that your application send metrics to over UDP     
* has virtually no overhead
* I use [Pete Fritchman's Ruby implementation](https://github.com/fetep/ruby-statsd)
* Statsd ships the metrics it receives to graphite
* Types of metrics
  * gauges
  * timers
  * counters

!SLIDE
# So about the code


<center style="font-size:2em;">Here is some sample java code</center>

![java-client](images/java-client.png)

!SLIDE
# Metrics, Metrics Everywhere

<img src="images/metrics-hat-full.png"  height="300px"
width="250px" style="float:right;"></img>
Coda Hale gave an [excellent talk](http://pivotallabs.com/talks/139-metrics-metrics-everywhere) about how his team at yammer
uses metrics
<br /><br />
He also created an excellent [java library](http://metrics.codahale.com/) that you can use together
with statsd

!SLIDE
# Now, Graphite Demo

<img src="images/graphite-graph-example.png"  height="500px"
width="800px" ></img>

.notes show how to display request_duration across multiple sub_domains

!SLIDE

# You will get for free

* System-level monitoring with collectd
* JMX monitoring w/ JMXtrans
* log aggregation on request via logstash+elasticsearch+kibana
* All those data points in graphite

<br />
<center style="font-size:4em;">But if you are serious about
performance . . .</center>

!SLIDE
# . . . You will

<img src="images/serious_cat.jpg" style="float:right;"></img>

* instrument your code with the statsd java client or Coda
  Hale's metrics library
* Create custom graphs in graphite
* Solve performance problems the way real engineers do, with _data_

!SLIDE
# Questions?

<center style="font-size:4em;">Ask away</center>

!SLIDE
# The Full Stack

![Full stack](images/full_stack.svg)

!SLIDE
# Further Resources

* [Logstash](http://logstash.net)
* [Collectd](http://collectd.org)
* [statsd](https://github.com/etsy/statsd) and Pete Fritchman's [ruby-statsd](https://github.com/fetep/ruby-statsd)
* [graphite](http://graphite.wikidot.org)
* Coda Hale's [excellent talk](http://pivotallabs.com/talks/139-metrics-metrics-everywhere)
and library [java library](http://metrics.codahale.com/)
* Be sure to listen to the FoodFightShow! 
   * [Monitoring for n00bs](http://traffic.libsyn.com/foodfight/ffs21_3.mp3)
   * [Monitoringsucks](http://traffic.libsyn.com/foodfight/ffs18_3.mp3)  

<img src="images/foodfight_banner.png" width="500px" height="210px"></img>


