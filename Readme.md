# Bypass ssl in android apps
Bypass ssl in android application to sniff https traffic

<p align="center">
  <img width="300" height="300" src="https://developer.android.com/guide/practices/ui_guidelines/images/NB_Icon_Mask_Shapes_Ext_02.gif" />
</p>

## Requirements
- Windows
- preferably rooted android device
- Python 3.6 and above

## Steps
- Install libraries below
```
pip3 install frida-tools objection
pip install adb
```
- Connect your phone to your device
- Download frida server matching with android architecture(for me: arm64) in https://github.com/frida/frida/releases. Replace "frida-server-15.1.22-android-arm64" with your file name

```
adb push frida-server-15.1.22-android-arm64 "/data/local/tmp"
adb shell "chmod 755 /data/local/tmp/frida-server-15.1.22-android-arm64"
adb shell setenforce 0
```

- Start frida server in another terminal tab. Replace "frida-server-15.1.22-android-arm64" with your file name
```
adb shell
su
"/data/local/tmp/frida-server-15.1.22-android-arm64"
```

- Launch the application you wanted to intercept and run this command to display the processes of the app
```
frida-ps -U
```
- Once u find the application, run process number or the name. Replace "appname" with your application name or pid
```
objection --gadget appname explore
```
- Remove sslpinning in the specifed app
```
android sslpinning disable
```
- After you've done. Use `Charles`, `BurpSuite` or any other tooling for request sniffing.

## Side note
- If you want Charles proxy license, you can buy me a coffee in https://www.buymeacoffee.com/bnityanantZ and leave your email in the message privately.


## Disclaimer
This repo was created for educational purposes only. Use it on your own risk.  


## Buy me a coffee
If You'd like to thank me you can buy me a coffee. coffee is never too much :)

https://www.buymeacoffee.com/bnityanantZ

