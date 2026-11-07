---
## Front matter
title: "Лабораторная работа № 5"
subtitle: "Лабораторная работа: Aдресация IPv4 и IPv6. Настройка DHCP"
author: "Жукова София Викторовна"

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

Получение навыков настройки службы DHCP на сетевом оборудовании для распределения адресов IPv4 и IPv6.



# Выполнение лабораторной работы

Запустим GNS3. Создаю новый  проект и собираю схему по Рис. 5.1. Топология моделируемой сети(рис. [-@fig:001]).

![Устройства](image/1.png){#fig:001 width=70%}

Коммутаторам присвоим названия по принципу username-sw-0x, маршрутизаторам - по принципу
username-gw-0x, VPCS - по принципу PCx-username, где вместо username
укажем имя нашей учётной записи, вместо x - порядковый номер устройства.

Включим захват трафика на соединении между коммутатором sw-01 и маршутизатором gw-01.
На маршрутизаторе перейдите в режим конфигурирования, изменитм имя
устройства и доменное имя, замените системного пользователя, заданного
по умолчанию, на вашего пользователя  удалите указание на
назначение ip-адреса по dhcp для интерфейса eth0 (рис. [-@fig:002]).

![Режим работы SELinux](image/2.png){#fig:002 width=70%}

**DHCP-сервер**

Выйдем из vtysh и создадим конфиг (рис. [-@fig:003]).

![создадим конфиг](image/3.png){#fig:003 width=70%}


Проверим как PC1 получает IPv4-адрес от DHCP-сервера (рис. [-@fig:004]).

![Проверка](image/4.png){#fig:004 width=70%}

Пытаюсь создать Alpine templamate, но при его добавлении на область проекта понимаю, что он не подходит для apple,  испольузю frr вместо Alma Linux и Alpine Linux Virt appliance (рис. [-@fig:005]).

![создание нового устройства](image/5.png){#fig:005 width=70%}

Создаю новую схему и добавляю устройства, как показано на Рис. 5.2. Топология моделируемой сети(рис. [-@fig:006]).

![Новая схема](image/6.png){#fig:006 width=70%}

Проверим роутер (рис. [-@fig:007]). 

![роутер](image/7.png){#fig:007 width=70%}

Запустим dnsmasq (рис. [-@fig:008]).

![dnsmasq](image/8.png){#fig:008 width=70%}

Настраиваем клиентов (рис. [-@fig:009]).

![show ip](image/9.png){#fig:009 width=70%}

Настраиваем клиентов (рис. [-@fig:010]).

![ping](image/10.png){#fig:010 width=70%}



# Выводы

Мы приобрели навыки настройки службы DHCP на сетевом оборудовании для распределения адресов IPv4 и IPv6.

