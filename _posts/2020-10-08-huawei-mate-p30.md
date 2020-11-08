---
title: 'Подготовка Huawei P30 Pro к использованию'
tags: 
    - Huawei
categories:
    - телефон
sources:
    - https://4pda.ru/forum/index.php?showtopic=916789&st=24820#entry88488013
    - https://forum.xda-developers.com/mate-20-pro/how-to/guide-remove-huawei-bloatware-noob-t3889426
    - https://android.stackexchange.com/questions/28767/view-apps-full-package-name
---

### Необходимо
* [Android Debug Bridge](https://developer.android.com/studio/releases/platform-tools.html)

### Удаление мусора
```
./adb shell cmd package uninstall -k --user 0 com.huawei.android.mirrorshare
./adb shell cmd package uninstall -k --user 0 com.huawei.android.totemweather
./adb shell cmd package uninstall -k --user 0 com.huawei.compass
./adb shell cmd package uninstall -k --user 0 com.huawei.hidisk
./adb shell cmd package uninstall -k --user 0 com.huawei.phoneservice
./adb shell cmd package uninstall -k --user 0 com.huawei.mirror
./adb shell cmd package uninstall -k --user 0 com.huawei.vassistant
./adb shell cmd package uninstall -k --user 0 com.huawei.search
./adb shell cmd package uninstall -k --user 0 com.android.mediacenter
./adb shell cmd package uninstall -k --user 0 com.huawei.appmarket
./adb shell cmd package uninstall -k --user 0 com.android.email
./adb shell cmd package uninstall -k --user 0 com.microsoft.translator
./adb shell cmd package uninstall -k --user 0 com.touchtype.swiftkey
./adb shell cmd package uninstall -k --user 0 com.swiftkey.swiftkeyconfigurator
./adb shell cmd package uninstall -k --user 0 com.android.providers.partnerbookmarks
./adb shell cmd package uninstall -k --user 0 com.facebook.appmanager
./adb shell cmd package uninstall -k --user 0 com.facebook.katana
./adb shell cmd package uninstall -k --user 0 com.facebook.services
./adb shell cmd package uninstall -k --user 0 com.facebook.system
./adb shell cmd package uninstall -k --user 0 com.google.android.gm 
./adb shell cmd package uninstall -k --user 0 com.google.android.partnersetup
./adb shell cmd package uninstall -k --user 0 com.huawei.health
./adb shell cmd package uninstall -k --user 0 com.huawei.himovie.overseas
./adb shell cmd package uninstall -k --user 0 com.huawei.parentcontrol
./adb shell cmd package uninstall -k --user 0 com.hicloud.android.clone
./adb shell cmd package uninstall -k --user 0 com.android.calendar
./adb shell cmd package uninstall -k --user 0 com.android.egg 
./adb shell cmd package uninstall -k --user 0 com.huawei.android.hwaps
```

### Список пакетов
```
adb shell "pm list packages" 
```