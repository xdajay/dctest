---
permalink: chart-guide/error-charts/introduction.html
title: Introduction to Error Chart | FusionCharts
description: An error chart is used to show the extent of uncertainty in information relative to an average value.
heading: Introduction to Error Chart
chartPresent: true
---

An error chart is used to show the extent of uncertainty in information relative to an average value. Error charts can be used to show the range of values that can be taken up by a data point, instead of being restricted to a point value.

In this section, you will be introduced to the:

* <a href="{{ site.baseurl }}chart-guide/error-charts/introduction.html#basics-of-an-error-chart">Basics of an error chart</a>

* <a href="{{ site.baseurl }}chart-guide/error-charts/introduction.html#use-of-error-charts">Use of error charts</a>

* <a href="{{ site.baseurl }}chart-guide/error-charts/introduction.html#types-of-error-charts">Types of error charts</a>

* <a href="{{ site.baseurl }}chart-guide/error-charts/introduction.html#features-of-an-error-chart">Features of an error chart</a>

## Basics of an Error Chart

An error chart shows the range of possible errors or deviations that might occur in the given data. Errors are indicated by distinct I-shaped bars that are both positive and negative. Typically the I-bars represent the standard deviation in a measurement indicating the degree of variance observed in a data point. Error charts give a general idea of the accuracy of information or, conversely, the amount of variation in data from it’s expected value.

## Use of Error Charts

Following are a few areas where error charts are commonly used:

* Appliance testing

* Scientific research

* Monitoring systems

* Weather analysis

* Human resource management

## Types of Error Charts

At present, there are three types of multi-series error charts available in the FusionCharts XT Suite:

* [Error bar chart]{% linkTo attrs.md chart=errorbar2d %}

* [Error line chart]{% linkTo attrs.md chart=errorline %}

* [Error scatter chart (XY plot)]{% linkTo attrs.md chart=errorscatter %}

### Error Bar Chart

An error bar chart looks like this:

{% embed_all {"source": "chart-guide-error-charts-introduction-example-1.js", "id": "1"} %}

### Error Line Chart

An error line chart looks like this:

{% embed_all {"source": "chart-guide-error-charts-introduction-example-2.js", "id": "2"} %}

### Error Scatter Chart

An error scatter chart looks like this:

{% embed_all {"source": "chart-guide-error-charts-introduction-example-3.js", "id": "3"} %}

## Features of an Error Chart

The distinct features of an error chart include:

* Supports both half and full error bars for positive and negative errors respectively.

* Provides options to configure error bars by changing their color, thickness, and transparency.

* Automatically customizes the width of the error bars depending on the importance of the deviation from actual data.