---
title: 'Установка ПО из исходных кодов в opensuse'
tags: 
    - 'opensuse'
    - 'zypper'
categories:
    - 'opensuse'
    - 'zypper'
sources:
    - https://unix.stackexchange.com/questions/231206/how-to-install-src-package-in-suse
    - https://en.opensuse.org/SDB:Zypper_usage
---

### Описание
Периодически сталкивался с проблемой - версия собранного пакета в репозитории ниже, чем версия пакета для установки из исходных кодов.
Выполнение комманды `zypper si ...` ничего не выполняет - пакет все рвно не установлен. Решение было найдено на просторах интернета
```
sudo zypper -v si --no-recommends --no-build-deps <package>
sudo rpmbuild -ba /usr/src/packages/SPECS/<package>.spec
sudo rpm -ivh /usr/src/packages/RPMS/x86_64/<package>-<version>.rpm
```

Для успешной сборки и установки необходим  пакет `rpm-tools`.
