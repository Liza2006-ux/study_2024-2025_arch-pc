---
## Front matter
title: "Отчёт по лабораторной работе №1"
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
Целью данной работы является приобретение практических навыков установки операционной системы на виртуальную машину, настройки минимально необходимых для дальнейшей работы сервисов.

# Указания к работе
Техническое обеспечение
Лабораторная работа подразумевает установку на виртуальную машину VirtualBox (https://www.virtualbox.org/) операционной системы Linux (дистрибутив Fedora).
Выполнение работы возможно как в дисплейном классе факультета физико-математических и естественных наук РУДН, так и дома. Описание выполнения работы приведено для дисплейного класса со следующими характеристиками техники:
Intel Core i3-550 3.2 GHz, 4 GB оперативной памяти, 80 GB свободного места на жёстком диске;
ОС Linux Gentoo (http://www.gentoo.ru/);
VirtualBox версии 7.0 или новее.
Для установки в виртуальную машину используется дистрибутив Linux Fedora (https://getfedora.org), вариант с менеджером окон sway (https://fedoraproject.org/spins/sway/).
При выполнении лабораторной работы на своей технике вам необходимо скачать необходимый образ операционной системы (https://fedoraproject.org/spins/sway/download/index.html).
В дисплейных классах можно воспользоваться образом в каталоге /afs/dk.sci.pfu.edu.ru/common/files/iso.
Для определённости в описании будем использовать версию Fedora-Sway-Live-x86_64-41-1.4.iso.

# Домашнее задание
Дождитесь загрузки графического окружения и откройте терминал. В окне терминала проанализируйте последовательность загрузки системы, выполнив команду dmesg. Можно просто просмотреть вывод этой команды:

dmesg | less
Можно использовать поиск с помощью grep:

dmesg | grep -i "то, что ищем"
Получите следующую информацию.
Версия ядра Linux (Linux version).
Частота процессора (Detected Mhz processor).
Модель процессора (CPU0).
Объём доступной оперативной памяти (Memory available).
Тип обнаруженного гипервизора (Hypervisor detected).
Тип файловой системы корневого раздела.
Последовательность монтирования файловых систем.

# Соглашения об именовании
При выполнении работ следует придерживаться следующих правил именования:

Пользователь внутри виртуальной машины должен иметь имя, совпадающее с учётной записью студента, выполняющего лабораторную работу.
Имя хоста вашей виртуальной машины должно совпадать с учётной записью студента, выполняющего лабораторную работу.
Имя виртуальной машины должно совпадать с учётной записью студента, выполняющего лабораторную работу.
В дисплейных классах вы можете посмотреть имя вашей учётной записи, набрав в терминале команду:

id -un
При установке на своей технике необходимо использовать имя вашей учётной записи дисплейных классов. Например, если студента зовут Остап Сулейманович Бендер, то его учётная запись имеет вид osbender.

# Последовательность выполнения работы
Варианты создания образа виртуальной машины
Предлагается несколько вариантов установки ОС Linux на основе следующих программных эмуляторов:
qemu;
virtualbox.

Установка Linux на qemu
Общая информация

Данный вариант установки возможен, если у Вас установлено программное обеспечение Qemu (https://www.qemu.org/).
Выполнение в дисплейном классе

Загрузила в дисплейном классе операционную систему Linux. Осуществите вход в систему.
Настройка каталога для виртуальных машин

Запустила терминал. Перейдите в каталог /var/tmp:
![lab1scr1.JPG](https://github.com/Liza2006-ux/study_2024-2025_arch-pc/blob/master/lab1scr1.JPG)

cd /var/tmp
Создала каталог с именем пользователя (совпадающий с логином студента в дисплейном классе).
Для этого использовала команду:
mkdir /var/tmp/`id -un`
Дальнейшую работу проводитла в этом каталоге.
Создание образа
Создадим образ виртуального диска: 60GB, формат qcow2:
qemu-img create -f qcow2 fedora-sway.qcow2 60G
Запустила виртуальную машину:
qemu-system-x86_64 -boot menu=on -m 2048 -cpu max -smp 4 \
    -cdrom Fedora-Sway-Live-x86_64-41-1.4.iso \
    -drive file=fedora-sway.qcow2,format=qcow2,if=virtio,aio=native,cache=none \
    -bios /usr/share/edk2-ovmf/OVMF_CODE.fd \
    -enable-kvm -machine q35 -device intel-iommu \
    -device virtio-balloon \
    -chardev qemu-vdagent,id=vdagent0,name=vdagent,clipboard=on,mouse=off \
    -display default,show-cursor=on \
    -vga none -device virtio-gpu-pci
Видео-устройств подключено на видеокарту компьютера.
Выберите Start Fedora-Sway-Live 41.
Загрузится графический режим.
Включила Passthrough mode.
Установила систему.
После установки виртуальной машины
Для удобства создала командный файл fedora-sway-start.sh:
touch fedora-sway-start.sh
chmod +x fedora-sway-start.sh
В файл записала команду для запуска:
#!/bin/bash
d81b8)

qemu-system-x86_64 -boot menu=on \
   -m 2048 -mem-path /dev/hugepages \
   -cpu max -smp 4 \
    -drive file=fedora-sway.qcow2,format=qcow2,if=virtio,aio=native,cache=none \
    -bios /usr/share/edk2-ovmf/OVMF_CODE.fd \
    -enable-kvm -machine q35 -device intel-iommu \
    -device virtio-balloon \
    -device virtio-serial \
    -chardev spicevmc,id=vdagent,debug=0,name=vdagent \
    -device virtserialport,chardev=vdagent,name=com.redhat.spice.0 \
    -chardev qemu-vdagent,id=vdagent0,name=vdagent,clipboard=on,mouse=on \
    -display default,show-cursor=on \
    -vga none -device virtio-gpu-pci
Видео: Установка Linux на qemu

RuTube: Установка Linux на qemu

Платформа: Установка Linux на qemu

VKvideo: Установка Linux на qemu

Youtube: Установка Linux на qemu


# Установка Linux на Virtualbox
Загрузила в дисплейном классе операционную систему Linux. Осуществила вход в систему.
Настройка каталога для виртуальных машин
Создание необходимых каталогов
Запустила терминал. Перешла в каталог /var/tmp:

cd /var/tmp
Я создайла каталог с именем пользователя (совпадающий с логином студента в дисплейном классе). 
Для этого можно использовать команду:

mkdir /var/tmp/`id -un`
Проверила в свойствах VirtualBox месторасположение каталога для виртуальных машин:
/var/tmp/имя_пользователя
Здесь имя_пользователя — логин (учётная запись) студента в дисплейном классе. edvolchkova
Значения по умолчанию
Linux: $HOME/VirtualBox VMs.
Графический интерфейс

В меню выбрала Файл, Настройки.
Выберите Общие, поле Папка для машин по умолчанию.
Установила новое значение, например /var/tmp/имя_пользователя.
Нажала ОК, чтобы сохранить изменения.
Командная строка

![lab1scr2.JPG](https://github.com/Liza2006-ux/study_2024-2025_arch-pc/blob/master/lab1scr2.JPG)
Задала отображение информации о настройках VirtualBox на английском.
Задала кодировку для отображения свойств VirtualBox:

vboxmanage setproperty language C
Установила папку для виртуальных машине в /var/tmp/имя_пользователя:

vboxmanage setproperty machinefolder /var/tmp/$(id -un)
Поверила, что папка виртуальных машин по умолчанию изменена:

vboxmanage list systemproperties | grep "Default machine folder:"
Следующая команда выдаст только каталог:


![lab1scr2](https://github.com/user-attachments/assets/d870506e-4ec0-47c3-b9ee-e228802b19a8)


vboxmanage list systemproperties | grep "Default machine folder:" | cut -d":" -f2 | tr -d ' '
Установочный образ

![lab1scr2](https://github.com/user-attachments/assets/e1d14f85-2504-47c0-8c75-b4cb3eabb1fa)

Перенесла установочный образ в папку /var/tmp/имя_пользователя/iso:

mkdir -p "$(vboxmanage list systemproperties | grep 'Default machine folder:' | cut -d':' -f2 | tr -d ' ')/iso"
mv Fedora-Sway-Live-x86_64-39-1.5.iso "$(vboxmanage list systemproperties | grep 'Default machine folder:' | cut -d':' -f2 | tr -d ' ')/iso"
Настройка хост-клавиши

![lab1scr4](https://github.com/user-attachments/assets/0d9d6584-18e3-452a-bf39-9ab411c41ac0)

Хост-клавишей по умолчанию является правый Ctrl.
По умолчанию в дисплейных классах на клавише правый Ctrl находится переключатель языка ввода.
Эти значения могут конфликтовать.
Графический интерфейс

![lab1scr5](https://github.com/user-attachments/assets/b3729d2d-aa69-4844-83c2-ff31d0d870ee)

В меню выберала Файл, Настройки.
Выбрала Ввод, вкладка Виртуальная машина.
Выберала Сочетание клавиш в строке Хост-комбинация.
Нажмите новое сочетание клавиш.
Нажмала ОК, чтобы сохранить изменения.
Командная строка
Проверила текущую комбинацию для хост-клавиши:
VBoxManage getextradata global GUI/Input/HostKeyCombination
По умолчанию установлена комбинация 65508, соответствующая правой клавише Ctrl.
Установила нужную клавишу (в примере клавиша Menu):
VBoxManage setextradata global GUI/Input/HostKeyCombination 65383
Комбинации клавиш можно, например, посмотреть на странице https://pythonhosted.org/pyglet/api/pyglet.window.key-module.html.
Создание виртуальной машины

![lab1scr6](https://github.com/user-attachments/assets/0fd0d604-0048-48b1-8094-2dd9db5e0383)

Для использования графического интерфейса запустила менеджер виртуальных машин, введя в командной строке:
VirtualBox &
Создайте новую виртуальную машину в графическом интерфейсе или в командной строке.

![lab1scr7](https://github.com/user-attachments/assets/5df6cdd8-64e0-47b8-b1f3-f69a44b76b0c)

В командной строке:

vboxmanage createvm --name "$(id -un)_os-intro" --ostype Fedora_64 --register
Указала имя виртуальной машины (ваш логин в дисплейном классе), тип операционной системы — Linux, Fedora.
Указала размер основной памяти виртуальной машины — от 2048 МБ.

![lab1scr8](https://github.com/user-attachments/assets/38e1015d-0e6d-448e-abc5-e2ad0c19f6a1)

В командной строке:

vboxmanage modifyvm "$(id -un)_os-intro" --memory 2048 --acpi on --nic1 nat
Задала конфигурацию жёсткого диска — загрузочный, VDI (VirtualBox Disk Image), динамический виртуальный диск.

Задала размер диска — 80 ГБ (или больше), его расположение — в данном случае /var/tmp/имя_пользователя/имя_машины/имя_машины.vdi.

В командной строке:

vboxmanage createhd --filename "$(vboxmanage list systemproperties | grep 'Default machine folder:' | cut -d':' -f2 | tr -d ' ')/$(id -un)_os-intro/$(id -un)_os-intro.vdi" --size 80000
Выбрала в VirtualBox Вашей виртуальной машины. Добавьте новый привод оптических дисков и выберите образ.

В командной строке:

Подключила загрузку с DVD:

vboxmanage modifyvm "$(id -un)_os-intro" --boot1 dvd
Добавьте IDE-контроллер:

vboxmanage storagectl "$(id -un)_os-intro" --name "IDE Controller" --add ide --controller PIIX4
Установила созданный вами файл VDI в качестве первого виртуального жесткого диска новой виртуальной машины:

vboxmanage storageattach "$(id -un)_os-intro" --storagectl "IDE Controller" --port 0 --device 0 --type hdd --medium "$(vboxmanage list systemproperties | grep 'Default machine folder:' | cut -d':' -f2 | tr -d ' ')/$(id -un)_os-intro/$(id -un)_os-intro.vdi"
Подключила к виртуальной машине ISO-файл:

![lab1scr9](https://github.com/user-attachments/assets/4c116a09-008d-41c2-8c7f-3121ce9e02a8)

vboxmanage storageattach "$(id -un)_os-intro" --storagectl "IDE Controller" --port 0 --device 1 --type dvddrive --medium "$(vboxmanage list systemproperties | grep 'Default machine folder:' | cut -d':' -f2 | tr -d ' ')/iso/Fedora-Sway-Live-x86_64-39-1.5.iso"
При установке на собственной технике использовала скачанный образ операционной системы Fedora.
В качестве графического контроллера поставьте VMSVGA.

В командной строке:

vboxmanage modifyvm "$(id -un)_os-intro" --graphicscontroller=vmsvga
Включила ускорение 3D.

В командной строке:
vboxmanage modifyvm "$(id -un)_os-intro" --accelerate-3d=on
Если есть проблемы при отображении, загрузитесь в режиме базовой графики.
Включила общий буфер обмена и перетаскивание объектов между хостом и гостевой ОС.
В командной строке:
vboxmanage modifyvm "$(id -un)_os-intro" --clipboard-mode=bidirectional --drag-and-drop=bidirectional
Включила поддержку UEFI.
В командной строке:
vboxmanage modifyvm "$(id -un)_os-intro" --firmware=efi
Установка драйверов для VirtualBox
Вошла в ОС под заданной вами при установке учётной записью.
Нажала комбинацию Win+Enter для запуска терминала.
Запустила терминальный мультиплексор tmux:

![lab1scr10](https://github.com/user-attachments/assets/53a1800e-d84d-4b19-b140-0e3bbf8a2d20)

tmux
Переключила на роль супер-пользователя:

sudo -i
Установила средства разработки:

dnf -y group install development-tools
Установите пакет DKMS:

dnf -y install dkms
В меню виртуальной машины подключила образ диска дополнений гостевой ОС.
Подмонтируйте диск:

mount /dev/sr0 /media
Установите драйвера:

/media/VBoxLinuxAdditions.run
Перегрузила виртуальную машину:

reboot
Подключила общей папки

![lab1scr11](https://github.com/user-attachments/assets/a2ddf1d0-f3ba-4afd-b2f4-a3124b97b2a0)

Внутри виртуальной машины добавила своего пользователя в группу vboxsf (вместо username укажите ваш логин):

gpasswd -a username vboxsf
В хостовой системе подключите разделяемую папку:

vboxmanage sharedfolder add "$(id -un)_os-intro" --name=work --hostpath=work --automount
Перегрузите виртуальную машину:

![lab1scr12](https://github.com/user-attachments/assets/bba0277d-cae6-48f4-9f6b-8bc58e783972)

reboot
Папка будет монтироваться в /media/sf_work.

Установка операционной системы

![lab1scr13](https://github.com/user-attachments/assets/67f5eaaf-5f94-4bde-aad4-c0f6a141b42c)

Запуск приложения для установки системы
Загрузила LiveCD.
Появился интерфейс начальной конфигурации.
Нажала Enter для создания конфигурации по умолчанию.
Нажала Enter, чтобы выбрать в качестве модификатора клавишу Win (она же клавиша Super).
В файле конфигурации эта клавиша будет обозначена как $Mod.
Нажмите комбинацию Win+Enter для запуска терминала.
В терминале запустите liveinst.
Для перехода к раскладке окон с табами нажала Win+w.

# Установка системы на диск
Выбрала язык интерфейса и перейдите к настройкам установки операционной системы.
При необходимости скорректировала часовой пояс, раскладку клавиатуры (рекомендуется в качестве языка по умолчанию указать английский язык).
Место установки ОС оставилабез изменения.
Установилаимя и пароль для пользователя root.
Установила имя и пароль для Вашего пользователя.
Задала сетевое имя Вашего компьютера.
После завершения установки операционной системы корректно перезапустите виртуальную машину.
В VirtualBox оптический диск должен отключиться автоматически, но если это не произошло, то необходимо отключить носитель информации с образом.

![lab1scr14](https://github.com/user-attachments/assets/8ef8a05c-413b-4219-9757-f6ae624338c4)

Видео: Установка операционной системы
RuTube: Установка операционной системы
Youtube: Установка операционной системы
После установки
Войдите в ОС под заданной вами при установке учётной записью.
Нажмите комбинацию Win+Enter для запуска терминала.
Переключитесь на роль супер-пользователя:
sudo -i
Обновления

![lab1scr15](https://github.com/user-attachments/assets/9d70cf2d-d21d-4017-bc4d-560bd4cd6a12)

Установите средства разработки:

sudo dnf -y group install development-tools
Обновить все пакеты

sudo dnf -y update

![lab1scr16](https://github.com/user-attachments/assets/b07fec39-3b22-47ae-9c40-cc4f4e71ac95)

Повышение комфорта работы
Программы для удобства работы в консоли:

sudo dnf -y install tmux mc
Другой вариант консоли:

sudo dnf -y install kitty

![lab1scr17](https://github.com/user-attachments/assets/b6d25c2b-6ce8-41cb-83e3-1c8d7b7d89d2)

Автоматическое обновление
Установка программного обеспечения:

sudo dnf -y install dnf-automatic
Задала необходимую конфигурацию в файле /etc/dnf/automatic.conf.
Запустила таймер:

![lab1scr18](https://github.com/user-attachments/assets/973951ac-77f0-4ff9-9c6b-05afe1ce087c)

sudo systemctl enable --now dnf-automatic.timer

Отключение SELinux
В данном курсе мы не будем рассматривать работу с системой безопасности SELinux.
Поэтому отключила его.
В файле /etc/selinux/config замените значение

![lab1scr19](https://github.com/user-attachments/assets/71a988d6-b9d8-4bc8-b926-fc00c03d699f)

SELINUX=enforcing
на значение

![lab1scr20](https://github.com/user-attachments/assets/06a8e42d-b6e0-4106-9aa7-b76cef7e34e2)

SELINUX=permissive
Перегрузила виртуальную машину:

sudo systemctl reboot

Настройка раскладки клавиатуры
Вошла в ОС под заданной вами при установке учётной записью.
Нажмала комбинацию Win+Enter для запуска терминала.
Запустила терминальный мультиплексор tmux:

tmux
Создала конфигурационный файл ~/.config/sway/config.d/95-system-keyboard-config.conf:

![lab1scr21](https://github.com/user-attachments/assets/82d1e75e-5c0c-4278-a45a-044f740984cf)

mkdir -p ~/.config/sway
touch ~/.config/sway/config.d/95-system-keyboard-config.conf
Отредактировала конфигурационный файл ~/.config/sway/config.d/95-system-keyboard-config.conf:

exec_always /usr/libexec/sway-systemd/locale1-xkb-config --oneshot
Переключила на роль супер-пользователя:

![lab1scr22](https://github.com/user-attachments/assets/c8834fa1-ac11-419f-ad4a-4f26f931a7a7)

sudo -i
Отредактировала конфигурационный файл /etc/X11/xorg.conf.d/00-keyboard.conf:

Section "InputClass"
            Identifier "system-keyboard"
            MatchIsKeyboard "on"
            Option "XkbLayout" "us,ru"
            Option "XkbVariant" ",winkeys"
            Option "XkbOptions" "grp:rctrl_toggle,compose:ralt,terminate:ctrl_alt_bksp"
EndSection
Использовала файловый менеджер mc и его встроенный редактор.
Перегрузила виртуальную машину:
sudo systemctl reboot

![lab1scr23](https://github.com/user-attachments/assets/78cc0ea2-2a23-41d8-9c40-edd889a79137)

# Установка имени пользователя и названия хоста
Запустила виртуальную машину и залогиньтесь.
Нажала  комбинацию Win+Enter для запуска терминала.
Запустила терминальный мультиплексор tmux:

tmux
Переключила на роль супер-пользователя:

sudo -i
Создала пользователя (вместо username укажите ваш логин в дисплейном классе):

![lab1scr24](https://github.com/user-attachments/assets/8c2a352b-0653-4455-af79-1d527fcab307)

adduser -G wheel username
Задала пароль для пользователя (вместо username укажите ваш логин в дисплейном классе):

passwd username
Установите имя хоста (вместо username укажите ваш логин в дисплейном классе):

hostnamectl set-hostname username
Проверила, что имя хоста установлено верно:

![lab1scr25](https://github.com/user-attachments/assets/f7b6fe05-3b10-4e4a-b3d5-d65658527f1e)

hostnamectl

Видео: Имя пользователя и хоста
RuTube: Имя пользователя и хоста

Youtube: Имя пользователя и хоста


Установка программного обеспечения для создания документации
Нажмала комбинацию Win+Enter для запуска терминала.
Запустила терминальный мультиплексор tmux:

tmux
Переключилась на роль супер-пользователя:

sudo -i

Работа с языком разметки Markdown
Средство pandoc для работы с языком разметки Markdown.
Установка с помощью менеджера пакетов:

sudo dnf -y install pandoc
Для работы с перекрёстными ссылками мы использовала пакет pandoc-crossref.
Пакет pandoc-crossref в стандартном репозитории отсутствует.
При установке pandoc-crossref следует обращать внимание, для какой версии pandoc он скомпилён.
Лучше установить pandoc и pandoc-crossref вручную.
Скачайте необходимую версию pandoc-crossref (https://github.com/lierdakil/pandoc-crossref/releases).
Посмотрела, для какой версии откомпилён pandoc-crossref.
Скачала соответствующую версию pandoc (https://github.com/jgm/pandoc/releases).
Распаковала архивы.
Обе программы собраны в виде статически-линкованных бинарных файлов.
Поместила их в каталог /usr/local/bin.

![lab1scr26](https://github.com/user-attachments/assets/52757ed6-fadf-4ac3-b29b-7567ce1f593d)

texlive
Установила дистрибутив TeXlive:

sudo dnf -y install texlive-scheme-full

# Список литературы.
1. Dash, P. Getting Started with Oracle VM VirtualBox / P. Dash. – Packt Publishing Ltd, 2013. – 86 сс.
2. Colvin, H. VirtualBox: An Ultimate Guide Book on Virtualization with VirtualBox. VirtualBox / H. Colvin. – CreateSpace Independent Publishing Platform, 2015. – 70 сс.
3. Vugt, S. van. Red Hat RHCSA/RHCE 7 cert guide : Red Hat Enterprise Linux 7 (EX200 and EX300) : Certification Guide. Red Hat RHCSA/RHCE 7 cert guide / S. van Vugt. – Pearson IT Certification, 2016. – 1008 сс.
4. Робачевский, А. Операционная система UNIX / А. Робачевский, С. Немнюгин, О. Стесик. – 2-е изд. – Санкт-Петербург : БХВ-Петербург, 2010. – 656 сс.
5. Немет, Э. Unix и Linux: руководство системного администратора. Unix и Linux / Э. Немет, Г. Снайдер, Т.Р. Хейн, Б. Уэйли. – 4-е изд. – Вильямс, 2014. – 1312 сс.
6. Колисниченко, Д.Н. Самоучитель системного администратора Linux : Системный администратор / Д.Н. Колисниченко. – Санкт-Петербург : БХВ-Петербург, 2011. – 544 сс.
7. Robbins, A. Bash Pocket Reference / A. Robbins. – O’Reilly Media, 2016. – 156 сс.
:::
