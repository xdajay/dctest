---
permalink: basic-chart-configurations/legend.html
title: Configure Legend to Correlate Data Plots | FusionCharts
description: A legend is a chart element that is used to display the series name of each dataset in multi-series/combination charts
heading: Legend
chartPresent: true
---

A legend is a chart element that is used to display the series name of each dataset in multi-series/combination charts. Legends are not applicable to single series charts. Legends are used to correlate a data plot to its series name using its color.

In the following image, the legend rendered below the x-axis helps to identify the data plots corresponding to a series name.

![Configuring Your Chart - Legend]({{ site.baseurl }}assets/images/legend.png)

Each series is represented by it’s own icon in the legend.

This article talks about:

* <a href="{{ site.baseurl }}basic-chart-configurations/legend.html#showinghiding-the-corresponding-data-series-when-a-legend-item-is-clicked">Showing/hiding the corresponding data series when a legend icon is clicked</a>

* <a href="{{ site.baseurl }}basic-chart-configurations/legend.html#highlighting-the-corresponding-data-series-when-a-legend-text-is-hovered-over">Highlighting the corresponding data series when a legend text is hovered over</a>

* <a href="{{ site.baseurl }}basic-chart-configurations/legend.html#setting-the-legend-position">Setting legend position</a>

* <a href="{{ site.baseurl }}basic-chart-configurations/legend.html#configuring-legend-icon-size">Configuring legend icon size</a>

* <a href="{{ site.baseurl }}basic-chart-configurations/legend.html#drawing-a-custom-legend-icon-shape">Drawing a custom legend icon</a>

* <a href="{{ site.baseurl }}basic-chart-configurations/legend.html#customizing-legend-scroll-bar">Customizing legend scroll bar</a>

* <a href="{{ site.baseurl }}basic-chart-configurations/legend.html#reversing-legend-order">Reversing legend order</a>

* <a href="{{ site.baseurl }}basic-chart-configurations/legend.html#hiding-legend">Hiding legend</a>

* <a href="{{ site.baseurl }}basic-chart-configurations/legend.html#hiding-series-upon-loading">Hiding series upon loading</a>

* <a href="{{ site.baseurl }}basic-chart-configurations/legend.html#customizing-legend-appearance">Customizing legend appearance</a>

* <a href="{{ site.baseurl }}basic-chart-configurations/legend.html#customizing-legend-font-cosmetics">Customizable legend font cosmetics</a>

## Showing/hiding the corresponding data series when a legend item is clicked

FusionCharts Suite XT supports legend interactivity. One of the features that comes under legend interactivity is being able to show/hide the data plots belonging to a data series by clicking the corresponding legend icon.

In the live chart shown below, when the legend icon for __Last Year__ is clicked, all data plots in blue, showing the quarterly revenue for the last year, are hidden.

{% embed_all {"source": "configuring-your-chart-legend-example-10.js", "id": "10"} %}

## Highlighting the corresponding data series when a legend text is hovered over

Starting FusionCharts Suite XT v3.10.0, FusionCharts has introduced a new legend interactivity feature. Now, every time the mouse pointer is hovered over a legend text, the corresponding data plots are highlighted by decreasing the opacity of the data plots belonging to the other data series.

For example, in the chart shown below, when the mouse pointer is hovered over the legend text __This Year__, the data plots in blue (corresponding to __Last Year__) fadeout and the data plots in green (corresponding to __This Year__) are highlighted.

{% embed_all {"source": "configuring-your-chart-legend-example-11.js", "id": "11"} %}

Given below is a brief description of the attribute used to enable this feature:

<table>
  <tr>
    <th> Attribute Name </th>
    <th> Description </th>
  </tr>
  <tr>
    <td> `plotHighlightEffect` </td>
    <td> Sets the highlight effect for data plots when the mouse pointer is hovered over a legend item. When the mouse pointer is hovered over a legend text and `plotHighlightEffect` attribute is set to `fadeout`, it causes the data plots belonging to the other data series to fadeout, by reducing their opacity. </td>
  </tr>
</table>


### Customizing the highlight effect

Instead of just reducing the opacity of the data plots that don't correspond to the hovered over legend text, you can customize a different effect. 

Take a look at the sample chart shown below:

{% embed_all {"source": "configuring-your-chart-legend-example-12.js", "id": "12"} %}

In this chart, when the mouse pointer is hovered over the legend text __This Year__, data plots belonging to the __Last Year__ data series are grayed out. 

The `plotHighlightEffect` attribute is defined in the following format in order to customize the highlight effect:

{% highlight javascript lineanchors %}{% raw %}

 plotHighlightEffect=effectName|confStr 

 {% endraw %}{% endhighlight %}

__effectName__ always stays __fadeout__. __confStr__ is a comma-separated list of customization properties for the effect.

Therefore, for the above chart, the attribute has been defined as shown below:

{% highlight javascript lineanchors %}{% raw %}

`"plotHighlightEffect": "fadeout|color=#7f7f7f, alpha=60"`

{% endraw %}{% endhighlight %}

In addition, the following attributes can also be used to customize the highlight effect:

<table>
  <tr>
    <th> Attribute Name </th>
    <th> Description </th>
  </tr>
  <tr>
    <td> `color` </td>
    <td> Hex code for the data plot fill color </td>
  </tr>
  <tr>
    <td> `alpha` </td>
    <td> Transparency of the data plots </td>
  </tr>
  <tr>
    <td> `borderColor` </td>
    <td> Hex code for the plot border color </td>
  </tr>
  <tr>
    <td> `borderAlpha` </td>
    <td> Transparency of the plot border <br> If this attribute is not defined as part of the configuration string, then it takes the value assigned to the attribute `alpha` (in the configuration string). </td>
  </tr>
  <tr>
    <td> `anchorBgColor` </td>
    <td> Hex code for the anchor background color </td>
  </tr>
  <tr>
    <td> `anchorBorderColor` </td>
    <td> Hex code for anchor border color <br> If this attribute is not defined as part of the configuration string, then it takes the value assigned to the attribute `color` (in the configuration string). </td>
  </tr>
  <tr>
    <td> `anchorBgAlpha` </td>
    <td> Transparency of the anchor background </td>
  </tr>
  <tr>
    <td> `anchorBorderAlpha` </td>
    <td> Transparency of the anchor border </td>
  </tr>
  <tr>
    <td> `valueBgColor` </td>
    <td> Hex code for the data value background color </td>
  </tr>
  <tr>
    <td> `valueBorderColor` </td>
    <td> Hex code for the data value border color </td>
  </tr>
  <tr>
    <td> `valueFontColor` </td>
    <td> Hex code for the data value font color <br> If this attribute is not defined as part of the configuration string, then it takes the value assigned to the attribute `color` (in the configuration string). </td>
  </tr>
</table>


## Setting the legend position

A multi-series column 2D chart with the legend positioned in the right looks as below:

{% embed_all {"source": "configuring-your-chart-legend-example-1.js", "id": "1"} %}

The attribute to set legend position is as mentioned below.

<table>
  <tr>
    <th>Attribute Name</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>`legendPosition`</td>
    <td>The legend can be plotted at two positions on the chart - below the chart for value `bottom` and to the right of the chart for value `right`.</td>
  </tr>
  <tr>
    <td>`legendAllowDrag`</td>
    <td>The legend can be made drag-able by setting this attribute to `1`. Set this to `0` (default) to disable dragging. </td>
  </tr>
</table>


## Configuring legend icon size

A multi-series column 2D chart with legend icon size changed to '**2'** looks as below:

{% embed_all {"source": "configuring-your-chart-legend-example-2.js", "id": "2"} %}

The attribute to configure legend icon size is detailed below:

<table>
  <tr>
    <th>Attribute Name</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>`legendIconScale`</td>
    <td>Scaling of legend icon is possible in FusionCharts XT. This attribute lets you control the size of legend icon with valid values from `1` (100%) to `5` (500%).</td>
  </tr>
</table>


## Drawing a custom legend icon shape

A multi-series column 2D chart with a custom legend icon shape looks as below:

{% embed_all {"source": "configuring-your-chart-legend-example-9.js", "id": "9"} %}

Given below are the attributes used to draw a custom legend icon shape:

<table>
  <tr>
    <th>Attribute Name</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>`drawCustomLegendIcon`</td>
    <td>Sets whether drawing a custom legend icon will be enabled. Setting this attribute to `1` will enable the feature, setting it to `0` (default) will disable it. All legend icon customization attributes work only if this feature is enabled. </td>
  </tr>
  <tr>
    <td>`legendIconBorderColor`</td>
    <td>Sets the hex color code for the border of the legend icon. By default, it is assigned the data plot border color.</td>
  </tr>
  <tr>
    <td>`legendIconBgColor`</td>
    <td>Sets the hex color code for the background of the legend icon. By default, it is assigned the data plot fill color.</td>
  </tr>
  <tr>
    <td>`legendIconAlpha`</td>
    <td>Sets the legend icon transparency. This attribute takes values between `0` (transparent) and `100` (opaque; default). </td>
  </tr>
  <tr>
    <td>`legendIconBgAlpha`</td>
    <td>Sets the legend icon background transparency. This attribute takes values between `0` (transparent) and `100` (opaque; default).</td>
  </tr>
  <tr>
    <td>`legendIconSides`</td>
    <td>Sets the number of sides for the legend icon. The default value is __4__.</td>
  </tr>
  <tr>
    <td>`legendIconBorderThickness`</td>
    <td>Sets the thickness of the legend icon border. The default value is __1__. </td>
  </tr>
  <tr>
    <td>`legendIconStartAngle`</td>
    <td>Sets the starting angle for drawing the legend icon. The default value is __45__.</td>
  </tr>
</table>


## Customizing legend scroll bar

If you have multiple data items in a multi-series chart, the legend automatically displays a scroll bar.

A multi-series column 2D chart with customized cosmetic properties of the legend scroll bar looks as below:

{% embed_all {"source": "configuring-your-chart-legend-example-3.js", "id": "3"} %}

The list of the attributes used to customize cosmetic properties of the legend scroll bar is mentioned below:

<table>
  <tr>
    <th>Attribute Name</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>`legendScrollBgColor`</td>
    <td>Sets the background color of the scroll bar. Accepts hex code. e.g. `#00ffaa`.</td>
  </tr>
</table>


## Reversing legend order

A multi-series column 2D chart with the order of legend items reversed looks as below:

{% embed_all {"source": "configuring-your-chart-legend-example-4.js", "id": "4"} %}

The attribute to reverse legend order is mentioned below:

<table>
  <tr>
    <th>Attribute Name</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>`reverseLegend`</td>
    <td>You can reverse the ordering of datasets in the legend by setting this attribute to `1`. This is set to `0` by default.</td>
  </tr>
</table>


## Hiding legend

A multi-series column 2D chart with legend hidden looks as below:

{% embed_all {"source": "configuring-your-chart-legend-example-5.js", "id": "5"} %}

The attribute to show or hide a legend is mentioned in the table below:

<table>
  <tr>
    <th>Attribute Name</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>`showLegend`</td>
    <td>Whether to show legend on the chart. Set it to `1` to show the legend or to `0` to hide it.</td>
  </tr>
</table>


## Hiding series upon loading

A multi-series column 2D chart with one data series hidden looks as below:

{% embed_all {"source": "configuring-your-chart-legend-example-6.js", "id": "6"} %}

Given below is the attribute used to initially hide a dataset on chart loading:

<table>
  <tr>
    <th>Attribute Name</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>`initiallyHidden`</td>
    <td>Works from the `dataset` object level in JSON data. Set it to `1` to hide the plots of a series initially, on chart load. Default value is `0` for all series and they show up initially.</td>
  </tr>
</table>


## Customizing legend appearance

A multi-series column 2D chart legend with customized appearance looks as below:

{% embed_all {"source": "configuring-your-chart-legend-example-7.js", "id": "7"} %}

Given below is the list of attributes used to customize the legend appearance:

<table>
  <tr>
    <th>Attribute Name</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>`legendBgColor`</td>
    <td>Background color for the legend. Accepts hex code. e.g. `#00ffaa`.</td>
  </tr>
  <tr>
    <td>`legendBgAlpha`</td>
    <td>Background alpha for the legend. It can take values from `0` (transparent) to `100` (opaque).</td>
  </tr>
  <tr>
    <td>`legendBorderColor`</td>
    <td>Border Color for the legend. Accepts hex code. e.g. `#00ffaa`.
</td>
  </tr>
  <tr>
    <td>`legendBorderThickness`</td>
    <td>Border thickness for the legend (in pixels).</td>
  </tr>
  <tr>
    <td>`legendBorderAlpha`</td>
    <td>Border alpha for the legend. It can take values from `0`(transparent) to `100` (opaque).</td>
  </tr>
  <tr>
    <td>`legendShadow`</td>
    <td>Whether to show a shadow for legend. Set it to `1` to show shadow and `0` to hide it.</td>
  </tr>
  <tr>
    <td>`legendScrollBgColor`</td>
    <td>If you've too many items on the legend, a scroll bar shows up on the same. This attribute lets you configure the background color of the scroll bar. Accepts hex code. e.g. `#00ffaa`.</td>
  </tr>
  <tr>
    <td>`legendCaptionAlignment`</td>
    <td>Sets the legend caption horizontal alignment with valid values of `left`, `center` and `right`.</td>
  </tr>
</table>


## Customizing legend font cosmetics

A multi-series column 2D chart legend with customized font cosmetics looks as below:

{% embed_all {"source": "configuring-your-chart-legend-example-8.js", "id": "8"} %}

Given below is the list of attributes used to customize the legend font cosmetics:

<table>
  <tr>
    <th>Attribute Name</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>`legendItemFont`</td>
    <td>Sets legend item font, e.g. `Arial`</td>
  </tr>
  <tr>
    <td>`legendItemFontSize`</td>
    <td>Sets legend item font size, with values ranging from `0` to `72`</td>
  </tr>
  <tr>
    <td>`legendItemFontColor`</td>
    <td>Sets legend item font color in hex code, e.g. `#00ffaa`</td>
  </tr>
  <tr>
    <td>`legendItemFontBold`</td>
    <td>Whether legend keys should be displayed in bold. Set `1` to make it bold or `0` to keep it normal.</td>
  </tr>
  <tr>
    <td>`legendItemHoverFontColor`</td>
    <td>Sets legend item font color on hover in hex code, e.g. `#00ffaa`</td>
  </tr>
  <tr>
    <td>`legendCaptionFont`</td>
    <td>Sets legend caption font, e.g. `Arial`</td>
  </tr>
  <tr>
    <td>`legendCaptionFontSize`</td>
    <td>Sets legend caption font size, with values ranging from `0` to `72`</td>
  </tr>
  <tr>
    <td>`legendCaptionBold`</td>
    <td>Whether legend caption should be displayed in bold. Set `1` to make it bold or `0` to keep it normal.</td>
  </tr>
</table>