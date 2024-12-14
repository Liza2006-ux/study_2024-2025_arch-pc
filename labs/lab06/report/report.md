---
## Front matter
title: "Отчёта по лабораторной работе 6"
subtitle: "Архитектура компютера"
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

Узнать и ознакомиться с арифметическими инструкциямиязыкаассемблера NASM.

# Задание

1. Написать программу вычисления выражения y = f(x)
   2. Программа должна выводить выражение для вычисления, выводитьзапрос на ввод значения x, вычислять заданное выражениевзависимости от введенного x, выводить результат вычислений.
    3. Вид функции f(x) выбрать из таблицы 6.3 вариантовзаданийвсоответствии с номером полученным при выполнениилабораторнойработы.
    4. Создайте исполняемый файл и проверьте его работу для значений x1и x2 из 6.3
# Теоретическое введение

Адресация в NASM Большинство инструкций на языкеассемблератребуют обработки операндов. Адрес операнда предоставляетместо, гдехранятся данные, подлежащие обработке. Это могут бытьданныехранящиеся в регистре или в ячейке памяти. Далее рассмотрены все существующие способызаданияадресахранения операндов – способы адресации. Существует три основных способа адресации: • Регистровая адресация – операнды хранятся в регистрахивкомандеиспользуются имена этих регистров, например: mov ax,bx. • Непосредственная адресация – значение операндазадаетсянепосредственно в команде, Например: mov ax,2. • Адресация памяти – операнд задает адрес в памяти. Вкомандеуказывается символическое обозначение ячейки памяти, надсодержимымкоторой требуется выполнить операцию.
# Выполнение лабораторной работы

Создала каталог для программам лабораторной работы№6, перешлавнего и создала файл lab6-1.asm:
mkdir ~/work/arch-pc/lab06
cd ~/work/arch-pc/lab06
touch lab6-1.asm
![1lab06](https://github.com/user-attachments/assets/4182f400-5e74-4706-be29-460823651851)


2. Рассмотрела примеры программ вывода символьныхичисленныхзначений. Программы будут выводить значения записанныеврегистрeax. Затем ввела в файл lab6-1.asm текст программыиз листинга6.1.Вданной программе в регистр eax записала символ 6 (moveax,'6'),врегистр ebx символ 4 (mov ebx,'4'). Далее к значению в регистре eax прибавила значениерегистраebx (add eax,ebx, результат сложения запишется в регистрeax). Потом вывела результат. Записала значение регистраeaxвпеременную buf1 (mov [buf1],eax), а потом адрес переменнойbuf1врегистр eax (mov eax,buf1) и вызовем функциюsprintLF. Ввела программу вывода значения регистра eax, создалаисполняемый файл и запустила его. nasm -f elf lab6-1.asm
ld -m elf_i386 -o lab6-1 lab6-1.o
./lab6-1
![2lab06](https://github.com/user-attachments/assets/5ba9cfbd-ab9f-4849-9d3a-29ecbb9ce6bc)



После изменила текст программы и вместо символов, записалаврегистры числа. Исправила текст программы (Листинг 6.1) следующимобразом: заменила строки
mov eax,'6' mov ebx,'4' на строки
mov eax,6
mov ebx,4

![3lab06](https://github.com/user-attachments/assets/de5bc0f7-1172-4e26-ac01-1307c57ee3fa)

Создала исполняемый файл и запустила его. Преобразовала текст программы из Листинга6.1сиспользованием этих функций. Создала файл lab6-2.asmвкаталоге~/work/arch-pc/lab06 и ввела в него текст программыиз листинга6.2.touch ~/work/arch-pc/lab06/lab6-2.asm
Создала исполняемый файл и запустила его.


![4lab06](https://github.com/user-attachments/assets/4283e99a-b495-40d2-beef-7107a6e16669)

В результате работы программы я получила число 106Аналогично предыдущему примеру изменила символыначисла.Потом заменила строки mov eax,'6' mov ebx,'4' на строкиmoveax,6movebx,4 Создала исполняемый файл и запустила его
Заменила функцию iprintLF на iprint, создайла исполняемыйфайли запустила его.

![5lab06](https://github.com/user-attachments/assets/6b9bbdee-40dd-4d5b-9831-46a622fe0d8b)

Создала файл lab6-3.asm в каталоге ~/work/arch-pc/lab06:
touch ~/work/arch-pc/lab06/lab6-3.asm

![6lab06](https://github.com/user-attachments/assets/01a2d46c-09e5-4af6-a473-7d5bdcedbc21)

Изучила текст программы из листинга 6.3 и ввела вlab6-3.asm.Создала исполняемый файл и запустила его. Результат работы программы должен быть следующим:user@dk4n31:~$ ./lab6-3
Результат: 4
Остаток от деления: 1
user@dk4n31:~$
Изменила текст программы для вычисления выражения

![7lab06](https://github.com/user-attachments/assets/2bb158fc-7663-4682-b7d7-cc5eed04e964)
![8lab06](https://github.com/user-attachments/assets/f95d66b9-5557-4cf3-b88c-fe96d083193d)

f(x) = (4 ∗ 6 + 2)/5. Создала исполняемый файл ипроверилаегоработу. Ответ: 5!





Далее вывела запрос на введение №студенческогобилета, потомвычислила номер варианта по формуле:
![9lab06](https://github.com/user-attachments/assets/3d8ca487-89de-42d9-983a-2a8222b7ba0f)


(𝑆 mod 20) + 1, где 𝑆 – номер студенческого билета(Вданномслучае a mod b – это остаток от деления a на b), потомвывеланаэкранномер варианта. Создала файл variant.asm в каталоге ~/work/arch-pc/lab06:
touch ~/work/arch-pc/lab06/variant.asm
Изучила текст программы из листинга 6.4 иввелавфайлvariant.asm. Потом создла исполняемый файл и запустила его, далеепроверила результат работы программы, вычислив номервариантааналитически. Ответы на вопросы:
1. Какие строки листинга 6.4 отвечают за вывод на экран сообщения‘Вашвариант:’?
20
2. Для чего используется следующие инструкции?
mov ecx, x помещаем в регистр ecx число х
mov edx, 80 длина строки 80 символов
call sread считывает из строки длиной 80 символов значение переменнойх3. Для чего используется инструкция “call atoi”?
4. Какие строки листинга 6.4 отвечают за вычисления варианта?
12
5. В какой регистр записывается остаток от деления при выполненииинструкции “div ebx”?
При этом остаток от целочисленного деления помещается в регистрAH, DXили EDX соответственно. 6. Для чего используется инструкция “inc edx”? -Инструкция
inc edx используется для увеличения значения регистра EDXна 17. Какие строки листинга 6.4 отвечают за вывод на экранрезультатавычислений?
mov eax,edx
call iprintLF



Выполнение самостоятельной работы. 
Написала программу вычисления выражения y = f(x). (Программа должна выводить выражение для вычисления, выводитьзапрос на ввод значения x, вычислять заданное выражение взависимостиот введенного x, выводить результат вычислений.)
![10lab06](https://github.com/user-attachments/assets/83baa85f-e509-4270-8192-26ac28bafd12)

Вид функции f(x) выбрала из таблицы 6.3 вариантовзаданийвсоответствии с номером полученным при выполнениилабораторнойработы

Затем создала исполняемый файл и проверьте его работудлязначений x1 и x2 из 6.3. x1 = 1, ответ = 21 и x2 = 3, ответ = 48
![11lab06](https://github.com/user-attachments/assets/344d9ec2-3d33-43a8-8d12-10e17315c756)


# Выводы

Целью было - узнать и ознакомиться с арифметическими инструкциямиязыкаассемблера NASM, проделав данные задания, я освоила инструкция в NASM. 

# Список литературы{.unnumbered}

1. GDB: The GNU Project Debugger. —URL: https://www.gnu.org/software/gdb/.2. GNU Bash Manual. — 2016. — URL: https://www.gnu.org/software/bash/manual/. 3. Midnight Commander Development Center. —2021. —URL: https://midnight-commander. org/. 4. NASM Assembly Language Tutorials. —2021. —URL: https://asmtutor.com/. 5. Newham C. Learning the bash Shell: Unix Shell Programming. —O’Reilly Media, 2005. — 354 с. — (In a Nutshell). —ISBN 0596009658. —URL: http://www.amazon.com/Learningbash-Shell-Programming-Nutshell/dp/0596009658.6. Robbins A. Bash Pocket Reference. —O’Reilly Media, 2016. —156с.— ISBN 978-1491941591. 7. The NASM documentation. — 2021. —URL: https://www.nasm.us/docs.php. 8. Zarrelli G. Mastering Bash. — Packt Publishing, 2017. —502с. —ISBN9781784396879. 9. Колдаев В. Д., Лупин С. А. Архитектура ЭВМ. —М. : Форум, 2018.10. Куляс О. Л., Никитин К. А. Курс программирования на ASSEMBLER. — М. : Солон-Пресс, 2017. 11. Новожилов О. П. Архитектура ЭВМи систем. —М. : Юрайт, 2016.12. Расширенный ассемблер: NASM. —2021. —URL: https://www.opennet.ru/docs/RUS/nasm/. 13. Робачевский А., Немнюгин С., Стесик О. ОперационнаясистемаUNIX. — 2-е изд. — БХВПетербург, 2010. —656 с. —ISBN978-5-94157-538-1.14. Столяров А. Программирование на языке ассемблера NASMдляОС Unix. — 2-е изд. — М. : МАКС Пресс, 2011. —URL: http://www.stolyarov.info/books/asm_unix. 15. Таненбаум Э. Архитектура компьютера. —6-е изд. —СПб. : Питер,2013. — 874 с. — (Классика Computer Science). 16. Таненбаум Э., Бос Х. Современные операционные системы. —4-еизд. — СПб. : Питер, 2015. — 1120 с. — (Классика Computer Science
