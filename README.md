<a href="https://www.tindie.com/products/squarofumi/badgy-iot-badge/"><img src="https://d2ss6ovg47m0r5.cloudfront.net/badges/tindie-larges.png" alt="I sell on Tindie" width="200" height="104"></a>

<img src="/website/img/badgytechnical.jpg" />

# Know Your Badgy

Since launching the first revision of Badgy, we have made various updates and fixes to the hardware and design. Refer to the diagram below to know which revision of Badgy you have. This is helpful for getting started and troubleshooting.

<img src="/website/img/badgy_rev.jpg" />

### Rev 2B

This is the latest revision of Badgy (May 2019) and can be uniquley identified by the small green PCB on the bottom left corner. It supports programming over USB (updated from CH340 to CP2104, woohoo!) and WiFi OTA. It fixes the battery issue with Rev 2A.

### Rev 2A

This revision of Badgy adds USB programming capability with the CH340 USB-UART controller. It also has two additional jumper pads: 1) ADC broken out if you choose to measure the battery voltage 2) jumper pad for driving other E-ink displays (e.g. 2.13" flexible E-ink). This version has a hardware bug that causes Badgy to not work on battery power, full description with hacks/fixes described here https://github.com/sqfmi/badgy/issues/20.

### Rev 1

This is the original and first revision of Badgy. It only supports firmware uploading via WiFi OTA, but the programming pads are broken out so you could also use your own USB-Serial adapter.

# Getting Started

By default your Badgy displays the welcome message when powered on. To upload new firmware, you can simply connect via USB **(Rev 2A/2B)**, or to your WiFi network **(Rev 1/2A/2B)**.

## Over USB (for Rev 2A & Rev 2B)
1. Download and install the latest version of Arduino IDE
2. Install board support for the ESP8266 using the Arduino Board Manager using instructions found [here](https://github.com/esp8266/Arduino#installing-with-boards-manager).
3. If you are using a windows machine then you need to add support for the CP201X by installing drivers from [here](https://www.silabs.com/community/interface/knowledge-base.entry.html/2016/12/30/downloading_cp210xd-ek07).
4. The USB-Serial device should show up on the list of ports (e.g. COM8, /dev/cu.\* , /dev/tty.\*).  If you don't see it then it is possible that you need to install the drivers for CP2014 on your system.
5. From Tools -> Board choose "NodeMCU 1.0 (ESP-12E Module)".
6. Compile and upload one of our code samples, or create your own!  See the 'compiling' section below for some details.

Note that if the ESP chip is in a deep sleep then it will not automatically respond to the upload request and you may see something like "error: espcomm open failed" when trying to upload.  A manual restart of the ESP chip, using the power slide button, just prior to upload gives you a small window of time to upload.

## Over WiFi
1. Power your Badgy through USB or a rechargeable battery, or both. Make sure the power switch is in the off position (up)
2. Hold down the center button and slide the power switch on (down). **Note: On older firmware versions it is not necessary to hold down the center button and OTA is on by default**
3. The screen should now update letting you know to connect to the "Badgy AP" network. You can now let go of the center button
4. Using your mobile phone, connect to the "Badgy AP" WiFi network
5. Follow the captive portal instructions to select your desired WiFi connection
6. Once connected, Badgy is ready to receive new firmware! Go to http://*YOUR_IP_ADDRESS*:8888/update to upload your new firmware
7. WiFi credentials are automatically saved onboard, your Badgy will automatically connect to your selected network the next time you perform an update

**WARNING: The battery charging IC does not have reverse polarity protection! Check the polarity before inserting the battery, and make sure you are using a rechargeable LiPo battery (LIR2450 coin cell or 1S LiPo). Other batteries such as the CR2032 will not work**

Check out the examples folders for various code samples, we're constantly adding more!

## Compiling examples
The readme files within the example directories contain specific library and version information for that example.   At a minimum though you should consider installing the following libraries as they are very useful and/or necessary for any real functionality.

1. GxEPD library: you can find the repo [here](https://github.com/ZinggJM/GxEPD).  It can also be found in the Library Manager under GxEPD.  Do not download GxEPD2.
2. AdaFruit GFX library: installation instructions available [here](https://learn.adafruit.com/adafruit-gfx-graphics-library/overview).  Also can be found in the Library Manager under Adafruit_GFX.
3. WifiManager library: you can find the repo [here](https://github.com/tzapu/WiFiManager).  You can also find this in the Library Manager under 'WiFiManager by tzapu'.
4. Time library: you can find the repo [here](https://github.com/PaulStoffregen/Time).    I was NOT able to find this in the Library Manager.
5. ArduinoJson library: you can find the repo [here](https://github.com/bblanchon/ArduinoJson). You can also find this in the Library Manager under 'ArduinoJson by Benoit Blanchon'.   Make sure that you install a 5.x version since some of the examples require that.
