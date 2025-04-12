---
## Front matter
title: "Отчёт по внешнему курсу=степик"
subtitle: "Операционные системы"
author: "Волчкова Eлизавета Дмитриевна"

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


# Сначала о формате
Каждая неделя состоит из нескольких уроков, которые представляют собой наборы коротких видео-лекций (от 30 секунд до 5 минут, в редких случаях дольше).

Обычно один урок посвящен обсуждению одного понятия в общем, а один видео-фрагмент внутри урока — одной стороне или детали понятия.

Видео чередуются с простыми тестами, состоящими из одного-двух вопросов для проверки только что услышанного материала.

Внутри одного урока видеофрагменты и тесты на платформе Stepik принято называть шагами (стэпами). В верхней части окна вы можете видеть несколько иконок-квадратов. Это кнопки навигации, позволяющие перемещаться от одного фрагмента видео или тестов к другому. Также можно использовать клавиши «вправо» и «влево» на клавиатуре.

Перейдите к следующему шагу, чтобы увидеть тестовое задание в действии.
