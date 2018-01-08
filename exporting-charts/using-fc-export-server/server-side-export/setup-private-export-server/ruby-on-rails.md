---
permalink: exporting-charts/using-fc-export-server/server-side-export/setup-private-export-server-ruby-on-rails.html
title: Setup Private Export Server Using Ruby on Rails | FusionCharts
description: To setup a private export server in Ruby on Rails, you will need to install the official RoR export handler in your project.
heading: Ruby on Rails
chartPresent: false
---

To setup a private export server in Ruby on Rails, you will need to install the __official RoR export handler__ in your project. The export handler will handle all exporting requests sent by the user and generate the chart in the requested format. The FusionCharts RoR export handler is dependent on two external modules—__Inkscape__ and __ImageMagick__—for conversion. These modules need to be downloaded and installed separately on the same server.

<p class="text-info"> Starting FusionCharts Suite XT v3.11.0, __Inkscape__ and __ImageMagick__ are no longer required for browsers with canvas support. </p>

## How does it work?

__Step 1__: A chart is rendered in the browser.

__Step 2__: When an export option is selected, the chart generates the SVG string that represents the current state and sends it to the export server.

__Step 3__: The export server captures the SVG string.

__Step 4__: The export server invokes a system call, triggering __Inkscape__ to convert the FusionCharts generated SVG string (which is passed to the server-side script over AJAX) to __PDF__, __PNG__, and __SVG__. However, __Inkscape__ still has a limitation of generating a JPG file. Hence, __ImageMagick__ is used to create the __JPG__ files. To export chart data as __XLS__, the CSV data generated from the charts is converted to the XLS format.

<p class="text-info"> FusionCharts Suite XT v3.11 onwards processes images on the client-side for modern browsers (with canvas support). This eliminates the use of third party softwares like __Inkscape__ and __ImageMagick__ for server-side as well as client-side exporting. </p>

__Step 5__: The export handler either writes the exported chart/chart data to disk, based on the configuration provided by  the chart, or streams it back to the user as a download.

## Installation

__Step 1__: Add this line to your application's Gemfile: <br/>

```javascript
    gem 'fusioncharts_exporter'
    ```

__Step 2__: Execute:
```javascript
    $ bundle
    ```

__Step 3__: Install both __Inkscape__ and __ImageMagick__ as they are necessary dependencies for the RoR export handler to work.

<p class="text-info">  Starting FusionCharts Suite XT v3.11.0, __Inkscape__ and __ImageMagick__ are no longer required for browsers with canvas support. In that case, this step can be skipped. </p>

__Step 4__: The gem provides a generator to create the required configuration files and directories. Run the following command: <br/>
```javascript
    $ rails generate fusioncharts_exporter:install
    ```

This creates the following files and directories:
- __config/fusioncharts_exporter.yml__
- __tmp/fusioncharts/__

<p class="text-info"> Starting v3.11.0, FusionCharts supports exporting chart data as __XLS__. To export chart data in the XLS format, using server-side exporting, it is mandatory that the exporting server has the latest code, which is available in the FusionCharts package. Alternatively the FusionCharts export link, __export.api3.fusioncharts.com__, can also be used.  </p>

## Inkscape

Inkscape is an open source vector graphics editor. What sets Inkscape apart is its use of Scalable Vector Graphics (SVG), an open XML-based W3C standard, as the native format. Inkscape has a powerful command line interface and can be used in scripts for a variety of tasks, such as exporting and format conversions. 
For more details, click [here](http://inkscape.org/doc/inkscape-man.html).

## ImageMagick

ImageMagick is a free and open-source software suite for displaying, converting, and editing raster image and vector image files. The software mainly consists of a number of command-line interface utilities for manipulating images.
For more details, click [here](http://www.imagemagick.org/).

## Configuration

The following are the configurables to be modified as required in the __config/fusioncharts_exporter.yml__:<br/>

- Set `inkscape_path` as the location of the __Inkscape__ executable.

- Set `imagemagick_path` as the location of the __ImageMagick__ executable.

- Set `save_path` as the location on the server where the image will be saved.


## Mount the application

You will have to specify the end point of the export server. In order to do this, you will have to mount the export handler to your rails application. Add the following lines in __config/routes.rb__: <br/>
```htmlmount FusionchartsExporter::Engine, at: "<path>"```


For example, if you want your export server hosted at __http://example.com/export__, then add the following lines:

```javascriptmount FusionchartsExporter::Engine, at: "export"```