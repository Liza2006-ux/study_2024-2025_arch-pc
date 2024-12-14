---
## Front matter
title: "Отчёт по лабораторной работе 7"
subtitle: "Архитектура компьютера"
author: "Волчкова Елизавета Дмитриевна"

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

Изучить команды условного и безусловного переходов иприобрестинавыки написания программ с использованием переходов, атакжезнакомство с назначением и структурой файла листинга.
# Задание

1. Напишите программу нахождения наименьшей из 3 целочисленныхпеременных �,� и . Значения переменных выбрать из табл. 7.5 всоответствиис вариантом, полученным при выполнении лабораторнойработы№7.Создайте исполняемый файл и проверьте его работу. 2. Напишите программу, которая для введенных с клавиатурызначений� и � вычисляет значение заданной функции �(�) и выводитрезультатвычислений. Вид функции �(�) выбрать из таблицы 7.6 вариантовзаданийвсоответствии с вариантом, полученным при выполнениилабораторнойработы № 7. Создайте исполняемый файл и проверьте егоработудлязначений � и � из 7.6.
# Теоретическое введение

Для реализации ветвлений в ассемблере используются такназываемыекоманды передачи управления или команды перехода. Можно выделить 2 типа переходов: • условный переход – выполнение или не выполнение переходавопределенную точку программы в зависимости от проверки условия. • безусловный переход – выполнение передачи управлениявопределенную точку программы без каких-либо условий.
# Выполнение лабораторной работы

1. Сначала создала каталог для программам лабораторнойработы№7,перешла в него и создайте файл lab7-1.asm:
mkdir ~/work/arch-pc/lab07
cd ~/work/arch-pc/lab07
touch lab7-1.asm

![1lab07](https://github.com/user-attachments/assets/e84922c5-32ed-4402-ac05-9fd07e71bf67)


Ввела в файл lab7-1.asm текст программы из листинга 7.1.

![2lab07](https://github.com/user-attachments/assets/adc3fefd-a246-40cb-b8be-42d979e75da6)

Создала исполняемый файл и запустила его. Результат работы данной программы будет следующим:
root@LAPTOP-KE7VHG2Q:~# ./lab7
Сообщение № 2
Сообщение № 3
root@LAPTOP-KE7VHG2Q:~#

![3lab07](https://github.com/user-attachments/assets/5c0f8ff9-2767-432f-abd5-6802c03a2359)


Далее в текст программы после вывода сообщения №2добавилаинструкцию jmp с меткой _label1 и после вывода сообщения №1добавилаинструкцию jmp с меткой _end .

![4lab07](https://github.com/user-attachments/assets/ce588c03-c45a-477f-b987-33e47d78a113)


Затем создала исполняемый файл и проверила его работу. Потомизменила текст программы добавив или изменив инструкцииjmp, чтобывывод программы был следующим:
root@LAPTOP-KE7VHG2Q:~# ./lab7
Сообщение № 3
Сообщение № 2
Сообщение № 1
root@LAPTOP-KE7VHG2Q:~#

![5lab07](https://github.com/user-attachments/assets/1ede9605-0fa1-478f-9332-338d45763ae2)
После создала файл lab7-2.asm в каталоге ~/work/arch-pc/lab07. Иявнимательно изучилла текст программы из листинга 7.3 и ввела вlab7-2.asmДалее я создала исполняемый файл и проверила его работудляразныхзначений B.

![6lab07](https://github.com/user-attachments/assets/4af07f18-526c-4549-ab40-4d828ef7fc62)

Потом создала файл листинга для программы из файла lab7-2.asmnasm -f elf -l list.lst lab7-2.asm
Открыла файл листинга list.lst с помощью текстового редактора nano:
nano list.lst

![7lab07](https://github.com/user-attachments/assets/33e9e1f2-c71c-4438-ad05-29efc6e37af1)


Я открыла файл с программой lab7-2.asm и в любойинструкциисдвумя операндами удалить один операнд. Выполнила трансляциюсполучением файла листинга: nasm -f elf -l list.lst lab7-2.asm-o obj.o. Какие выходные файлы создаются в этом случае?
list.lst
obj.o
11
Что добавляется в листинге?
Файл листинга позволяет увидеть работу компилятора FASM: чтогенерируеткаждая строка исходного кода, сколько байт занимают машинныекоманды,какие значения присваиваются переменным. Листинг состоит из трехколонок:первая содержит адреса (точнее, смещения в секции), вторая —сгенерированный машинный код и третья — соответствующие строчки исходногокодапрограммы.
12
1. Написала программу нахождения наименьшей из 3 целочисленныхпеременных a,b и . Значения переменных выбрать из табл. 7.5всоответствии с вариантом, полученным привыполнениилабораторной работы № 7. Создала исполняемый файл и проверила его работу.
2.  2. Написала программу, которая для введенных с клавиатурызначений x и a вычисляет значение заданной функции f(x) и выводитрезультатвычислений. Вид функции f(x) выбрала из таблицы7.6вариантовзаданий в соответствии с вариантом, полученнымпривыполнениилабораторной работы № 7. Создала исполняемый файл ипроверилаегоработу для значений x и a из 7.6.
![8lab07](https://github.com/user-attachments/assets/ab42ab1e-ad6b-4f90-b43d-a5662483e4d6)



После создала файл lab7-2.asm в каталоге ~/work/arch-pc/lab07. Иявнимательно изучилла текст программы из листинга 7.3 и ввела вlab7-2.asmДалее я создала исполняемый файл и проверила его работудляразныхзначений B.
![9lab07](https://github.com/user-attachments/assets/35c89c16-463f-47ce-9495-37b01100a146)


# Выводы

Целью было изучить команды условного и безусловногопереходовиприобрести навыки написания программ с использованиемпереходов,атакже знакомство с назначением и структурой файла листинга, сделавзадания, я смога разобраться в данной теме.

# Список литературы{.unnumbered}

1. GDB: The GNU Project Debugger. —URL: https://www.gnu.org/software/gdb/.2. GNU Bash Manual. — 2016. — URL: https://www.gnu.org/software/bash/manual/. 3. Midnight Commander Development Center. —2021. —URL: https://midnight-commander. org/. 4. NASM Assembly Language Tutorials. —2021. —URL: https://asmtutor.com/. 5. Newham C. Learning the bash Shell: Unix Shell Programming. —O’Reilly Media, 2005. — 354 с. — (In a Nutshell). —ISBN 0596009658. —URL: http://www.amazon.com/Learningbash-Shell-Programming-Nutshell/dp/0596009658.6. Robbins A. Bash Pocket Reference. —O’Reilly Media, 2016. —156с.— ISBN 978-1491941591. 7. The NASM documentation. — 2021. —URL: https://www.nasm.us/docs.php. 8. Zarrelli G. Mastering Bash. — Packt Publishing, 2017. —502с. —ISBN9781784396879. 9. Колдаев В. Д., Лупин С. А. Архитектура ЭВМ. —М. : Форум, 2018.10. Куляс О. Л., Никитин К. А. Курс программирования на ASSEMBLER. — М. : Солон-Пресс, 2017. 11. Новожилов О. П. Архитектура ЭВМи систем. —М. : Юрайт, 2016.12. Расширенный ассемблер: NASM. —2021. —URL: https://www.opennet.ru/docs/RUS/nasm/. 13. Робачевский А., Немнюгин С., Стесик О. ОперационнаясистемаUNIX. — 2-е изд. — БХВПетербург, 2010. —656 с. —ISBN978-5-94157-538-1.14. Столяров А. Программирование на языке ассемблера NASMдляОСUnix. — 2-е изд. — М. : МАКС Пресс, 2011. —URL: http://www.stolyarov.info/books/asm_unix. 15. Таненбаум Э. Архитектура компьютера. —6-е изд. —СПб. : Питер,2013. — 874 с. — (Классика Computer Science). 16. Таненбаум Э., Бос Х. Современные операционные системы. —4-еизд. — СПб. : Питер, 2015. — 1120 с. — (Классика 
