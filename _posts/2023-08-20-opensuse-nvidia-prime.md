---
title: 'Использование NVIDIA Prime в opensuse'
tags: 
    - opensuse
    - nvidia
categories:
    - nvidia
    - opensuse
sources:
    - https://download.nvidia.com/XFree86/Linux-x86_64/435.21/README/primerenderoffload.html
    - https://en.opensuse.org/SDB:NVIDIA_SUSE_Prime
updated: 01.03.2024T21:30:00
---

### Описание
Для полноценной работы nvidia prime - запускаем систему с prime-select в offroad
`# prime-select boot offroad`,
 а приложения запускаем с переменными окружения
`__NV_PRIME_RENDER_OFFLOAD=1 __GLX_VENDOR_LIBRARY_NAME=nvidia`.
В результате при обычной работе видеокарта не работает и подключается только по необходимости.

### Обновлено
Можно создать в папке `~/bin` скрипт запуска `prime-run` и запускать приложение через данный скрипт `prime-run vlc`

### prime-run
```
#!/bin/bash
DRI_PRIME=pci-0000_01_00_0 __NV_PRIME_RENDER_OFFLOAD=1 __VK_LAYER_NV_optimus=NVIDIA_only __GLX_VENDOR_LIBRARY_NAME=nvidia  LIBVA_DRIVER_NAME=nvidia "$@"
```