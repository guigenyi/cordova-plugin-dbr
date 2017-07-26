# Cordova Plugin with Dynamsoft Barcode Reader for iOS and Android
================================
Use the Cordova plugin to quickly develop mobile barcode reader apps for iOS and Android.

## Installation
1. Install **Cordova** vi **npm**:

    ```  
        npm install -g cordova
    ```

2. Download the source code and add the plugin via local path:

    ```
        cordova plugin add <local-path>/cordova-plugin-dbr
    ```

   Or, install the plugin via repo url directly:
    ```
        cordova plugin add https://github.com/dynamsoft-dbr/cordova-plugin-dbr.git
    ```

## Supported Platforms

- iOS
- Android

## Supported Barcode Types ##
The following barcode types are currently supported:

* Code 39
* Code 93
* Code 128
* Codabar
* EAN-8
* EAN-13
* UPC-A
* UPC-E
* Interleaved 2 of 5 (ITF)
* Industrial 2 of 5 (Code 2 of 5 Industry, Standard 2 of 5, Code 2 of 5)
* ITF-14 
* QRCode
* DataMatrix
* PDF417

## Example

**index.html**

```html
<body>
        <div class="app">
            <div id="deviceready">
                <button id="scan">scan barcode</button>
            </div>
        </div>
        <script type="text/javascript" src="cordova.js"></script>
        <script type="text/javascript" src="js/index.js"></script>
    </body>
```

**index.js**

```js
   onDeviceReady: function() {
        document.getElementById("scan").onclick = function() {
                        cordova.plugins.barcodeScanner.scan(
                                                            function (result) {
                                                            alert("We got a barcode\n" +
                                                                  "Result: " + result.text + "\n" +
                                                                  "Format: " + result.format + "\n" +
                                                                  "Cancelled: " + result.cancelled);
                                                            },
                                                            function (error) {
                                                            alert("Scanning failed: " + error);
                                                            },
                                                            {
                                                            "preferFrontCamera" : false, // iOS and Android
                                                            "showFlipCameraButton" : true, // iOS and Android
                                                            }
                                                            );
                    }
        this.receivedEvent('deviceready');
    },
```

