---
title: 'Запуск XCOM2 под opensuse'
tags: 
    - Игры
    - XCOM2
    - opensuse
categories:
    - games
sources:
---

### Необходимо

* XCOM2 сборка под Linux
* Дополнительные пакеты 

### Пошагово

* Находим сборку XCOM2 под Linux (тестировалось на XCOM2 v1.2.3)
* скачаиваем пакеты
```
libSDL2-2_0-0-2.0.8-150200.11.6.1.x86_64.rpm
libSDL2_ttf-2_0-0-2.0.15-bp154.1.126.x86_64.rpm
libSDL2_image-2_0-0-2.0.5-1.60.x86_64.rpm
libldap-legacy-2.4.46-1.1.x86_64.rpm
libldap-2_4-2-2.4.46-150200.14.5.1.x86_64.rpm
libcurl4-7.79.1-150400.3.1.x86_64.rpm
libopenssl1_0_0-1.0.2p-3.49.1.x86_64.rpm
```
* распаковываем содержимое rpm в `XCOM2/lib`
* запускаем и играем
