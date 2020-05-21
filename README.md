# EsptouchPython
A python script to implement the Esptouch protocol on platforms other than iOS or Android 

I needed to generate the Esptouch protocol from an embedded system, not from a smart device. Since I could not find anything suitable anywhere I wrote this. Pretty impressed with the size of this script vs the size of the objective-c or Java versions.

This script does not have a listener like the smart apps have. There is no confirmation of any sort if a device connect correctly after receiving the smartconfig data. This script only broadcast the data in the air and hope for the best. You can always make a prayer before launching it...

## Usage
ESPTouch.py \[ssid\] \[password\] \[broadcast T/F\] \[returnIP\] \[bssid\]

The broadcast True or False , if true will send all group of packets at 255.255.255.255. If false will send multicast sequentially 234.XXX.XXX.XXX like defined in the protocol. I assume this feature is for if your router does not forward multicast.  
The return IP value doesnt matter as we do not listen back (you need however to provide one).

**Examples:**  
ESPTouch.py NARNIA w4rdr0b3 F 192.168.1.222 abcdef0102ff  
ESPTouch.py NARNIA w4rdr0be T 192.168.1.1 000000000000

## Personal Notes
* The timing in the android app are differents from the ones in the iOS version and it does not seem to matter. In the article "ESP-TOUCH decoding and encoding rules" the person seems puzzled that the Android versions sends less packet groups than the iOS; I think that it's just that the java code execute slower than obj-c on iOS.

* In the iOS version, there is a concept of not sending the ssid if it is hidden but it is totally omitted in the android version. So I omitted it here since I was never able to make it work properly without an ssid in the messages.

* The bssid seems to be superfluous, if I just send 000000000000 as a mac address or if I totally omit to inject them in the stream of data, the process works correctly anyway ???

* With the multicast option the system that runs the script does not needs to be connected by wifi, as long as it is the same subnet.

## References
[EsptouchForAndroid](https://github.com/EspressifApp/EsptouchForAndroid)

[EsptouchForIOS](https://github.com/EspressifApp/EsptouchForIOS)

[ESP-TOUCH decoding and encoding rules](http://programmersought.com/article/30242322446/;jsessionid=8670B066FC7F10A1F5345072E44AC52A)

[Original ESP-TOUCH decoding and encoding rules](https://blog.csdn.net/flyingcys/article/details/54670688)

[CRC8 Maxim/Dallas](https://gist.github.com/eaydin/768a200c5d68b9bc66e7)

[CRC Calc](https://crccalc.com/)

