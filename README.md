# MagTek uDynamo Card Reader Plugin #

Allow using the MagTek uDynamo Card Reader with PhoneGap apps

Installation
------------

Install the plugin using CLI

```
cordova plugin add https://github.com/pickupman/CardReaderPlugin.git
```

Methods
-------

clearCardData(successCallback, errorCallback)

closeDevice(successCallback, errorCallback)

getCardExpDate(successCallback, errorCallback)

getCardIIN(successCallback, errorCallback)

getCardLast4(successCallback, errorCallback)

getCardName(successCallback, errorCallback)

getCardServiceCode(successCallback, errorCallback)

getCardStatus(successCallback, errorCallback)

getDeviceSerial(successCallback, errorCallback)

getMagnePrint(successCallback, errorCallback)

getMagnePrintStatus(successCallback, errorCallback)

getSessionID(successCallback, errorCallback)

getTrackDecodeStatus(successCallback, errorCallback)

getTrack1(successCallback, errorCallback)

getTrack1Masked(successCallback, errorCallback)

getTrack2(successCallback, errorCallback)

getTrack2Masked(successCallback, errorCallback)

getTrack3(successCallback, errorCallback)

getTrack3Masked(successCallback, errorCallback)

isDeviceConnected(successCallback, errorCallback)

isDeviceOpened(successCallback, errorCallback)

listenForEvents(successCallback, errorCallback)

openDevice(successCallback, errorCallback)

setDeviceProtocolString(successCallback, errorCallback)

setDeviceType(successCallback, errorCallback)


Usage
-----

Initialize the reader in your controller by the window object

```
window.cordova.plugins.MagTek.openDevice(function(device) {

}, function(error) {

});
```

While card reader is connected, wait for a swipe event to occur
```
window.cordova.plugins.MagTek.listenForEvents(function(card_data) {

}, function(error) {

});
```

## Troubleshooting ##

Android
-------

Make sure the volume is set to max volume. The card reader is read as microphone input.
Volume needs raised to be able to detect audio signal from the reader.


iOS
---

Do to the way the Magtek SDK for the uDynamo is provided, it has two different libraries based on
 on the way the build environment. This plugin includes the library for the live (device) build.
 You will not be able to run your app from the iOS simulator. In order to successfully build your
 app with the ionic / cordova CLI, you must using the following syntax:

 ```
 cordova build ios --device
 // or
 ionic build ios --device
 ```

 Then you can install the app, by using Xcode to push to an actual device, or using the appropriate
 CLI command. Failure to build the app with those arguments will cause the build to FAIL.
