---
## Front matter
title: "Лабораторная работа № 6"
subtitle: "Адресация IPv4 и IPv6. Настройка маршрутизации по протоколу RIP"
author: "Жукова София Виктровна"

## Generic otions
lang: ru-RU
toc-title: "Содержание"

## Bibliography
bibliography: bib/cite.bib
csl: pandoc/csl/gost-r-7-0-5-2008-numeric.csl

## Pdf output format
toc: true # Table of contents
toc-depth: 2
lof: true # List of figures
lot: true # List of tables
fontsize: 12pt
linestretch: 1.5
papersize: a4
documentclass: scrreprt
## I18n polyglossia
polyglossia-lang:
  name: russian
  options:
	- spelling=modern
	- babelshorthands=true
polyglossia-otherlangs:
  name: english
## I18n babel
babel-lang: russian
babel-otherlangs: english
## Fonts
mainfont: IBM Plex Serif
romanfont: IBM Plex Serif
sansfont: IBM Plex Sans
monofont: IBM Plex Mono
mathfont: STIX Two Math
mainfontoptions: Ligatures=Common,Ligatures=TeX,Scale=0.94
romanfontoptions: Ligatures=Common,Ligatures=TeX,Scale=0.94
sansfontoptions: Ligatures=Common,Ligatures=TeX,Scale=MatchLowercase,Scale=0.94
monofontoptions: Scale=MatchLowercase,Scale=0.94,FakeStretch=0.9
mathfontoptions:
## Biblatex
biblatex: true
biblio-style: "gost-numeric"
biblatexoptions:
  - parentracker=true
  - backend=biber
  - hyperref=auto
  - language=auto
  - autolang=other*
  - citestyle=gost-numeric
## Pandoc-crossref LaTeX customization
figureTitle: "Рис."
tableTitle: "Таблица"
listingTitle: "Листинг"
lofTitle: "Список иллюстраций"
lotTitle: "Список таблиц"
lolTitle: "Листинги"
## Misc options
indent: true
header-includes:
  - \usepackage{indentfirst}
  - \usepackage{float} # keep figures where there are in the text
  - \floatplacement{figure}{H} # keep figures where there are in the text
---

# Цель работы

Изучение принципов маршрутизации по протоколу RIP в IPv4- и IPv6-сетях и принципов настройки сетевого оборудования.


# Выполнение лабораторной работы

**Настройка динамической маршрутизации в сетях IPv4 и IPv6**

(рис. [-@fig:022]).

![man mc](image/22.jpeg){#fig:022 width=70%}

(рис. [-@fig:024]).

![man mc](image/24.png){#fig:024 width=70%}

(рис. [-@fig:025]).

![man mc](image/25.png){#fig:025 width=70%}


Запустим GNS3 VM и GNS3. Создадим новый проект, назовем его pr-gns3-rip. В рабочем пространстве разместим и соединим устройства в соответствии
с топологией, приведённой на рис. 6.1. Использем маршрутизаторы FRR.
Изменим отображаемые названия устройств. Коммутаторам присвойте названия по принципу msk-user-sw-0x, маршрутизаторам — по принципу
msk-user-gw-0x, VPCS — по принципу PCx-user, где вместо user укажем
имя вашей учётной записи, вместо x — порядковый номер устройства.
Включим захват трафика на соединении между коммутатором sw-01 и маршрутизатором gw-01, а также между коммутатором sw-02 и маршрутизатором gw-03. (рис. [-@fig:001]).

![новый проект](image/1.png){#fig:001 width=70%}

Присвоем IPv4-адреса оконечным устройствам PC1 и PC2 в соответствии с данными в табл. 6.2 (рис. [-@fig:002]).

![PC1](image/2.png){#fig:002 width=70%}

 (рис. [-@fig:003]).

![PC2](image/3.png){#fig:003 width=70%}

Настроим IPv4-адреса на интерфейсах маршрутизаторов (рис. [-@fig:004]).

![msk-user-gw-01](image/4.png){#fig:004 width=70%}

msk-user-gw-02 (рис. [-@fig:005]).

![msk-user-gw-02](image/5.png){#fig:005 width=70%}

Тоже самое для msk-user-gw-03 и msk-user-gw-04

Присвоим IPv6-адреса оконечным устройствам PC1 и PC2 в соответствии с данными в табл. 6.2 (рис. [-@fig:006]).

![PC1](image/6.png){#fig:006 width=70%}

PC2 (рис. [-@fig:007]).

![PC2](image/7.png){#fig:007 width=70%}

Настроим IPv6-адреса на интерфейсах маршрутизаторов(рис. [-@fig:008]).

![msk-user-gw-01](image/8.png){#fig:008 width=70%}

msk-user-gw-02 (рис. [-@fig:009]).

![msk-user-gw-02](image/9.png){#fig:009 width=70%}

Тоже самое для msk-user-gw-03 и msk-user-gw-04

**Настройка динамической маршрутизации по протоколу RIP.**

На маршрутизаторах настроим RIP в качестве протокола динамической маршрутизации (рис. [-@fig:010]).

![msk-user-gw-01](image/10.png){#fig:010 width=70%}

Убедимся, что маршрутизация по RIP настроена:(рис. [-@fig:011]).

![msk-user-gw-04](image/11.png){#fig:011 width=70%}

Проверим пути прохождения пакетов
– С PC1 пропингуйте PC2 и определите путь следования пакетов: (рис. [-@fig:012]).

![PC1](image/12.png){#fig:012 width=70%}

Предположим, что пакет проходит через маршрутизатор msk-user-gw-02. Отключим на маршрутизаторе msk-user-gw-02 интерфейс:(рис. [-@fig:013]).

![msk-user-gw-02](image/13.png){#fig:013 width=70%}

Проверьте метрики протокола RIP(рис. [-@fig:014]).

![msk-user-gw-01](image/14.png){#fig:014 width=70%}

Проверим пути прохождения пакетов:
– С PC1 пропингуйте PC2 и определите путь следования пакетов:(рис. [-@fig:015]).

![PC1](image/15.png){#fig:015 width=70%}

Предположим, что пакет проходит через маршрутизатор msk-user-gw-02. Отключим на маршрутизаторе msk-user-gw-02 интерфейс: (рис. [-@fig:016]).

![msk-user-gw-02](image/17.png){#fig:016 width=70%}

**Задание для самостоятельного выполнения**

Моделируемая сеть (рис. [-@fig:023]).

![сеть 2](image/23.png){#fig:023 width=70%}


Присвоим IPv4-адреса оконечным устройствам PC1 и PC2 в соответствии с данными в табл (рис. [-@fig:018]).

![PC1](image/18.png){#fig:018 width=70%}

Настроим IPv4/6-адреса на интерфейсах маршрутизаторов(рис. [-@fig:019]).

![msk-user-gw-01](image/19.png){#fig:019 width=70%}

На маршрутизаторах настроим RIP в качестве протокола динамической маршрутизации:(рис. [-@fig:020]).

![RIP](image/20.png){#fig:020 width=70%}

Проверим метрики протокола RIP: (рис. [-@fig:021]).

![метрики протокола RIP](image/21.png){#fig:021 width=70%}

# Выводы

Мы изучили принципы маршрутизации по протоколу RIP в IPv4- и IPv6-сетях и принципов настройки сетевого оборудования.

