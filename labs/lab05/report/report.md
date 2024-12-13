---
## Front matter
title: "Отчёт по лабораторной работе 5"
subtitle: "Архитектура компьютера"
author: "Волчкова Елизавета дмитриевна"

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

Приобретение практических навыков работы в Midnight Commander. Освоение инструкций
языка ассемблера mov и int.


# Задание

1. Создайте копию файла lab5-1.asm. Внесите изменения в программу (без использования внешнего файла in_out.asm), так чтобы она работала по следующему алгоритму:
• вывести приглашение типа “Введите строку:”;
• ввести строку с клавиатуры;
• вывести введённую строку на экран.
2. Получите исполняемый файл и проверьте его работу. На приглашение ввести строку
введите свою фамилию.
3. Создайте копию файла lab5-2.asm. Исправьте текст программы с использование подпрограмм из внешнего файла in_out.asm, так чтобы она работала по следующему
алгоритму:
• вывести приглашение типа “Введите строку:”;
• ввести строку с клавиатуры;
• вывести введённую строку на экран.

# Теоретическое введение

Следующие комбинации клавиш облегчают работу с Midnight Commander:
• Tab используется для переключениями между панелями;
• ↑ и ↓ используется для навигации, Enter для входа в каталог или открытия файла
(если в файле расширений mc.ext заданы правила связи определённых расширений
файлов с инструментами их запуска или обработки);
• Ctrl + u (или через меню Команда > Переставить панели ) меняет местами содержимое
правой и левой панелей;
• Ctrl + o (или через меню Команда > Отключить панели ) скрывает или возвращает панели
Midnight Commander, за которыми доступен для работы командный интерпретатор
оболочки и выводимая туда информация.
• Ctrl + x + d (или через меню Команда > Сравнить каталоги ) позволяет сравнить содержимое каталогов, отображаемых на левой и правой панелях.


# Выполнение лабораторной работы

1. Сначала открыла Midnight Commander user@dk4n31:~$mc2.
2.  Далее я, пользуясь клавишами ↑, ↓ и Enter перешлавкаталог~/work/arch-pc созданный при выполнении лабораторнойработы№4.

![1lab05](https://github.com/user-attachments/assets/ddd84570-4de9-4d26-a1a4-db37bcb46f62)

3. С помощью функциональной клавиши F7 создала папкуlab05иперешла в созданный каталог.

![2lab05](https://github.com/user-attachments/assets/9cd2cabd-d542-4eab-b8fd-1fcff26fb8c7)

5. Потом, пользуясь строкой ввода и командой touch создалаlab5-1.asm.5.Затем с помощью функциональной клавиши F4 открылафайлlab5-1.asm для редактирования во встроенном редакторе.
6. После ввела текст программы из листинга 5.1, затем сохранила изменения и закрыда файл.
![3lab05](https://github.com/user-attachments/assets/3b994b38-3183-486d-a52a-ff6c90ad42cd)


7. После этого с помощью функциональной клавишиF3открылафайл lab5-1.asm для просмотра и убедилась, что файл содержит
 текст программы
![4lab05](https://github.com/user-attachments/assets/53f69a9b-7526-4b5f-b899-f5f8089e754d)

8. Оттранслировала текст программы lab5-1.asmв объектныйфайл. Далее я выполнила компоновку объектного файла изапуститеполучившийся исполняемый файл.
![5lab05](https://github.com/user-attachments/assets/995ba25c-d57f-48b6-a0fb-bcc56140d46c)
![6lab05](https://github.com/user-attachments/assets/73f1d642-edb2-4e2e-af81-ef6fa84c6202)

9. Для вызова подпрограммы из внешнего файла использовала инструкциюcall, которая имеет следующий вид call, где function - имя подпрограммы.Для выполнения лабораторных работ использовала файл in_out.asm1.(Подключаемый файл in_out.asm должен лежать в томже каталоге,чтои файл с программой, в которой он используется.)
Затем в одной из панелей mc открыла каталог с файломlab5-1.asm.Вдругой панели каталог со скаченным файлом in_out.asm. Скопировала файл in_out.asm в каталог с файлом lab5-1.asmспомощью функциональной

![7lab05](https://github.com/user-attachments/assets/df1cc673-79ff-4237-a65d-5b03a40495d0)

Дальше я с помощью функциональной клавиши F6 создалакопиюфайла lab5-1.asm с именем lab5-2.asm, вывела файл lab5-1.asm, нажалаклавишу F6 , ввела имя файла lab5-2.asm и нажала клавишу Enter. Исправила текст программы в файле lab5-2.asmс использованиеподпрограмм из внешнего файла in_out.asm (используя подпрограммыsprintLF, sread и quit) в соответствии с листингом 5.2. и создала исполняемыйфайл и проверила его работу.

Выполнение для самостоятельной работы. 
1. В начале я создала копию файла lab5.asm. Затем внесла изменения в программу (без использования внешнего файла in_out.asm)Важное условие, чтобы она программа по следующемуалгоритму:• вывести приглашение типа “Введите строку:”; • ввести строку с клавиатуры; • вывести введённую строку на экран.
2. ![8lab05](https://github.com/user-attachments/assets/dfdef505-5985-4b5f-9014-f83836bb47c5)

3. 2. Затем я получила исполняемый файл lab5.exe
![9lab05](https://github.com/user-attachments/assets/87fd6e6e-b8e0-4085-8b10-dd404e5add41)

4. Проверила работу программы. Условие задачи выполнено, дляпримера ввела «f» и получила «f»
# Выводы


Целью работы было - приобретение практических навыков работы в Midnight Commander и освоение инструкций
языка ассемблера mov и int, сделав данные задания я приоберал необходимые навыки.

# Список литературы{.unnumbered}

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
