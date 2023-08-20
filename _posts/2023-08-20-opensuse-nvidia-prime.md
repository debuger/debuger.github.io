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
---

### Описание
Для полноценной работы nvidia prime - запускаем систему с prime-select в offroad
`# prime-select boot offroad`,
 а приложения запускаем с переменными окружения
`__NV_PRIME_RENDER_OFFLOAD=1 __GLX_VENDOR_LIBRARY_NAME=nvidia`.
В результате при обычной работе видеокарта не работает и подключается только по необходимости.
