---
## Front matter
title: "Отчёт по лабораторной работе №13"
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


# Цель работы
Цель работы
Изучить основы программирования в оболочке ОС UNIX. Научится писать более
сложные командные файлы с использованием логических управляющих конструкций
и циклов.
#  Последовательность выполнения работы
1. Используя команды getopts grep, написала командный файл, который анализирует
командную строку с ключами:
– -iinputfile — прочитать данные из указанного файла;
– -ooutputfile — вывести данные в указанный файл;
– -pшаблон — указать шаблон для поиска;
– -C — различать большие и малые буквы;
– -n — выдавать номера строк.
а затем ищет в указанном файле нужные строки, определяемые ключом -p.
![lab123scr1](https://github.com/user-attachments/assets/2a50956e-7fff-4304-a375-33e00c34d6d5)


3. Написала на языке Си программу, которая вводит число и определяет, является ли оно
больше нуля, меньше нуля или равно нулю.
****![lab13scr2](https://github.com/user-attachments/assets/49d26b81-6c7c-46a9-8126-4ee310e12893)

 Затем программа завершается с помощью
функции exit(n), передавая информацию в о коде завершения в оболочку.
Командный файл вызывал эту программу и, проанализировав с помощью команды
$?, выдал сообщение о том, какое число было введено.
![lab13scr3](https://github.com/user-attachments/assets/a40a6841-70c6-490d-9413-26142646de4f)

5. Написала командный файл, создающий указанное число файлов, пронумерованных
последовательно от 1 до 𝑁 (например 1.tmp, 2.tmp, 3.tmp,4.tmp и т.д.).
Число файлов,
![lab13scr4JPG](https://github.com/user-attachments/assets/25fd65ee-76ca-4dbb-b446-48e2ea9deacb)

которые необходимо создать, передаётся в аргументы командной строки.
Этот же командный файл умеет удалять все созданные им файлы (если они существуют).
![lab13scr5](https://github.com/user-attachments/assets/e56a1003-a0e5-4855-933c-466d7acea53d)

7. Написала командный файл, который с помощью команды tar запаковывает в архив
все файлы в указанной директории. Модифицировала его так, чтобы запаковывались
только те файлы, которые были изменены менее недели тому назад (использовала
команду find).
![lab13scr6](https://github.com/user-attachments/assets/d0eeb51d-f77f-416c-ac5f-00a3d9eda9f3)

# Вывод
Проделав данные задания - я смогла освоить материал и достичь цели.
