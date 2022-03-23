<!--- Copyright (c) 2014 Spence Konde. See the file LICENSE for copying permission. -->
DHT22/AM230x/RHT0x Temperature and RH Sensor
=============================================

<span style="color:red">:warning: **Please view the correctly rendered version of this page at https://www.espruino.com/DHT22. Links, lists, videos, search, and other features will not work correctly when viewed on GitHub** :warning:</span>

* KEYWORDS: Module,DHT21,DHT22,DHT33,DHT44,RHT01,RHT02,RHT03,RHT04,RHT05,AM2301,AM2302,AM2303,HM2301,temperature,humidity

![DHT22 pins](DHT22/pins.jpg)

Check the [datasheet](/datasheets/DHT22.pdf) for further details.

Overview
---------

This module interfaces with the DHT22 (also DHT21, DHT22, DHT33, DHT44, RHT01, RHT02, RHT03, RHT04, RHT05, AM2301, AM2302, AM2303 and HM2301), an inexpensive temperature and relative humidity sensor similar to the [[DHT11]], but with higher accuracy and wider range. 

Key Specifications:

  |                   |          |
  |-------------------|----------|
  | Temperature Range | -40~80 C |
  | Temp. Accuracy    | +/- 0.5C |
  | Humidity Range    | 0 ~ 100% |
  | Humidity Accuracy | +/- 2%   |

The module supports setting a retry count which defaults to `1`.
If the module does not get any response after the specified number of retries, or if other sanity checks fail, an error is returned (see below), indicating a likely problem with the sensor or wiring.

The DHT22 is much more reliable than the [[DHT11]], and it rarely fails to provide data, however, it is still important to perform your own sanity checks on the data returned. 


Wiring
-----------------

From left to right when part is viewed from the front (the side with the ventilation holes) with pins pointing down. (The DHT22 has no pin markings). 

**IMPORTANT:** Be sure to get the polarity right! If connected backwards, it will ruin the DHT22. 

  | Device Pin | Espruino |
  |------------|----------|
  | 1 (Vcc)    | 3.3      |
  | 2 (S)      | Any GPIO |
  | 3 (NC)     | N/C*     |
  | 4 (GND)    | GND      |

**Note:** There are reports of DHT22s on the market where pins 3 and 4 are reversed. Meanwhile, app notes sometimes depict pins 2 and 3 tied together. 


Usage
-----

Call `require("DHT22").connect(pin)` to get a DHT22 object.

Call `read(callback, [retryCount])` on the object to read the sensor (`retryCount` on error defaults to 1).
The callback receives an object of the following form:
* if data was read completely, `{temp, rh}` (`temp`: temperature in °C, `rh`: relative humidity in %, `raw`: raw sensor reading).
* if no data was received: `{"temp": -1, "rh": -1, err : true, "checksumError": false}`.
* if some data is received, but the checksum is invalid, or the read timed out: `{"temp": -1, "rh": -1, err : true, "checksumError": true}`

In all cases, there is a `raw` field containing the received raw data as a string of `1` and `0` characters.

**Note:** 
Collecting period should be : >2 seconds.


Example:
--------

```JavaScript
var dht = require("DHT22").connect(C11);
dht.read(function (a) {console.log("Temp is "+a.temp.toString()+" and RH is "+a.rh.toString());});
```
* APPEND_USES: DHT22


Buying
------

DHT22 parts and modules can be purchased from many places:
* [eBay](http://www.ebay.com/sch/i.html?_nkw=DHT22&_sacat=92074)
* [digitalmeans.co.uk](https://digitalmeans.co.uk/shop/index.php?route=product/search&tag=dht22)
