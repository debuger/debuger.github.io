---
title: 'Подготовка USB flash для использования в embedded device'
tags: 
    - embed
    - fat32
    - mkfs
categories:
    - blog
sources:
    - https://debbuger.blogspot.com/2016/06/usb-flash-embedded-device.html
---
Большинство устройств поддерживающих внешние накопители используют FAT32 в качестве ФС. Для корректного использования USB flash в embedded устройствах необходимо создать старый добрый DOS раздел безо всяких GPT и primary fat32 раздела:

```
> /fdisk/sdx
```

* o (create a new empty DOS partition table) =>
* n (add a new partition) p => 
* t (change a partition type) 0c =>
* w (write table to disk and exit)

```
> mkfs.vfat -F 32 /dev/sdxN
```

И вуаля - можно использовать