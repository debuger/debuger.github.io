---
title: 'С чего все началось'
tags: 
    - jekyll
    - gitpages
categories:
    - blog
updated: 11.11.2020T22:00:00
sources:
    - https://jekyllrb.com/
    - https://pages.github.com/
    - https://www.sylvaindurand.org/making-jekyll-multilingual/
    - https://jekyllthemes.io/
    - https://habr.com/ru/post/336266/
    - https://github.com/mojombo/mojombo.github.io
    - https://github.com/jgthms/html-reference
---
Все началось как pet проект - хотелось найти примитивный blog-engine с некоторыми условиями:
* open-source с возможностью допиливания под свои нужды
* неплохая документация для возможности быстрого допиливания под свои нужды
* возможность добавления записей в markdown
* возможность редактирования даже с "утюга" или , в крайнем случае, с "холодильника"
* возможность "быстрого старта", без особых костылей


В результате поиска найдено было найдено только одно подходящее решение -  [jekyll](https://jekyllrb.com/) в связке с [github pages](https://pages.github.com/).

Для быстрого старта был использован docker [образ](https://hub.docker.com/u/jekyll) в проекте вида:

```
.
├── docker
│   ├── docker-compose.yml
│   ├── .env
└── src
    ├── _config.yml
    ├── _drafts
    ├── Gemfile
    ├── _includes
    ├── index.html
    ├── _layouts
    ├── _posts
```

Необходимыми для старта были файлы:
* `docker/docker-compose.yml` 

```
version: "3.2"
services:
  jekyll:
    image: jekyll/builder:3.8
    volumes:
      - ${PWD}/../src/:/srv/jekyll
      - jekill_cache:/usr/local/bundle
      - tmp:/tmp
    entrypoint:
      - jekyll
      - serve
    env_file:
    - .env
volumes:
  tmp:
    driver_opts:
      type: bind
      o: bind
      device: "/tmp"
  jekill_cache:
    driver_opts:
      type: bind
      o: bind
      device: ${PWD}/gemcache
```

* `docker/.env`

```
JEKYLL_UID=1000 //id -u
JEKYLL_GID=100 // id -g
JEKYLL_GITHUB_TOKEN= //github token for github pages
PROJECT_NAME=PN // some name
COMPOSE_PROJECT_NAME=PN // as I remember the same name
DOCKER_COMPOSE_ARGS=--file docker-compose.yml -p PN // the same
```

* `src/Gemfile`

```
source 'https://rubygems.org'
gem "github-pages", group: :jekyll_plugins
```

При помощи данной начальной настройки была возможность вести свой блог без особых затрат в формате `markdown`.