---
title: 'Сборка RetroArch в linux'
tags: 
    - 'RetroArch'
    - 'NES'
    - 'PSP'
    - 'retrogames'
categories:
    - 'RetroArch'
    - 'retrogames'
sources:
    - https://www.libretro.com/
    - https://docs.libretro.com/development/retroarch/compilation/ubuntu/
    - https://losst.pro/luchshie-emulyatory-dlya-linux
    - https://r-roms.github.io/
    - https://www.emulatorgames.net/
    - https://www.reddit.com/r/Roms/comments/rtfvnk/archiveorg_games/
    - https://github.com/zach-morris/plugin.program.iagl
---
### Сборка
* скачиваем последний релиз из https://github.com/libretro/RetroArch/releases
* распаковываем `tar -xf RetroArch-1.16.0.3.tar.gz`
* собираем 
```
cd RetroArch-1.16.0.3 && \
./configure && \
make clean && \
make -j4 && \
make install
```
* скачиваем assets для корректной работы из https://github.com/libretro/retroarch-assets/releases
* распаковываем `7za x assets.7z -o``readlink -f  ~/.config/retroarch/assets/`` `
* скачиваем cores из https://github.com/libretro/libretro-super/releases 
* распаковываем и собираем
```
tar -xf libretro-super-Latest.tar.gz && \
cd libretro-super-Latest && \
./libretro-fetch.sh parallel_n64 genesis_plus_gx snes9x mesens ppsspp && \
./libretro-build.sh parallel_n64 genesis_plus_gx snes9x mesens ppsspp && \
cp dist/unix/* `readlink -f  ~/.config/retroarch/cores/`
```

PS: assets и cores можно скачать прямо из retroacrh.