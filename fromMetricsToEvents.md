# From Metrics to Events

# Metrics - How they're made

## The Basics

```
function A 
	do something 
	call function B once
	do something Else
	
function B 
	do a thing
	for n times 
		call function C
	do another thing

funtion C
	do yet another thing
```

--- Then add timers to everything ---

```
function A 
	[New Relic Timer A start]
	do something 
	call function B once
	do something Else
	[New Relic Timer A stop]
	
function B 
	[New Relic Timer B start]
	do a thing
	for n times 
		call function C
	do another thing
	[New Relic Timer B stop]

funtion C
	[New Relic Timer C start]
	do yet another thing
	[New Relic Timer C stop]
```

## Record all meta data

Warning, it's going to be huge!

Function Name|Start Time|Stop Time
---|---|---
A|100|1000
B|200|800
C|250|300
C|325|380
C|385|440

![A B and C Timing](/art/fMtE-functionTimingDiagrams/Slide1.png)

But we don't really want starts and stops, what we really want to find out is duration. But not just overall (inclusive) duration of each function, we also want the duration of the calling function (exclusive).

Duration Inclusive Table:

Function|Duration
---|---
A|900
B|600
C|50
C|55
C|55

![Inclusive Timing](/art/fMtE-functionTimingDiagrams/Slide2.png)

Duration Exclusive Table:

Function|Duration
---|---
A|300
B|440

![Exclusive Timing](/art/fMtE-functionTimingDiagrams/Slide3.png)

Then realize for a real system, we're not running this once, we're running this 100s, 1000s, or 1000000s of times per minute in somem systems. Sometimes it's longer, sometimes shorter, never exactly the same.

So now instead of an inclusive and exclusive table showing 5 and 2 values respectively. We have 100s, 1000s, or 1000000s of tables. That's a lot of data and simply too much to send back every minute. And this is an over-simplified example. It gets really gross in a real system. So what do we do?

## The Power of Statistics

You would expext that when we look at the timing of various functions over a large enough set you would get something that approximates some sort of normal distribution. 

![Normal Distribution](http://i.investopedia.com/normal_distribution.png)

This is almost true, but not quite. Turns out that in many biological, [financial](http://www.investopedia.com/articles/investing/102014/lognormal-and-normal-distribution.asp), [geological](http://worldcomplex.blogspot.com/2011/02/scale-invariance-in-geological.html), mechanical, and electrical systems have a response mechanism that is normalized, but normalized on a logarithmic scale. This is something that has been seen over and over again with function timing and still proves to be true on today's systems.

![Normal vs Lognormal Distribution](https://instream.zendesk.com/hc/en-us/article_attachments/200997439/lognormal_curve.png)

**Assumption:**  
The timing response of a function will follow a lognormal distribution.  
We can therefore describe N iterations of a function simply by describing the characteristics of the lognormal distribution that most closely matches the dataset.

### Accurate but lossy compression

Now we can take a table of thousands or tens of thousands of start and stop times for a function, plot it as a [lognormal distribution](https://en.wikipedia.org/wiki/Log-normal_distribution#Location_and_scale), and then describe all those datapoints with the following data points:

* time_mean = arithmetic mean or the centralized location (μ) for this set of measurements
* [variance](https://en.wikipedia.org/wiki/Variance) = derived from the scale (σ) for the distribution
* Other values: 
  * count = number of function calls made during this timeframe
  * time_min = what the best-case time was
  * time_max = what the worst-case time was

So now we've managed to accurately describe our responses, but instead of sending thousands and thousands (or more) of start and stop times tied to a single function and then multiplied by all the functions and their inclusive and exclusive variants...instead we get the same data, but with only a handful of values that must be transmitted. Now we have data small enough that we can send it over the internet and then recreate the description accurately on our side.

[Example of raw metric data](https://staging.newrelic.com/account/1/agent/1441/metrics/5b22436f6e74726f6c6c65722f736572766572732f696e6465782e6a736f6e222c22225d)

![raw metric data](/art/metricDataDump.png)

## Traces

But what if I want to see specific instances?

But just getting the aggregate information isn't enough for finding what's really going on. Typically we want to look at the things that are on the long end of the tail and would love to see WHY and HOW those things went wrong.

To solve this issue what we do is we create a trace for all the calls made during a minute, but we toss out all but the slowest 5 per minute. 

Q: Why?  
A: Because the slowest ones are typically of the greatest interest.

Q: Is that representative?   
A: Depends.

Q: What challenges could you run into?  
A: Longest trace could be a particular subset that you don't care as much about. Might also want to see traces for fastest or median traces. Sometimes the longest traces are all one particular issue that you can't solve, so you want to see the next biggest problem, but don't have that data.

[raw trace data](https://staging.newrelic.com/accounts/1/applications/1441/transactions#id=5b22436f6e74726f6c6c65722f736572766572732f696e6465782e6a736f6e222c22225d&app_trace_id=2d7b0-b90ae6d3-caa8-11e5-bf57-000af75963c0)

## Events

[Raw event data](https://insights.newrelic.com/accounts/1/query?query=SELECT%20*%20from%20Transaction%20WHERE%20appName%20%3D%20%27RPM%20Combined%20Production%27%20limit%201)

## What next?

Each of these types of data comes with its own set of advantages and drawbacks.

* Metric data is very information-dense in and of itself, but when you store all named metrics seperately the data can get quite large.
* Trace data can have an immensely rich, but comes at a high cost to the user and is too large to store all traces. 
* Event data is incredibly flexible, but uses a lot more disk space and that comes at a high cost.

Nic Benders gave a good talk on what all we'll be working on next

Lew Cirne and some other engineers are tinkering with ways to use NRDB to store Metric data even more efficiently than ever, while increasing our ability to search, parse, and bundle the metric data:  
[Lew's Timeslice file format ideas](https://newrelic.quip.com/ddKAAAG5Zav)

Our future platform rests not only on what data we store; but, how we store it, what information we can tease out for customers, and 

### Launchpoints and Links

* Architecture Notes: specifically the metric & event notes - https://pages.datanerd.us/engineering-management/architecture-notes/notes/
* Agent Specs - https://source.datanerd.us/agents/agent-specs/
* Specific Language Agent Specs - https://newrelic.atlassian.net/wiki/display/eng/Agent+Architecture
