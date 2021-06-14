## Подготовка к бассейну Школы 21
В данном репозитории представлены материалы, собранные при подготовке к бассейну Школы 21 в Новосибирске, а также примеры решения задача на языке С. Задачи никак не связаны с заданиями Школы 21, найдены на просторах интернета. Решения выполнены владельцем репозитория и не являются единственным верным вариантом. Репозиторий писался на основании той информации, которую можно найти и собрать по кусочкам на тех же простора интернета. Может не являться истинной, т.к. в Новосибирском кампусе обучение может отличаться от Московского и Казанского кампусов.

#### Оглавление <a name="content"></a>
0. [Введение](#intro)
1. [Работа с терминалом](#terminal)
	- [Основные команды навигации в терминале](#termCommand)
	- [Справка о командах](#help)
	- [Прочее](#other)
2. [Устанавливаем и настраиваем vim](#vim)
    - [Работа в vim](#workVim)
	- [Перемещение по файлу](#navigation)
	- [Ввод текста](#enterText)
	- [Удаление и вставка](#deletAndPaste)
	- [Отмена изменений](#undo)
	- [Выход из vim](#quit)
	- [Терминал в vim](#term)
	- [Заголовок школы](#header)
	- [Решение некоторых проблем](#solveProblems)
	- [Дополнительный материал](#addMaterial)
3. [Компилятор gcc](#gcc)
4. [Устанавливаем и настраиваем norminette](#norminette)
5. [Работа с git](#git)
6. [Hello, World!](#helloWorld)

### Введение <a name="intro"></a>
Если ты нашёл этот репозиторий, то наверняка уже много прочитал различной информации про Школу 21, про франшизу Школы 42, про peer-to-peer (P2P) метод обучения, про бассейн (интенсив) и т.д. и т.п. Скорей всего ты уже прошёл первый отбор: 2 игры, видео-интервью и онлайн встречу. Перед тобой следующий этап - это бассейн. Как раз о нём я и постараюсь рассказать, основываясь на информации, которую смог найти сам. Опишу этапы моей подготовки.

Первое, что нужно понять, - вся работа во время интенсива будет проходить на iMac, компьютерах от Apple. Из чего можно сделать вывод, что в работе будут использоваться bash-команды (но это неточно), может быть ещё установлена zsh-командная оболочка. Командные оболочки позволяют работать в терминале с операционной системой с помощью простых команд без GUI. Прежде всего командные оболочки нужны системным администраторам для работы с серверами, где GUI вообще по факту не нужен. Но и программистам навыки работы с терминалом очень пригождаются в работе. Потому нужно научиться работать с Bash. Один из способов потренироваться, это через терминал дистрибутивов Linux, в которых уже предустановлен Bash. Будете ли вы устанавливать новую ОС, или ставить виртуальную машину, или пользоваться Live-режимом с USB-флешки - это решать вам.  

Второе - языком программирования интенсива является язык Си. Да, язык не самый популярный у новичков и не прост в понимании для начинающих. Но таковы правила Школы 21, начинать с азов. Это компилируемый статически типизированный язык программирования, потому для работы с ним нужен компилятор. По разным источникам в Школе 21 может быть компилятором как Clang, так и gcc. Я для тренировки выбрал gcc.

Третье - текстовые редакторы. На интенсиве, скорей всего, будут доступны только nano, emacs и vim. Советую заранее выбрать один из этих редакторов и научиться в нём работать, чтобы не тратить драгоценное время на интенсиве. Я выбрал редактор vim. Мне так вкусней.

Четвёртое - правила написания кода в Школе 21. Они есть и их нужно соблюдать, иначе можно отхватить 0 баллов за выполнение задания. Да, всё настолько строго, да, для новичков.

Пятое - работа с git. Git - это система управления версиями. У Git две основных задачи: первая - хранить информацию о всех изменениях в вашем коде, начиная с самой первой строчки, а вторая - обеспечение удобства командной работы над кодом. Каждый программист должен уметь пользоваться Git-ом. Именно сейчас вы читаете данный репозиторий на веб-сервисе GitHub, который основан на системе контроля версий Git. На бассейне работа будет завязана на локальном git-репозитории, с помощью git-команд нужно будет отправлять решения на проверку.

И наконец, шестое - первая программа "Hello, World!", на которой я покажу все описанные выше инструменты. 

P.S. Все примеры и команды, показанные мной ниже, я выполнял в терминале дистрибутива Linux Mint 20.1 MATE в командной оболочке Bash. 

[Оглавление](#content)

### 1 Работа с терминалом <a name="terminal"><a>

Под терминалом принято понимать окружение, где можно вводить команды и получать на них ответ, это может быть физический терминал или терминал на компьютере.

Запуск терминала в Linux Mint осуществляется сочетаниями клавиш:

	Ctrl + Alt + T

Запуск терминала в macOS осущестляется другой комбинаций (не проверял):

	Command(⌘) + T

Другой способ запуска терминала в macOS:

	Ctrl + пробел

Во всплывающем окошке введите слово «Терминал» (terminal). После того, как увидите нужное приложение, просто кликните на него (не проверял).

Так выглядит терминла в Linux Mint:
![Terminal](https://ibb.co/sH3DVM0)

**Основные команды навигации в терминале:** <a name="termCommand"></a>

Узнать, в какой рабочей папке вы находитесь:
```
$ pwd
```
Вывести список файлов и каталогов в рабочей папке:
```
$ ls
```
Вывести список файлов и каталогов в рабочей папке, включая скрытые:
```
$ ls -a
```
Вывести список файлов и каталогов с полной информацией о них в рабочей папке, включая скрытые:
```
$ ls -all
```
Команда cd используется очень часто при работе с папками в терминале. Она позволяет сменить текущую папку на произвольную. Можно использовать чтобы не набирать длинные пути, также она необходима при компиляции. По умолчанию, текущая папка - домашняя.

Перейи в подпапку домашней папки:
```
$ cd Загрузки/
```
Вернуться в предыдущую папку:
```
$ cd -
```
Перейти в родительский каталог:
```
$ cd ..
```
Быстрый переход в домашнюю папку:
```
$ cd
```
Создание файла в рабочей папке:
```
$ touch file_name.expansion
```
Создание каталога в рабочей папке:
```
$ mkdir dir_name
```
Удаление файла в рабочей папке:
```
$ rm file_name
```
Удаление каталога и рекурсивно всё его содержимое:
```
$ rm -r dir_name
```
Переименовать файл:
```
$ mv file_name file_new_name
```
Переместить файл в другой каталог:
```
$ mv file_name dir_name/
```
Копировать файл в рабочую папку:
```
$ cp file_name copy_file_name
```
Копировать каталог в другой каталог:
```
$ cp -a dir_name_1/ dir_name_2/
```
Копировать файл в каталог:
```
$ cp frile_name dir_name/
```

**Справка о командах** <a name="help"></a>

Если не знаешь, как работает команда и её параметры, спроси у "мужика":
```
$ man cp
$ man ls
$ man mkdir
...
```
Чтобы узнать о параметрах команды, используйте параметр `--help`:
```
$ ls --help
$ cd --help
$ rm --help
...
```

**Прочее** <a name="other"></a>

Команда `bg` позволяет посмотреть процессы, которые выполняются в фоне. Если вы нажмете сочетание клавиш `Ctrl+Z`, то утилита будет свернута в фоновый режим (такое может случиться при работе в vim). Этой командой вы можете посмотреть последний свёрнутый процесс и его id для данной оболочки.
```
$ bg
```
Посмотреть все запущенные процессы, которые работают на заднем фоне:
```
$ jobs
```
Эта команда позволяет восстановить процесс из фона, в параметрах ей нужно передать только идентификатор нужного процесса, который вы можете узнать с помощью `bg` или `jobs`.
```
$ fg id_process
```
[Оглавление](#content)

### 2 Устанавливаем и настраиваем vim <a name="vim"><a>

**Vim** (сокр. от **V**i **Im**proved, произносится «вим») — свободный текстовый редактор, созданный на основе более старого vi. Ныне это мощный текстовый редактор с полной свободой настройки и автоматизации, возможными благодаря расширениям и надстройкам. Пользовательский интерфейс Vim’а может работать в чистом текстовом (консольном) режиме.

Прежде чем устанавливать vim, необходимо обновить базы данных пактов (необязательно), чтобы установить последнюю версию vim:
```
$ sudo apt update
```
Установка vim:
```
$ sudo apt install vim
```
Узнать версию vim, также выводит информацию о пользовательсом файле vimrc, он нам понадобиться для настройки vim:
```
$ vim --version
```
Открыть туториал по vim:
```
$ vimtutor
```
Создать файл через vim в рабочей папке:
```
$ vim file_name.expansion
Пример:
$ vim main.c
```
#### Работа в vim <a name="workVim"></a>

**Основные режимы работы**

*Обычный режим* - перемещение по файлу, стирание текста и другие редактирующие функции. Это - основной режим, только из него можно сразу перейти в другие режимы. Для возврата в основной режим из любого другого режима:

	ESC, иногда 2 раза
	Ctrl + [

*Режим ввода* - ввод текста. Как только завершается ввод текста, принято сразу возвращаться в обычный режим. Заметьте, что стирание и ввод текста происходит в двух разных режимах. Переход в него из обычного режима:

	i
	Insert

*Командный режим* - команды (операции с файлом, поиск и замена, настройка редактора…). Переход в него из обычного режима:

	Shift + :

*Режим поиска* - ввод поискового запроса. Переход в него из обычного режима:

	/ , поиск от курсора до конца документа
	? , поиск от курсора до начала документа
	n - повторить поиск
	N - повторить поиск назад

*Визуальный режим* - режим выделения текста:

	v + влево или вправо стрелками
	Shift + v , вся строка целиком
	Ctrl + v , выделение прямоугольником часть текса

**Перемещение по файлу** <a name="navigation"></a>

Команды, которые использую я (их может быть достаточно для комфортной работы в vim, больше команд можете найти в `vimtutor` ):

	Для перемещение курсора можно использовать стрелки вверх, вниз, вправо и влево (см. рисунок ниже)

![Стрелки](https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Flinchakin.com%2Ffiles%2Fword%2F1000%2F15%2F1.jpg&f=1&nofb=1)

	Ctrl + f - перейти на сраницу (экран) вниз
	Ctrl + b - перейти на страницу (экран) вверх
	0 ("ноль") - перейти в начало текущей страки
	$ - перейти в конец текущей строки
	Ctrl + стрелка вправо - перейти на слово вправо
	Ctrl + стрелка влево - перейти на слово влево
	Shift + } - перейти на абзац вниз
	Shift + { - перейти на абзац вверх
	gg - перейти в начало файла
	G - перейти в конец файла
	number + G - перейти на конкретную строку number
	
**Ввод текста** <a name="enterText"></a>

Следующие команды переводят редактор в режим ввода:

	i - перейти в режим в ввода с текущей позиции
	I - переместиться в начало строки и перейти в режим ввода
	A - переместиться в конец строки и перейти в режим ввода
	S - удаляет всю текущую строку и переходит в режим ввода

**Удаление и вставка** <a name="deletAndPaste"></a>

	x - удалить символ под курсором вправо;
	X - удаляет символ влево;
	dd - вырезать текущую строку;
	C - удаляет текст с екущего положения курсора до конца строк и переходит в режим ввода
	yy или Y - копирование текущей строки в буфер
	y - копирование выделенной строки в буфер
	p - вставка содержимого буфера под курсором
	P - вставка содержимого буфера перед курсором
	J - слияние текущей строки со следующей

**Отмена изменений** <a name="undo"></a>

	u - отмена последней команды
	Ctrl + r - вернуть последние изменения 

**Выход из vim** <a name="quit"></a>

Наконец, дошли до самого интересного, выхода из редактора vim, который является проблемой для новичка:

	:q! - выйти без сохранения
	:wq - записать файл и выйти
	ZZ - записать файл и выйти (если файл не изменяли, то записи не будет)

**Терминал в vim** <a name="term"></a>

В vim можно открыть терминал, что позволяет удобно одноврменно писать код и компилировать:

	:term - открыть терминал в vim
	Ctrl + w - переключаться между окнами

**Заголовок Школы 21 (Школы 42)** <a name="header"></a>

Во всех файлах должен быть заголовок (heder), который установлен правилами Школы (см.на рисунке ниже).

![Header](https://ibb.co/NY1xgkz)

Для создания заголовка 42header необходимо использовать плагин, который скачивается и устанавливается с помощью пакетного менеджера Vundle.

> Плагин нужен только тем, кто работает на своём пк/ноутбуке. На компьютерах школы всё и так прекрасно работает.

Чтобы скачаь Vundle, понадобиться установить систему контроля версий Git (как им пользоваться, рассказываю  ниже):

	$ sudo apt install git

Теперь создадим необходимую директорию и скачаем туда менеджер Vundle:

	$ mkdir -p ~/.vim/bundle
	$ git clone https://github.com/VundleVim/Vundle.vim.git ~/.vim/bundle/Vundle.vim

Далее настраиваем Vim и пактный менеджер Vundle, а также запишем в очередь на установку плагин 42header. Для этого создадим в каталоге ~/.vim файл vimrs:

	$ cd .vim/
	$ vim vimrc

Был созда и сразу открыт в редакторе vim файл vimrc, в который необходимо записать следующие настройки:

	set number
	set cursorline
	set cursorcolumn
	set autoindent
	set cindent
	highlight ExtraWhitespace ctermbg=red guibg=red
	match ExtraWhitespace /\s\+$\|\s+\s{1}/highlight MoreThan80 ctermbg=blue guibg=blue
	:2match MoreThan80 /\%81v.\+/
	set tabstop=4
	set shiftwidth=4

	set nocompatible
	filetype off
	set rtp+=~/.vim/bundle/Vundle.vim
	call vundle#begin()
	Plugin 'VundleVim/Vundle.vim'
	Plugin 'pandark/42header.vim'
	
	" Add plugins here

	call vundle#end()
	filetype plugin indent on

Теперь необходимо установить и обновить прописанные в vimrc плагины. Откройте vim и выполните в нём команду:

	$ vim
	:PluginInstall

Пропишем в файле настроек командной оболочки имя пользователя $USER и почту $MAIL для нашего заголовка 42header. Открываем .bashrc (или .zshrc, если у вас zsh): 

	$ vim .bashrc

и прописываем вконце строки:

	export USER=тут_будет_ваш_login
	export MAIL=тут_будет_ваш_email

После сохранения .bashrc, его необходимо перезапустить:

	$ source .bashrc

Проверяем. Запускаем vim и прописываем команду:

	:FortyTwoHeader

Чтобы поменять команду с `:FortyTwoHeader` на команду `:Stdheader`, изменим строку 187 в:

	$ vim ~/.vim/bundle/42header.vim/plugin/42header.vim

на:

	command! Stdheader call s:fortytwoheader()

Чтобы сделать печать заголовка при нажатии на кнопку `F5`, пропишем в файле vimrc:

	nmap <f5> :Stdheader<CR


**Решение некоторых проблем** <a name="solveProblems"></a>

Не работает кнопка `Backspace`.
Откройте vim и пропишите команду:

	:set backspace=indent,eol,start

**Дополнительный материал** <a name="addMaterial"></a>

Другие настройки vim:
[Настройка vim](https://losst.ru/nastrojka-vim)

Установка цветовой схемы Drakula:
[Drakula](https://draculatheme.com/vim)

Так выглядит цвеовая схема Drakula:
![Цветовая схема Drakuls](https://ibb.co/tLpvXHm)

Выбор встроенных в vim  цветовых схем:
```
:colorscheme + Tab
```

Узнать текущую цветовую схему:
```
:color
```

[Оглавление](#content)

---
### 3 Компилятор gcc <a name="gcc"><a>
...

[Оглавление](#content)

---
### 4 Устанавливаем и настраиваем norminette <a name="norminette"><a>
...

[Оглавление](#content)

---
### 5 Работа с git <a name="git"><a>
...

[Оглавление](#content)

---
### 6 Hello, World! <a name="helloWorld"><a>
...

[Оглавление](#content)

---
