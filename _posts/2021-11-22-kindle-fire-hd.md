---
title: 'Подготовка Kindle Fire HD (2019) к нормальному использованию'
tags: 
    - Kinlde Fire
categories:
    - Kindle
sources:
    - https://4pda.ru/forum/index.php?showtopic=973800&st=900#entry102738225
    - https://www.androidpolice.com/2020/12/25/install-play-store-amazon-fire-tablet/
    - https://www.androidpolice.com/2020/07/23/how-to-make-your-amazon-fire-tablet-feel-more-like-stock-android/
---

### Необходимо
* [Android Debug Bridge](https://developer.android.com/studio/releases/platform-tools.html)


### Обновляемся

Используя стандартные настройки обновляем систему до последней доступно версии.

### Установка Google Services

Скачиваем по ссылкам и устанавливаем:
* GOOGLE ACCOUNT MANAGER
* GOOGLE SERVICES FRAMEWORK
* GOOGLE PLAY SERVICES
* GOOGLE PLAY STORE

```
./adb install "com.google.android.gsf_9-6475783-28_minAPI28(nodpi)_apkmirror.com.apk"
./adb install "com.google.android.gsf.login_7.1.2-25_minAPI23(nodpi)_apkmirror.com.apk"
./adb install "com.google.android.gms_20.50.66_(100400-351698872)-205066028_minAPI28(arm64-v8a,armeabi-v7a)(nodpi)_apkmirror.com.apk"
./adb install "com.android.vending_23.9.24-21_0_PR_355187674-82392410_minAPI21(armeabi-v7a,x86,x86_64)(nodpi)_apkmirror.com.apk"
```

### Установка альтернативного лаунчера

* Логинимся в Play Market
* Обновляемся
* Устанавливаме `Launchair 2`
* Включаем как лаунчер по умолчанию


```
./adb shell pm set-home-activity ch.deletescape.lawnchair.plah/ch.deletescape.lawnchair.LawnchairLauncher && \
./adb shell am force-stop com.amazon.firelauncher && ./adb shell pm disable-user --user 0 com.amazon.firelauncher
```

### Убираем все лишнее

```
./adb shell am force-stop com.amazon.photos && ./adb shell pm disable-user --user 0 com.amazon.photos && \
./adb shell am force-stop com.amazon.windowshop && ./adb shell pm disable-user --user 0 com.amazon.windowshop && \
./adb shell am force-stop com.amazon.iris && ./adb shell pm disable-user --user 0 com.amazon.iris && \
./adb shell am force-stop com.amazon.webapp && ./adb shell pm disable-user --user 0 com.amazon.webapp && \
./adb shell am force-stop com.amazon.ods.kindleconnect && ./adb shell pm disable-user --user 0 com.amazon.ods.kindleconnect && \
./adb shell am force-stop com.amazon.kindle.kso && ./adb shell pm disable-user --user 0 com.amazon.kindle.kso && \
./adb shell am force-stop com.amazon.mp3 && ./adb shell pm disable-user --user 0 com.amazon.mp3 && \
./adb shell am force-stop com.amazon.kindle && ./adb shell pm disable-user --user 0 com.amazon.kindle && \
./adb shell am force-stop com.amazon.avod && ./adb shell pm disable-user --user 0 com.amazon.avod && \
./adb shell am force-stop com.audible.application.kindle && ./adb shell pm disable-user --user 0 com.audible.application.kindle && \
./adb shell am force-stop com.amazon.tahoe && ./adb shell pm disable-user --user 0 com.amazon.tahoe && \
./adb shell am force-stop com.washingtonpost.rainbow && ./adb shell pm disable-user --user 0 com.washingtonpost.rainbow && \
./adb shell am force-stop com.amazon.kindle.kso && ./adb shell pm disable-user --user 0 com.amazon.kindle.kso
```

```
./adb shell pm disable-user --user 0 com.goodreads.kindle && \
./adb shell pm disable-user --user 0 com.android.music && \
./adb shell pm disable-user --user 0 com.amazon.kindle.personal_video && \
./adb shell pm disable-user --user 0 com.amazon.photos.importer && \
./adb shell pm disable-user --user 0 com.kingsoft.office.amz && \
./adb shell pm disable-user --user 0 com.amazon.advertisingidsettings && \
./adb shell pm disable-user --user 0 com.amazon.kor.demo && \
./adb shell pm disable-user --user 0 com.android.protips && \
./adb shell pm disable-user --user 0 com.amazon.kindle.otter.oobe && \
./adb shell pm disable-user --user 0 com.android.calculator2 && \
./adb shell pm disable-user --user 0 com.android.contacts && \
./adb shell pm disable-user --user 0 com.amazon.zico && \
./adb shell pm disable-user --user 0 com.android.email && \
./adb shell pm disable-user --user 0 com.amazon.alexa.youtube.app
```

```
./adb shell pm disable-user --user 0 com.amazon.cloud9 && \
./adb shell pm disable-user --user 0 com.amazon.cloud9.contentservice && \
./adb shell pm disable-user --user 0 com.amazon.weather && \
./adb shell pm disable-user --user 0 com.amazon.dp.contacts && \
./adb shell pm disable-user --user 0 com.amazon.dp.fbcontacts && \
./adb shell pm disable-user --user 0 com.android.deskclock && \
./adb shell pm disable-user --user 0 com.amazon.smartgenie && \
./adb shell pm disable-user --user 0 com.amazon.kindle.otter.oobe.forced.ota && \
./adb shell pm disable-user --user 0 com.amazon.device.software.ota && \
./adb shell pm disable-user --user 0 com.amazon.device.software.ota.override
```