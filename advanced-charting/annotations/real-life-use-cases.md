---
permalink: advanced-chart-configurations/annotations/real-life-use-cases.html
title: Real-life Use Cases | FusionCharts
description: This article describes how annotations can be used in adding a data callout label, providing more information about the data plots, customising Y axis, adding more context to the chart, adding images for better visualization, events triggering display of annotation items and creating a collaborative dashboard.
heading: Real-life Use Cases
chartPresent: true
---

This article describes how annotations can be used in the following scenarios:

* <a href="{{ site.baseurl }}advanced-chart-configurations/annotations/real-life-use-cases.html#adding-a-data-callout-label">Adding a data callout label</a>

* <a href="{{ site.baseurl }}advanced-chart-configurations/annotations/real-life-use-cases.html#providing-more-information-about-data-plots">Providing more information about the data plots</a>

* <a href="{{ site.baseurl }}advanced-chart-configurations/annotations/real-life-use-cases.html#customizing-the-y-axis">Customising Y Axis</a>

* <a href="{{ site.baseurl }}advanced-chart-configurations/annotations/real-life-use-cases.html#adding-more-context-to-the-chart">Adding more context to the chart</a>

* <a href="{{ site.baseurl }}advanced-chart-configurations/annotations/real-life-use-cases.html#annotation-images-for-better-visualization">Adding images for better visualization</a>

* <a href="{{ site.baseurl }}advanced-chart-configurations/annotations/real-life-use-cases.html#events-triggering-display-of-annotation-items">Events triggering display of annotation items</a>

* <a href="{{ site.baseurl }}advanced-chart-configurations/annotations/real-life-use-cases.html#creating-a-collaborative-dashboard">Creating a collaborative dashboard</a>

## Adding a Data Callout Label

{% embed_chart {"source": "advanced-charting-annotations-real-life-use-cases-example-1.js", "id": "1"} %}

The above chart shows the usage of annotations to create a callout (using a rectangle, a polygon, and a text annotation, grouped together) above a column. The annotations are dynamically  positioned using annotation macros. After the chart is rendered (when the [renderComplete]{% linkTo FusionCharts.events.renderComplete %}  event is triggered), the quarter with the highest revenue is determined and the annotation group is positioned over the data plot representing that quarter.

The data structure for this chart is given below::

{% embed_data {"source": "advanced-charting-annotations-real-life-use-cases-example-1.js"} %}

## Providing More Information about Data Plots

{% embed_chart {"source": "advanced-charting-annotations-real-life-use-cases-example-2.js", "id": "2"} %}

The above chart compares the footfall at two stores, Bakersfield Central and Los Angeles Topanga.

When the mouse pointer is hovered over a data plot, it triggers the [dataplotRollover]{% linkTo FusionCharts.events.dataplotRollOver %} event. Consequently, an annotation group (containing of a line, a label, and text annotation) that displays additional information about the data plot is shown. When the mouse pointer is hovered out of the data plot, it triggers the [dataPlotRollOut]{% linkTo FusionCharts.events.dataplotRollOut %} event and the annotation group is hidden.

Macro sub-tokens are used to position the annotation group with respect to the axes and datasets. The `hide()` method is used to hide the group.

The data structure for this chart is given below:

{% embed_data {"source": "advanced-charting-annotations-real-life-use-cases-example-2.js"} %}

## Customizing the Y-axis

{% embed_chart {"source": "advanced-charting-annotations-real-life-use-cases-example-2a.js", "id": "3"} %}

The above chart showcases annotations positioned dynamically, with respect to the y-axis, using macros. The annotations are used to mark three different ranges - low, moderate and high, with three different colors.

The data structure for this chart is given below:

{% embed_data {"source": "advanced-charting-annotations-real-life-use-cases-example-2a.js"} %}

## Adding More Context to the Chart

{% embed_chart {"source": "advanced-charting-annotations-real-life-use-cases-example-3.js", "id": "4"} %}

The above gauge shows the customer satisfaction score with some significant data like, the state average and the national average, using annotation shapes and text elements.

The data structure for this chart is given below:

{% embed_data {"source": "advanced-charting-annotations-real-life-use-cases-example-3.js"} %}

## Annotation Images for Better visualization

{% embed_chart {"source": "advanced-charting-annotations-real-life-use-cases-example-4.js", "id": "5"} %}

In this chart, images of brands are shown instead of the conventional 2D column data plots. Using these annotations makes the chart more intuitive while also increasing its visual appeal. Imagine how easy it becomes for your audience to read data in a chart like this, especially if the data is for a large number of brands.

The data structure for this chart is given below:

{% embed_data {"source": "advanced-charting-annotations-real-life-use-cases-example-4.js"} %}

## Events Triggering Display of Annotation Items

{% embed_chart {"source": "advanced-charting-annotations-real-life-use-cases-example-5.js", "id": "6"} %}

The above chart shows how you can use events on annotation items. Hovering the mouse pointer on the Weekend zone that is represented by a green rectangle on the chart, triggers the events `annotationRollOver` and `annotationRollOut`, which show the total footfall on Saturday and Sunday.

The data structure for configuring events on annotation items is as follows:

{% embed_data {"source": "advanced-charting-annotations-real-life-use-cases-example-5.js"} %}

## Creating a Collaborative Dashboard

Click [here](http://www.fusioncharts.com/dashboards/collaboration/) to see a collaborative dashboard that is a complex and practical example of how annotations can be used to add more information to a chart.

Notice the callout that renders above the data plot for April. The callout is an annotation. When this callout is clicked, `annotationClick` event is triggered. This navigates the user to a view that shows the monthly sales analysis for April in the left pane and user comments on this analysis in the right pane. Every time a comment is added, the text annotation (showing the number of comments) alongside the callout is updated.

Annotations, thus, let you add more information to your charts, creatively.