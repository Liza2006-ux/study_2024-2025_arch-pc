---
## Front matter
title: "Шаблон отчёта по лабораторной работе номер 9"
subtitle: "Архитектура компьютеровт"
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

Приобретение навыков написания программ с использованием подпрограмм и знакомство
с методами отладки при помощи GDB и его основными возможностями.



# Задание

1. Преобразуйте программу из лабораторной работы №8 (Задание №1 для самостоятель-
ной работы), реализовав вычисление значения функции 𝑓(𝑥) как подпрограмму.
2. В листинге 9.3 приведена программа вычисления выражения (3 + 2) ∗ 4 + 5. При запуске
данная программа дает неверный результат. Проверьте это. С помощью отладчика GDB,
анализируя изменения значений регистров, определите ошибку и исправьте ее

# Теоретическое введение


Отладка — это процесс поиска и исправления ошибок в программе. В общем случае его
можно разделить на четыре этапа:
• обнаружение ошибки;
• поиск её местонахождения;
• определение причины ошибки;
• исправление ошибки.
Можно выделить следующие типы ошибок:
• синтаксические ошибки — обнаруживаются во время трансляции исходного кода и
вызваны нарушением ожидаемой формы или структуры языка;
• семантические ошибки — являются логическими и приводят к тому, что программа
запускается, отрабатывает, но не даёт желаемого результата;
• ошибки в процессе выполнения — не обнаруживаются при трансляции и вызывают пре-
рывание выполнения программы (например, это ошибки, связанные с переполнением
или делением на ноль).
Более подробно про Unix см. в [@tanenbaum_book_modern-os_ru; @robbins_book_bash_en; @zarrelli_book_mastering-bash_en; @newham_book_learning-bash_en].

# Выполнение лабораторной работы

1. Создала каталог для выполнения лабораторной работы № 9, перешла в него и со-
здала файл lab09-1.asm


3. В качестве примера рассмотрела программу вычисления арифметического выражения
𝑓(𝑥) = 2𝑥 + 7 с помощью подпрограммы _calcul. В данном примере 𝑥 вводилось с
клавиатуры, а само выражение вычисляется в подпрограмме. Затем внимательно изучила
текст программы (Листинг 9.1).
Листинг 9.1. П
![1](image/1lab09.jpg)

![2lab09](https://github.com/user-attachments/assets/7c9511e8-fa88-4eb4-941c-f8cde53eb685)

Первые строки программы отвечают за вывод сообщения на экран (call sprint), чтение
данных введенных с клавиатуры (call sread) и преобразования введенных данных из
символьного вида в численный (call atoi).]
После следующей инструкции call _calcul, которая передает управление подпрограмме
_calcul, выполнила инструкции подпрограммы:

![3lab09](https://github.com/user-attachments/assets/ed356321-7e97-4165-ab34-453edf1a67d1)


Инструкция ret является последней в подпрограмме и ее исполнение приводит к воз-
вращению в основную программу к инструкции, следующей за инструкцией call, которая
вызвала данную подпрограмму.
![4lab09](https://github.com/user-attachments/assets/1f14db51-0d44-429e-a814-52e81aa1e32b)

Последние строки программы реализуют вывод сообщения (call sprint), результата вы-
числения (call iprintLF) и завершение программы (call quit).

Ввела в файл lab09-1.asm текст программы из листинга 9.1. Создала исполняемый
файл и проверила его работу.

Потом изменила текст программы, добавив подпрограмму _subcalcul в подпрограмму _calcul,
для вычисления выражения 𝑓(𝑔(𝑥)), где 𝑥 вводится с клавиатуры, 𝑓(𝑥) = 2𝑥 + 7, 𝑔(𝑥) =
3𝑥 − 1. Т.е. 𝑥 передается в подпрограмму _calcul из нее в подпрограмму _subcalcul, где
вычисляется выражение 𝑔(𝑥), результат возвращается в _calcul и вычисляется выражение
𝑓(𝑔(𝑥)). Результат возвращается в основную программу для вывода результата на экран.
9.4.2. Отладка программам с помощью GDB
Сначала создала файл lab09-2.asm с текстом программы из Листинга 9.2. (Программа печати
сообщения Hello world!):



![5lab9](https://github.com/user-attachments/assets/7c14bd41-ebfc-415a-b49c-d349fe034cb5)
![6lab09](https://github.com/user-attachments/assets/8dc1cce2-03f6-4a90-b6d7-49d6efc89d5e)


![7lab09](https://github.com/user-attachments/assets/115e1ec1-02e6-4166-9a3d-709e60f383b1)

Получила исполняемый файл. Для работы с GDB в исполняемый файл необходимо добавила
отладочную информацию, для этого трансляцию программ необходимо проводить с ключом
‘-g’.\

![8lab09](https://github.com/user-attachments/assets/41317fbc-245d-4171-94fd-39983ec33ac7)




![9lab09](https://github.com/user-attachments/assets/e99f4a69-e6cf-4b2e-bf65-558eb4dfdce3)



Загрузила исполняемый файл в отладчик gdb:
user@dk4n31:~$ gdb lab09-2
Проверила работу программы, запустив ее в оболочке GDB с помощью команды run (со-
кращённо r):
(


Hello, world!
[Inferior 1 (process 10220) exited normally]
(gdb)
Для более подробного анализа программы установила брейкпоинт на метку _start, с
которой начинается выполнение любой ассемблерной программы, и запустила её.
(gdb) break _start
Breakpoint 1 at 0x8049000: file lab09-2.asm, line 12.
(gdb) run
Starting program: ~/work/arch-pc/lab09/lab09-2
Breakpoint 1, _start () at lab09-2.asm:12
12 mov eax, 4

![10lab09](https://github.com/user-attachments/assets/5ae8e699-0246-4ea0-9a5b-70ee172a6693)


Посмотрела дисассимилированный код программы с помощью команды disassemble
начиная с метки _start
(gdb) disassemble _start
Переключилась на отображение команд с Intel’овским синтаксисом, введя команду set
disassembly-flavor intel
(gdb) set disassembly-flavor intel
(gdb) disassemble _start
Перечислила различия отображения синтаксиса машинных команд в режимах ATT и Intel.
Далее включила режим псевдографики для более удобного анализа программы (рис. 9.2):
(gdb) layout asm
(gdb) layout regs

В этом режиме есть три окна:

• В верхней части видны названия регистров и их текущие значения;
• В средней части виден результат дисассимилирования программы;
• Нижняя часть доступна для ввода команд.

9.4.2.1. Добавление точек останова
Установить точку останова можно командой break (кратко b). Типичный аргумент этой
команды — место установки. Его можно задать или как номер строки программы (имеет
смысл, если есть исходный файл, а программа компилировалась с информацией об отладке),
или как имя метки, или как адрес. Чтобы не было путаницы с номерами, перед адресом
ставится «звёздочка»:
На предыдущих шагах была установлена точка останова по имени метки (_start). Про-
верьте это с помощью команды info breakpoints (кратко i b):
![12lab09](https://github.com/user-attachments/assets/962e1dcb-dd35-4f57-aed1-abf67ec5257b)

![13lab09](https://github.com/user-attachments/assets/0d6a7f17-d10c-451b-919b-3514a850de25)




Посмотрела значение переменной msg1 по имени и посмотрела значение переменной msg2 по адресу.

![14лаб09](https://github.com/user-attachments/assets/c60136ed-e7dd-426d-b386-3853a54380ba)

![15lab09](https://github.com/user-attachments/assets/0c526e0b-17e9-432f-814f-7ce5f5bf2053)

Вывел в различных форматах (в шестнадцатеричном формате, в двоичном формате и в символьном виде) значение регистра edx.


![16lab09](https://github.com/user-attachments/assets/1b4c2f94-285f-4541-b919-488dcbfad725)

![17lab09](https://github.com/user-attachments/assets/cbb3b20b-0ebd-469c-9368-70c30d4c9a67)

Скопировал файл lab8-2.asm, созданный при выполнении лабораторной работы №8, с программой выводящей на экран аргументы командной строки. Создал исполняемый файл. Для загрузки в gdb программы с аргументами необходимо использовать ключ --args. Загрузил исполняемый файл в отладчик, указав аргументы.

![18lab09](https://github.com/user-attachments/assets/c9fe06fa-0425-4ddf-b73a-843e3d48bd75)

![Uploading 19lab09.jpg…]()


Установила точку останова перед первой инструкцией в программе и запустила ее.

Адрес вершины стека храниться в регистре esp и по этому адресу располагается число равное количеству аргументов командной строки (включая имя программы). Как видно, число аргументов равно 5 – это имя программы lab9-3 и непосредственно аргументы: аргумент1, аргумент, 2 и 'аргумент 3'.

Посмотрела остальные позиции стека – по адесу [esp+4] располагается адрес в памяти где находиться имя программы, по адесу [esp+8] храниться адрес первого аргумента, по  

# Выводы

Целью работы было - приобретение навыков написания программ с использованием подпрограмм и знакомство
с методами отладки при помощи GDB и его основными возможностями, сделав данные задания, я познакомилась с написанием программ при помощи GDB.

# Список литературы{.unnumbered}
1. GDB: The GNU Project Debugger. — URL: https://www.gnu.org/software/gdb/.
2. GNU Bash Manual. — 2016. — URL: https://www.gnu.org/software/bash/manual/.
3. Midnight Commander Development Center. — 2021. — URL: https://midnight-commander.
org/.
4. NASM Assembly Language Tutorials. — 2021. — URL: https://asmtutor.com/.
5. Newham C. Learning the bash Shell: Unix Shell Programming. — O’Reilly Media, 2005. —
354 с. — (In a Nutshell). — ISBN 0596009658. — URL: http://www.amazon.com/Learning-
bash-Shell-Programming-Nutshell/dp/0596009658.
6. Robbins A. Bash Pocket Reference. — O’Reilly Media, 2016. — 156 с. — ISBN 978-1491941591.
7. The NASM documentation. — 2021. — URL: https://www.nasm.us/docs.php.
8. Zarrelli G. Mastering Bash. — Packt Publishing, 2017. — 502 с. — ISBN 9781784396879.
9. Колдаев В. Д., Лупин С. А. Архитектура ЭВМ. — М. : Форум, 2018.
10. Куляс О. Л., Никитин К. А. Курс программирования на ASSEMBLER. — М. : Солон-Пресс,
2017.
11. Новожилов О. П. Архитектура ЭВМ и систем. — М. : Юрайт, 2016.
12. Расширенный ассемблер: NASM. — 2021. — URL: https://www.opennet.ru/docs/RUS/nasm/.
13. Робачевский А., Немнюгин С., Стесик О. Операционная система UNIX. — 2-е изд. — БХВ-
Петербург, 2010. — 656 с. — ISBN 978-5-94157-538-1.
14. Столяров А. Программирование на языке ассемблера NASM для ОС Unix. — 2-е изд. —
М. : МАКС Пресс, 2011. — URL: http://www.stolyarov.info/books/asm_unix.
15. Таненбаум Э. Архитектура компьютера. — 6-е изд. — СПб. : Питер, 2013. — 874 с. —
(Классика Computer Science).
16. Таненбаум Э., Бос Х. Современные операционные системы. — 4-е изд. — СПб. : Питер,
2015. — 1120 с. — (Классика Computer Science)
::: {#refs}
:::
