---
layout: post
title: "On Traffic Flow"
description: ""
category: 
tags: [musings]
---
{% include JB/setup %}

> "29 minutes from the Aurora Toll Plaza to the North-South Tollway."  

* * * 

Most of my professional work has been centered around high-performance systems, so when I hear something like the statement above, I think: 'Has that been experimentally verified?'

So, while I'm sitting there in traffic, I wonder about how these things are actually measured. (N.B. I am not a statistician or a mathematician. I am a computer scientist, and my speculations are purely that.)

## Direct measurement

* Choose a reference car at Point A at time t<sub>0</sub>.
* Wait until that car passes Point B at time t<sub>1</sub>.
* Subtract t<sub>0</sub> from t<sub>1</sub> and report that as the travel time from A to B.

This suffers from a critical issue.  The measurement only tells you how long it takes the reference car to travel the selected segment *at t<sub>0</sub>*.  By the time you have the measurement, it is invalid.  A car at Point A at t<sub>1</sub> may have a longer or shorter travel time depending on how traffic is changing. We need some way of measuring that takes changing conditions into account.

## Extrapolation

* For all cars C passing Point A at time t<sub>C0</sub>
  * Measure the time until car C passes Point B
* Extrapolate to predict the travel time of Car X at time t<sub>X0</sub>

This, however, seems extremely subject to recent changes.  Your most recent measurement is still far in the past.  Using a local regression, we don't have the data points that would lend the most credibility to our prediction, so our model is probably a bad predictor.

## Instantaneous Travel Time

We really need to reduce the time it takes to get a measurement so we have some better data for our model.  The best idea I've come up with so far is as follows.

### To measure travel time between points A and B

* Choose N points between A and B inclusive.  These points need not be equidistant, but point P<sub>0</sub> should be at A, and point P<sub>N-1</sub> should be at B.
* Measure the time required for some car C<sub>n</sub> to travel between points P<sub>n</sub> and P<sub>n+1</sub>
* Sum all measurements and record that as your instantaneous travel time.

We still can't predict changes in travel flow, but at least we have an estimate *now*, which may be useful to drivers.

## The actual methodology

[This site](http://ops.fhwa.dot.gov/publications/tt_reliability/TTR_Report.htm#Whatmeasures) explains how travel times are actually predicted. 

It turns out that it is nothing like the methods I proposed.  More than likely it is simply not feasible to measure traffic with the granularity that I propose, so historical models are more effective.  It will be interesting to see how increased data collection changes these methods, and how it impacts prediction.
