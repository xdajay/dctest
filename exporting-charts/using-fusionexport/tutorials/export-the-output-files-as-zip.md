---
permalink: exporting-charts/using-fusionexport/tutorials/export-the-output-files-as-zip.html
title: Export the output files as a zip | FusionCharts
description: This article talks about the SDKs used for exporting output files as a zip.
heading: Export the output files as a zip
chartPresent: False
---

For exporting the output files as a zip, set `--exportAsZip` option to __true__.
To do this, you can use the CLI or SDKs of the languages mentioned below, using the command given below:

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
    <div>If you want to export the files as a zip, set the <strong>--output-as-zip</strong> option to true as shown in the command below:</div>
```javascript
        $ fe -c multiple_charts_config.json -z false
        ```
    </div>
    
    <div class="tab nodejs-tab">
```javascript
        const fs = require('fs');
const path = require('path');

// require fusionexport
const FusionExport = require('../');

const chartConfig = JSON.parse(fs.readFileSync(path.resolve(__dirname, 'bulk.json')).toString());
const host = '127.0.0.1';
const port = 1337;

// instantiate FusionExport
const fusion = new FusionExport({ host, port });

const exportConfig = {
  chartConfig,
  exportAsZip: 'true',
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
        config.set("chartConfig", readFile("fullpath/of/bulk.json"));
        config.set("exportAsZip", "true");

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
            exportConfig.Set("chartConfig", File.ReadAllText("fullpath/of/bulk.json"));
            exportConfig.Set("exportAsZip", "true");

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

// Exporting the Output Files as Zip

require __DIR__ . '/../vendor/autoload.php';

// Use the sdk
use FusionExport\ExportManager;
use FusionExport\ExportConfig;

// Instantiate the ExportConfig class and add the required configurations
$exportConfig = new ExportConfig();
$exportConfig->set('chartConfig', file_get_contents('resources/multiple.json'));
$exportConfig->set('exportFile', 'php-export-<%= number(5) %>');
$exportConfig->set('exportAsZip', true);

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
export_config["chartConfig"] = read_file("bulk.json")
export_config["exportAsZip"] = True

# Instantiate the ExportManager class
em = ExportManager()
# Call the export() method with the export config and the respective callbacks
em.export(export_config, on_export_done, on_export_state_changed)

        ```
    </div>
    <div class="tab golang-tab">
```javascript
        // Exporting the Output Files as Zip

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

    chartConfig, err := ioutil.ReadFile("resources/multiple.json")
    check(err)
    exportConfig.Set("chartConfig", string(chartConfig))
    exportConfig.Set("exportFile", "go-export-<%= number(5) %>")
    exportConfig.Set("exportAsZip", "true")

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