<!SLIDE center>

<center style="font-size:6em;">
Measure it, <br />
Don't Just Monitor It
</center>
![alt text](images/preso-front.svg)
<br />
Devopsdays Italy 2012, Bryan W. Berry

!SLIDE
# Ohai There

* I work at [UN Food and Agriculture Organization](http://www.fao.org)
on the [http://data.fao.org](http://data.fao.org) project
* Creator and co-host of the
  [Food Fight podcast](http://foodfightshow.org)
* You can reach me at bryan.berry@gmail.com or @bryanwb
<br /><br />
<div style="float:left;">
<img src="images/data-fao-org-logo-v8.png"></img> &nbsp; &nbsp;
<img src="images/foodfight_banner.png" width="250px" height="105px"></img>
</div>

!SLIDE
# more on data.fao.org

<img src="images/screenshot01.png" height="480px" width="500px"></img>

!SLIDE 
# Overview

* SOA is complicated
* Monitoring Helps
* But What does it all mean?
* Measure it, don't just monitor it
* Presentation matters

!SLIDE
# data.fao.org Architecture on Paper 

show image of architecture

!SLIDE
# data.fao.org Architecture in Reality

<center><img src="images/spaghetti-bolognese.jpg" height="800px" width="600px" /></center>

<center style="font-size:3em;">systematic monitoring is critical to
untangling it</center><br />

.notes http://dummyatcooking.files.wordpress.com/2007/10/spaghetti-bolognese.jpg

!SLIDE
# What We use for Monitoring

* Collectd (cpu, disk, network, arbitrary system data)
* JMXtrans to poll JMX data
* Logstash + statsd to gather stats from application logs
* Graphite
* Elasticsearch + Kibana


largely based on discussion in [foodfightshow episode 21](http://foodfightshow.org/2012/07/monitoring-for-n00bs-with-jason-dixon.html)

!SLIDE 
# Here is what it looks like
<center>
<img src="images/full_stack.svg"></img>
</center>

!SLIDE
# Let There Be Graphs!
<div style="float:left;">
<img src="images/185px-The_Yes_Guy.png"></img>
</div>
![moar graphs](images/moar_graphs.svg)


!SLIDE
# But what does it all mean?

![dazed and confused](images/confusing_graphs.svg)

.notes http://www.buzzlol.com/wp-content/uploads/2012/05/Confused-Dog-Is-Confused.jpg

!SLIDE
# Do you know What this means?

<img src="images/http_requests.png"></img>

!SLIDE
# How fast/slow is the site?

* How many Requests per Second? Per minute?
* Are those thousands of seconds or thousands of milliseconds?
* What is the average request latency?
* Is "average" what we really want to know?

