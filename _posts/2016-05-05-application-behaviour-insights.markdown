---
layout: post
title:  "Optimising our APIs"
date:   2016-05-05 21:59:09 +0100
categories: data analytics performance
---

Whilst we track a number of logs across our entire estate of servers (data centers and appliances) we selectively monitor a number of our schools for specific performance data against our API's.  For each API call we log data about SQL utilisation (how many, how long), CPU and memory, this example demonstrates data we collect in our PHP layers.  This provides us valuable insights about how our application behaves and pointers for continued improvements.

For Example:

{% highlight javascript %}
{"server":"SCHOOL_NAME","url":"/api/2/?method=feedback.getFeedback",
"dur":0.1775860786438,"ram":24641536,"timestamp":1462419744,"sqlraw":0,
"sqlrawdur":0,"sqlins":0,"sqlinsdur":0,"sqlsel":28,
"sqlseldur":0.009455680847168,"sqlcou":0,"sqlcoudur":0,"sqlupd":0,
"sqlupddur":0,"sqldel":0,"sqldeldur":0,"sqltru":0,"sqltrudur":0,
"cpuuser":0.635754,"cpusys":0.012998,"curl":0}
{% endhighlight %}

This data is collected, stored and processed using the <a href="https://www.elastic.co">ELK stack</a> (more on that in another post).

We can use this information to highlight general peaks/troughs in the estate and narrow down on particular API that may be exhibiting undesirable behaviors

<img src="{{ site.baseurl }}/assets/elk-example.png">

Or we can narrow down on specific pain points, in this example we see the average execution time of our text search API taking way too long.

<img src="{{ site.baseurl }}/assets/elk-problem.png">