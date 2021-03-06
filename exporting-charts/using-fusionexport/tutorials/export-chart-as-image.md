---
permalink: exporting-charts/using-fusionexport/tutorials/export-chart-as-image.html
title: Export chart as image | FusionCharts
description: This article talks about the SDKs used for exporting charts as images.
heading: Export chart as image
chartPresent: False
---

Let's start with a simple chart export. For exporting a single chart, save the chart configuration in a JSON file. The configuration should be inside an array.
To export charts as images, you can use the CLI or SDKs of the languages mentioned below, using the command given below:

<ul class="code-tabs extra-tabs">
    <li class="active"><a data-toggle="cli">CLI</a></li>
    <li><a data-toggle="nodejs">Node.js</a></li>
    <li><a data-toggle="java">Java</a></li>
    <li><a data-toggle="csharp">C#</a></li>
    <li><a data-toggle="php">PHP</a></li>
    <li><a data-toggle="python">Python</a></li>
    <li><a data-toggle="golang">Golang</a></li>
</ul>

<div class="tab-content extra-tabs">
    <div class="tab cli-tab active">
    <div class="pb-10">FusionExport CLI accepts a chart’s configuration using the  <strong>--chart-config</strong> or <strong>-c</strong> options.</div>
    <div class="mt-10 pb-10"><strong>For exporting a single chart from the CLI, using a JSON file:</strong></div>
    <div><strong>Step 1</strong></div>
    <div class="pb-10">Save the chart configuration in a JSON file named as chart-config-file.json</div>
    
```javascript
        [
   {
      "type": "column2d",
      "renderAt": "chart-container",
      "width": "550",
      "height": "350",
      "dataFormat": "json",
      "dataSource": {
         "chart": {
            "caption": "Number of visitors last week",
            "subCaption": "Bakersfield Central vs Los Angeles Topanga"
         },
         "data": [
            {
               "label": "Mon",
               "value": "15123"
            },
            {
               "label": "Tue",
               "value": "14233"
            },
            {
               "label": "Wed",
               "value": "25507"
            }
         ]
      }
   }
]
        ```

    <div class="mt-20"><strong>Step 2</strong></div>
    <div class="pb-10">To export the file, run the following command from the terminal/command prompt:</div>
```javascript
    $ fe -c chart-config-file.json
    ```

    <div class="mt-30"><strong>For exporting a single chart from the CLI, using a JS file:</strong></div>
    <div class="mt-20"><strong>Step 1</strong></div>
    <div class="pb-10">Save the chart configuration in a JavaScript file named as <strong>chart-config-file.js</strong>. In this case, the whole chart configuration object must be exported. </div>

```javascript
    module.exports = {
  // fusioncharts config
};
    ```

    <div class="mt-20"><strong>Step 2</strong></div>
    <div class="pb-10">To use this newly created JavaScript file for the export, execute the following command:</div>
```javascript
    $ fe -c chart-config-file.js
    ```
    </div>
    <div class="tab nodejs-tab">
```javascript
        const fs = require('fs');
const path = require('path');

// require fusionexport
const FusionExport = require('../');

const chartConfig = JSON.parse(fs.readFileSync(path.resolve(__dirname, 'chart-config-file.json')).toString());
const host = '127.0.0.1';
const port = 1337;

// instantiate FusionExport
const fusion = new FusionExport({ host, port });

const exportConfig = {
  chartConfig,
};

// provide the export config
fusion.export(exportConfig);

fusion.on('exportDone', (files) => {
  // files can be read from files array
  // e.g. [{tmpPath:"", realName: ""}]
});

fusion.on('exportStateChange', (state) => {
  // called for export progress state change
});

fusion.on('error', (err) => {
  // catch error here
});

        ```
    </div>
    <div class="tab java-tab">
```java
        import java.io.ByteArrayOutputStream;
import java.io.File;
import java.io.FileInputStream;
import java.io.InputStream;
import com.fusioncharts.fusionexport.client.*; // import sdk

public class ExportChart implements ExportDoneListener, ExportStateChangedListener {

    public static void main(String[] args) {

        // Instantiate the ExportConfig class and add the required configurations
        ExportConfig config = new ExportConfig();
        config.set("chartConfig", readFile("fullpath/of/chart-config-file.json"));

        // Instantiate the ExportManager class
        ExportManager em = new ExportManager();
        // Call the export() method with the export config and the respective callbacks
        em.export(config, new ExportChart(), new ExportChart());
    }

    @Override // Called when export is done
    public void exportDone(String result, ExportException error) {
        if (error != null) {
            System.out.println(error.getMessage());
        } else {
            System.out.println("DONE: " + result);
        }
    }

    @Override // Called on each export state change
    public void exportStateChanged(String state) {
        System.out.println("STATE: " + state);
    }

    private static String readFile(String file) {
        String fileContent = "";
        try {
            File f = new File(file);
            FileInputStream inp = new FileInputStream(f);
            byte[] bf = new byte[(int) f.length()];
            inp.read(bf);
            fileContent = new String(bf, "UTF-8");
        } catch (Exception e) {
            e.printStackTrace();
        }
        return fileContent;
    }
}

        ```
    </div>
    <div class="tab csharp-tab">
```c
        using System;
using System.IO;
using FusionCharts.FusionExport.Client; // Import sdk

namespace FusionExportTest
{
    class Program
    {
        static void Main(string[] args)
        {
            // Instantiate the ExportConfig class and add the required configurations
            ExportConfig exportConfig = new ExportConfig();
            exportConfig.Set("chartConfig", File.ReadAllText("fullpath/of/chart-config-file.json"));

            // Instantiate the ExportManager class
            ExportManager em = new ExportManager();
            // Call the Export() method with the export config and the respective callbacks
            em.Export(exportConfig, OnExportDone, OnExportStateChanged);
        }
        
        // Called when export is done
        static void OnExportDone(string result, ExportException error)
        {
            if(error != null)
            {
                Console.WriteLine("Error: " + error);
            } else
            {   
                Console.WriteLine("Done: " + result); // export result
            }
        }
        
        // Called on each export state change
        static void OnExportStateChanged(string state)
        {
            Console.WriteLine("State: " + state);
        }
    }
}

        ```
    </div>
    <div class="tab php-tab">
```php
        <?php

// Exporting a chart

require __DIR__ . '/../vendor/autoload.php';

// Use the sdk
use FusionExport\ExportManager;
use FusionExport\ExportConfig;

// Instantiate the ExportConfig class and add the required configurations
$exportConfig = new ExportConfig();
$exportConfig->set('chartConfig', file_get_contents('resources/single.json'));

// Called on each export state change
$onStateChange = function ($state) {
  echo('STATE: [' . $state->reporter . '] ' . $state->customMsg . "\n");
};

// Called when export is done
$onDone = function ($export, $e) {
    if ($e) {
        echo('ERROR: ' . $e->getMessage());
    } else {
        foreach ($export as $file) {
            echo('DONE: ' . $file->realName . "\n");
            copy($file->tmpPath, $file->realName);
        }
    }
};

// Instantiate the ExportManager class
$exportManager = new ExportManager();
// Call the export() method with the export config and the respective callbacks
$exportManager->export($exportConfig, $onDone, $onStateChange);

        ```
    </div>
    <div class="tab python-tab">
```python
        #!/usr/bin/env python

from fusionexport import ExportManager, ExportConfig  # Import sdk


def read_file(file_path):
    try:
        with open(file_path, "r") as f:
            return f.read()
    except Exception as e:
        print(e)


# Called when export is done
def on_export_done(result, error):
    if error:
        print(error)
    else:
        print(result)


# Called on each export state change
def on_export_state_changed(state):
    print(state)


# Instantiate the ExportConfig class and add the required configurations
export_config = ExportConfig()
export_config["chartConfig"] = read_file("chart-config-file.json")

# Instantiate the ExportManager class
em = ExportManager()
# Call the export() method with the export config and the respective callbacks
em.export(export_config, on_export_done, on_export_state_changed)

        ```
    </div>
    <div class="tab golang-tab">
```javascript
        // Exporting a chart

package main

import (
    "io/ioutil"
    "../FusionExport" // import the sdk
    "fmt"
)

func saveFiles(fileBag []FusionExport.OutFileBag) {
    for _, file := range fileBag {
        fmt.Println(file.RealName)
        fileData, err := ioutil.ReadFile(file.TmpPath)
        check(err)
        err = ioutil.WriteFile(file.RealName, fileData, 0644)
        check(err)
    }
}

// Called when export is done
func onDone (outFileBag []FusionExport.OutFileBag, err error) {
    check(err)
    saveFiles(outFileBag)
}

// Called on each export state change
func onStateChange (event FusionExport.ExportEvent) {
    fmt.Println("[" + event.Reporter + "] " + event.CustomMsg)
}

func main() {
    // Instantiate ExportConfig and add the required configurations
    exportConfig := FusionExport.NewExportConfig()

    chartConfig, err := ioutil.ReadFile("resources/single.json")
    check(err)
    exportConfig.Set("chartConfig", string(chartConfig))

    // Instantiate ExportManager
    exportManager := FusionExport.NewExportManager()
    // Call the Export() method with the export config and the respective callbacks
    exportManager.Export(exportConfig, onDone, onStateChange)
}

func check(e error) {
    if e != nil {
        panic(e)
    }
}
        ```
    </div>
</div>