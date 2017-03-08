# MagTek uDynamo Card Reader Plugin #

Allow using the MagTek uDynamo Card Reader with PhoneGap apps

Installation
------------

Install the plugin using CLI

```
cordova plugin add https://github.com/joseph-perez/CardReaderPlugin
```

Methods
-------

######clearCardData(successCallback, errorCallback)######

Clear data from device buffer

######closeDevice(successCallback, errorCallback)######

Turn off the device

######getCardExpDate(successCallback, errorCallback)######

Get the expiration date from a credit card

######getCardIIN(successCallback, errorCallback)######

Get ISO Issuer Identifier Number

######getCardLast4(successCallback, errorCallback)######

Get last 4 digits from a credit card

######getCardName(successCallback, errorCallback)######

Get the card holders name typically last name, first name

######getCardServiceCode(successCallback, errorCallback)######

######getCardStatus(successCallback, errorCallback)######

######getDeviceSerial(successCallback, errorCallback)######

Get serial number from card reader

######getMagnePrint(successCallback, errorCallback)######

######getMagnePrintStatus(successCallback, errorCallback)######

######getSessionID(successCallback, errorCallback)######

16 character string generated by device after a swipe

######getTrackDecodeStatus(successCallback, errorCallback)######

######getTrack1(successCallback, errorCallback)######

Get track 1 information in raw format

######getTrack1Masked(successCallback, errorCallback)######

Get track 1 information in decrypted format

######getTrack2(successCallback, errorCallback)######

Get track 2 information in raw format

######getTrack2Masked(successCallback, errorCallback)######

Get track 2 information in decrypted format

######getTrack3(successCallback, errorCallback)######

Get track 3 information in raw format

######getTrack3Masked(successCallback, errorCallback)######

Get track 3 information in decrypted format

######isDeviceConnected(successCallback, errorCallback)######

Returns true if device is currently open and connected

######isDeviceOpened(successCallback, errorCallback)######

Returns true if device is currently open/on

######listenForEvents(successCallback, errorCallback, events)######

Returns data after a swipe has occurred

######openDevice(successCallback, errorCallback)######

Open the device on the audio port

######setDeviceProtocolString(successCallback, errorCallback)######

######setDeviceType(successCallback, errorCallback)######


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

}, ['TRANS_EVENT_ERROR', 'TRANS_EVENT_OK', 'TRANS_EVENT_START'],
function(error) {

});
```

After processing card data, close the device to save battery life

```
window.cordova.plugins.MagTek.closeDevice(function(succes){

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
