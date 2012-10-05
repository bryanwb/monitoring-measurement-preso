<!SLIDE center>

<center style="font-size:6em;">
Measure it, <br />
Don't Just Monitor It
</center>
![alt text](preso-front1.png)
<br />
Devopsdays Italy 2012, Bryan W. Berry

!SLIDE
# Ohai There

* I work at [UN Food and Agriculture Organization](http://www.fao.org)
on the [http://data.fao.org](http://data.fao.org) project
* Creator and co-host of the
  [Food Fight podcast](http://foodfightshow.org)
* You can reach me at bryan.berry@gmail.com or @bryanwb
* I am a novice at statistics, graphs, and monitoring
<br /><br />
<div style="float:left;">
<img src="data-fao-org-logo-v8-bigger.png"></img> &nbsp; &nbsp;
<img src="foodfight_banner.png" width="250px" height="105px"></img>
</div>

!SLIDE
# more on data.fao.org

<img src="screenshot01.png" height="480px" width="500px"></img>

!SLIDE 
# Overview

* SOA is complicated
* Monitoring Helps
* But What does it all mean?
* Measure it, don't just monitor it
* Presentation matters

!SLIDE
# data.fao.org Architecture on Paper 

<center>
<img src="data_fao_org_arch.jpg"></img>
</center>

!SLIDE full-page

<center><img src="spaghetti-bolognese.jpg" height="800px" width="600px" /></center>

<center style="font-size:3em;">The Reality</center><br />

.notes http://dummyatcooking.files.wordpress.com/2007/10/spaghetti-bolognese.jpg

!SLIDE
# What We use for Monitoring

* Collectd (cpu, disk, network, arbitrary system data)
* JMXtrans to poll JMX data
* Logstash + statsd awesome combination
* Graphite
* Elasticsearch + Kibana


largely based on discussion in [foodfightshow episode 21](http://foodfightshow.org/2012/07/monitoring-for-n00bs-with-jason-dixon.html)

!SLIDE 
# Here is what it looks like
<center>
<img src="full_stack.png"></img>
</center>

!SLIDE
# Let There Be Graphs!
<div style="float:left;">
<img src="185px-The_Yes_Guy.png"></img>
</div>
![moar graphs](moar_graphs.png)

!SLIDE full-page
<center>
<img src="confusing_graphs.png"></img>
</center>

.notes http://www.buzzlol.com/wp-content/uploads/2012/05/Confused-Dog-Is-Confused.jpg

!SLIDE
# Do you know What this means?

<img src="request_latency-svg.png"></img>

Just collecting the data isn't enough

!SLIDE
# How fast/slow is the site?

* How many Requests per Second? Per minute?
* Are those thousands of seconds or thousands of milliseconds?
* What is the average request latency?
* Is "average" what we really want to know?

