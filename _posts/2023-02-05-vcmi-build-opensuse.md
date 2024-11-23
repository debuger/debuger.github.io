---
title: 'Сборка VCMI под opensuse'
tags: 
    - Игры
    - HOMM3
    - VCMI
categories:
    - games
updated: 23.11.2020T22:00:00
sources:
    - https://vcmi.eu/developers/Building_Linux/
    - https://wiki.vcmi.eu/Installation_on_Linux
    - https://github.com/vcmi/vcmi
---

### Необходимо

* Исходные данные из HOMM3
* Исходные коды для VCMI
* Установка необходимых пакетов для сборки
* Дополнительные пакеты 

### Пошагово

* скачиваем с https://github.com/vcmi/vcmi/releases последний релиз
* распаковываем в соотвествии с инструкцией
```
.
├── vcmi-1.5.7 
└── build
```
* устанавливаем зависимости для сборки
```
zypper in cmake libSDL2-devel libSDL2_image-devel libSDL2_ttf-devel libSDL2_mixer-devel zlib-devel  libavformat-devel libswscale-devel libavresample-devel libswresample-devel libboost_atomic1_75_0-devel libboost_program_options1_75_0-devel libboost_filesystem1_75_0-devel libboost_system1_75_0-devel libboost_thread1_75_0-devel libboost_locale1_75_0-devel libboost_iostreams1_75_0-devel libboost_iostreams1_75_0 tbb-devel libQt5Widgets-devel libQt5Core-devel libQt5Gui-devel libQt5Network-devel minizip-devel libqt5-linguist libqt5-linguist-devel ffmpeg-7-libavcodec-devel ffmpeg-7-libavdevice-devel ffmpeg-7-libavutil-devel ffmpeg-7-libswscale-devel ffmpeg-7 gcc-14 gcc14-c++
```
* скачиваем дополнительные пакеты 
```
https://www.fuzzylite.com/downloads/
```
* копируем дополнительыне пакеты
```
fuzzylite-6.0.zip/fuzzylite > vcmi-1.1.1/AI/FuzzyLite
```
* настраиваем
```
cd build
CC=/usr/bin/gcc-14 CXX=/usr/bin/g++-14 cmake ../vcmi-1.5.7
```
* собираем
```
CC=/usr/bin/gcc-14 CXX=/usr/bin/g++-14 cmake --build . -- -j4
```
* ставим
```
sudo CC=/usr/bin/gcc-14 CXX=/usr/bin/g++-14 cmake --install .
```
* ставим data файлы из оригинальных HOMM3
* ностальгируем