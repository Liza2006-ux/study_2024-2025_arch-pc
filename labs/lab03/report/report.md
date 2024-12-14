---
## Front matter
title: "Отчёт по лабораторной работе 3"
subtitle: "Простейший вариант"
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

Целью работы является освоение процедуры оформления отчетов с помощью легковесного
языка разметки Markdown.

# Задание

1. В соответствующем каталоге сделайте отчёт по лабораторной работе № 2 в формате
Markdown. В качестве отчёта необходимо предоставить отчёты в 3 форматах: pdf, docx
и md.
2. Загрузите файлы на github.


# Теоретическое введение

Чтобы создать заголовок, используйте знак #, например:
# This is heading 1
## This is heading 2
### This is heading 3
#### This is heading 4
Чтобы задать для текста полужирное начертание, заключите его в двойные звездочки:
This text is **bold**.
Чтобы задать для текста курсивное начертание, заключите его в одинарные звездочки:
This text is *italic*

# Выполнение лабораторной работы
Отккрыла терминал
Я создала заголовок, используя знак #, например:
# This is heading 1
## This is heading 2
### This is heading 3
#### This is heading 4
Задала для текста полужирное начертание, заключила его в двойные
звездочки: This text is **bold**, а для того чтобы сделать для текста
курсивное начертание, заключила его в одинарные звездочки: This text is
*italic*. Затем задала полужирное и курсивное начертание, заключите его в
тройные звездочки: This is text is both ***bold and italic***. Потом создала блоки цитирования с помощью символа >:
> The drought had lasted now for ten million years, and the reign of the
terrible lizards had long since ended. Here on the Equator, in the continent which
would one day be known as Africa, the battle for existence had reached a new
climax of ferocity, and the victor was not yet in sight. In this barren and desiccated
land, only the small or the swift or the fierce could flourish, or even hope to
survive.

![1lab03](https://github.com/user-attachments/assets/5f330aab-d698-4ab0-80f7-df8fac2060e7)


Далее я упорядоченный список отформатировала с помощью
соответствующих цифр:
1. First instruction
1.Sub-instruction
1. Sub-instruction
1. Second instruction
![2lab03](https://github.com/user-attachments/assets/c8036d90-5857-4954-81b1-d40c69203e39)


Потом вложила один список в другой, далее добавила отступ для
элементов дочернего списка:
1. First instruction
1. Second instruction
1. Third instruction

![3lab03](https://github.com/user-attachments/assets/a04dd9b9-42d3-4932-886d-f0be53ada664)

Я отформатировала неупорядоченный (маркированный) список с
помощью звездочек или тире:
* List item 1
* List item 2
* List item 3
Но, чтобы вложить один список в другой, я добавила отступ для
элементов дочернего списка: - List item 1
- List item A
- List item B
- List item 2
![4lab03](https://github.com/user-attachments/assets/31f8e0fc-a596-4cda-ac44-5cb7f46816a5)

Так как синтаксис Markdown для встроенной ссылки состоит из части
[link text], представляющей текст гиперссылки, и части (file-name.md) – URL- адреса или имени файла, на который дается ссылка:
[link text](file-name.md) или [link text](http://example.com/ "Необязательная
подсказка"). Я ввела эти ссылки. Теория: Огражденные блоки кода — это простой способ выделить
синтаксис для фрагментов кода. Общий формат огражденных блоков кода: ``` language your code goes in here ```, я ввела эту команду.




Я ввела ормула sin2 (x) + cos2 (x) = 1, которая записывается так:
$\sin^2 (x) + \cos^2 (x) = 1$
Выключение формулы: sin2 (x) + cos2 (x) = 1 (3.1) со ссылкой в тексте
«Смотри формулу ({-eq. 3.1}).» я записала, как:
$$ \sin^2 (x) + \cos^2 (x) = 1 $$ {#eq:eq1}
Смотри формулу (`[-@eq:eq1]`).

![6lab03](https://github.com/user-attachments/assets/44446c86-ac88-4199-8dc9-fca2a8c90e42)


В конце преобразовала файл README.md таким образом: pandoc
README.md -o README.pdf

![7lab03](https://github.com/user-attachments/assets/c6141ef0-17c4-424a-bafb-1f760ae389d3)


 
3.5. Задание для самостоятельной работы
1. В соответствующем каталоге сделала по лабораторной работе № 2 в формате
Markdown. В качестве отчёта предоставила отчёты в 3 форматах: pdf, docx
и md.
2. Загрузила файлы на github.

# Выводы

Целью работы было освоение процедуры оформления отчетов с помощью легковесного
языка разметки Markdown, проделав данные задания, я поняла, как оформлять отч`ты с помощью Markdown.

# Список литературы{.unnumbered}

Список литературы
1. GDB: The GNU Project Debugger. — URL: https://www.gnu.org/software/gdb/.
2. GNU Bash Manual. — 2016. — URL: https://www.gnu.org/software/bash/manual/.
3. Midnight Commander Development Center. — 2021. — URL: https://midnight-commander.
org/.
4. NASM Assembly Language Tutorials. — 2021. — URL: https://asmtutor.com/.
5. Newham C. Learning the bash Shell: Unix Shell Programming. — O’Reilly Media, 2005. —
354 с. — (In a Nutshell). — ISBN 0596009658. — URL: http://www.amazon.com/Learningbash-Shell-Programming-Nutshell/dp/0596009658.
6. Robbins A. Bash Pocket Reference. — O’Reilly Media, 2016. — 156 с. — ISBN 978-1491941591.
7. The NASM documentation. — 2021. — URL: https://www.nasm.us/docs.php.
8. Zarrelli G. Mastering Bash. — Packt Publishing, 2017. — 502 с. — ISBN 9781784396879.
9. Колдаев В. Д., Лупин С. А. Архитектура ЭВМ. — М. : Форум, 2018.
10. Куляс О. Л., Никитин К. А. Курс программирования на ASSEMBLER. — М. : Солон-Пресс,
2017.
11. Новожилов О. П. Архитектура ЭВМ и систем. — М. : Юрайт, 2016.
12. Расширенный ассемблер: NASM. — 2021. — URL: https://www.opennet.ru/docs/RUS/nasm/.
13. Робачевский А., Немнюгин С., Стесик О. Операционная система UNIX. — 2-е изд. — БХВПетербург, 2010. — 656 с. — ISBN 978-5-94157-538-1.
14. Столяров А. Программирование на языке ассемблера NASM для ОС Unix. — 2-е изд. —
М. : МАКС Пресс, 2011. — URL: http://www.stolyarov.info/books/asm_unix.
15. Таненбаум Э. Архитектура компьютера. — 6-е изд. — СПб. : Питер, 2013. — 874 с. —
(Классика Computer Science).
16. Таненбаум Э., Бос Х. Современные операционные системы. — 4-е изд. — СПб. : Питер,
2015. — 1120 с. — (Классика Computer Science).
