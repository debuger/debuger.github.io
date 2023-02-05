---
title: 'Сборка VCMI под opensuse'
tags: 
    - Игры
    - HOMM3
    - VCMI
categories:
    - games
sources:
    - https://wiki.vcmi.eu/How_to_build_VCMI_(Linux)
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
├── vcmi-1.1.1 
└── build
```
* устанавливаем зависимости для сборки
```
zypper in cmake libSDL2-devel libSDL2_image-devel libSDL2_ttf-devel libSDL2_mixer-devel zlib-devel  libavformat-devel libswscale-devel libavresample-devel libswresample-devel libboost_atomic1_66_0-devel libboost_program_options1_66_0-devel libboost_filesystem1_66_0-devel libboost_system1_66_0-devel libboost_thread1_66_0-devel libboost_locale1_66_0-devel tbb-devel libQt5Widgets-devel libQt5Core-devel libQt5Gui-devel libQt5Network-devel minizip-devel
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
cmake ../vcmi-1.1.1
```
* собираем
```
cmake --build . -- -j4
```
* ставим
```
sudo cmake --install .
```
* ставим data файлы из оригинальных HOMM3
* ностальгируем