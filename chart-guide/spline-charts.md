---
permalink: chart-guide/spline-charts.html
title: Spline Charts Guide | FusionCharts
description: Spline charts are a specialized form of line charts that display smooth curves through the different data points.
heading: Spline Charts
chartPresent: true
---

Spline charts are a specialized form of line charts that display smooth curves through the different data points.

In this section, you will be introduced to the:

* <a href="{{ site.baseurl }}chart-guide/spline-charts.html#basics-of-spline-charts">Basics of spline charts</a>

* <a href="{{ site.baseurl }}chart-guide/spline-charts.html#types">Types of spline charts</a>

## Basics of Spline Charts

Spline charts integrate all the characteristics of a conventional line chart except for the fact that unlike line charts, which connect data points with straight lines, spline charts draw a fitted curved line to join the data points.

Spline charts can be used for plotting data that requires the usage of curve-fitting e.g. an impulse-response chart, a product life cycle chart, etc. It is also significantly used in designing Pareto charts.

## Types

FusionCharts Suite XT includes four types of spline charts:

* <a href="{{ site.baseurl }}chart-guide/spline-charts.html#single-series-spline-2d-chart">Single-series spline 2D chart</a>

* <a href="{{ site.baseurl }}chart-guide/spline-charts.html#multi-series-spline-2d-chart">Multi-series spline 2D chart</a>

* <a href="{{ site.baseurl }}chart-guide/spline-charts.html#multi-series-spline-area-2d-chart">Single-series spline area 2D chart</a>

* <a href="{{ site.baseurl }}chart-guide/spline-charts.html#single-series-spline-area-2d-chart">Multi-series spline area 2D chart</a>

### Single-series Spline 2D Chart

A single-series spline 2D chart draws a single fitted curve through the data points.

A simple single-series spline 2D chart looks like this:

{% embed_all {"source": "chart-guide-spline-charts-example-1.js", "id": "1"} %}





### Multi-series Spline 2D Chart

A simple multi-series spline 2D chart looks like this:

{% embed_all {"source": "chart-guide-spline-charts-example-2.js", "id": "2"} %}

To render a multi-series spline chart:

* Set the `type` attribute to `msspline`.

* Use the `seriesname` attribute and the `data` object, which belong to the `dataset` object, to specify multiple datasets.

### Multi-series Spline Area 2D Chart

A multi-series spline area 2D chart is nothing but a conventional area with a smoothened curve drawn through the data points in the series. It allows you to plot data for multiple data sets.

A simple multi-series spline area 2D chart looks like this:

{% embed_all {"source": "chart-guide-spline-charts-example-3.js", "id": "3"} %}

### Single-series Spline Area 2D Chart

A simple single-series spline area area 2D chart looks like this:

{% embed_all {"source": "chart-guide-spline-charts-example-4.js", "id": "4"} %}

To render a single-series spline chart:

* Set the `type` attribute to `splinearea`.

<p class="text-info">Spline and spline area charts do not support joining of empty data points in the chart. That means, if your chart does not contain data at a particular point, the data points cannot be connected to each other and will appear as a broken dataset.</p>