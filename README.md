# Это шпаргалка по Git

Чтобы тебе было удобнее взаимодействовать с командной строкой, мы подготовили шпаргалку.

## Навигация

* ```pwd``` (от англ. print working directory, «показать рабочую папку») — покажи, в какой я папке;
* ```ls``` (от англ. list directory contents, «отобразить содержимое директории») — покажи файлы и папки в текущей папке;
* ```ls -a``` — покажи также скрытые файлы и папки, названия которых начинаются с символа .;
* ```cd first-project``` (от англ. change directory, «сменить директорию») — перейди в папку ```first-project```;
* ```cd first-project/html``` — перейди в папку ```html```, которая находится в папке ```first-project```;
* ```cd ..``` — перейди на уровень выше, в родительскую папку;
* ```cd ~``` — перейди в домашнюю директорию ```(/Users/Username)```;
* ```cd /``` — перейди в корневую директорию.

## Работа с файлами и папками

### ***Создание***

* ```touch index.html``` (англ. touch, «коснуться») — создай файл ```index.html``` в текущей папке;
* ```touch index.html style.css script.js``` — если нужно создать сразу несколько файлов, можно напечатать их имена в одну строку через пробел;
* ```mkdir second-project``` (от англ. make directory, «создать директорию») — создай папку с именем second-project в текущей папке.

### ***Копирование и перемещение***

* ```cp file.txt ~/my-dir``` (от англ. copy, «копировать») — скопируй файл в другое место;
* ```mv file.txt ~/my-dir``` (от англ. move, «переместить») — перемести файл или папку в другое место.

### ***Чтение***

* ```cat file.txt``` (от англ. concatenate and print, «объединить и распечатать») — распечатай содержимое текстового файла ```file.txt```.

### ***Удаление***

* ```rm about.html``` (от англ. remove, «удалить») — удали файл ```about.html```;
* ```rmdir images``` (от англ. remove directory, «удалить директорию») — удали папку ```images```;
* ```rm -r second-project``` (от англ. remove, «удалить» + recursive, «рекурсивный») — удали папку ```second-project``` и всё, что она содержит.

## Работа с репозиторием

### ***Инициализирование***

* ```git init``` - Инициализируй репозиторий(сделай папку репозиторием);
* ```rm -rf .git``` - «Разгитить» папку, если что-то пошло не так;
* ```git status``` - Проверить состояние репозитория.

### ***Добавление***

* ```git add ``` - Добавление файла и подготовка его к сохранению;
* ```git add .```- Добавить всю текущую папку;
* ```git add --all``` - Добавить все фйлы в репозитории;
* ```git add todo.txt```- Добавление только файлаа ```todo.txt```.


### ***Коммит***

* ```git commit``` - Выполнить коммит;
* ```git commit -m "Мой первый коммит"``` - Выполнить коммит и написать соообщение;
* ```git commit --amend --no-edit``` - Дополнить коммит новыми файлами без сообщения, не создавая новый коммит. Также можно добавить изменения в уже добавленном в коммит файле;
* ```git commit --amend -m "Какое-то сообщение"``` - Тоже самое, что сверху, но с сообщением.

### ***История коммитов***

* ```git log``` - Посмотреть историю коммитов;
* ```git log --oneline``` - Посмотреть историю коммитов в сокращенном виде.

## Работа с GitHub

### ***Генерация SSH ключа***

* ```ls -la .ssh/``` - Вывести список созданных ключей(если создавали). Ключи находятся в корневой дирректории;
* ```ssh-keygen -t ed25519 -C "электронная почта, к которой привязан ваш аккаунт на GitHub"``` - Генерировать SSH ключ;
* ```ssh-keygen -t rsa -b 4096 -C "электронная почта, к которой привязан ваш аккаунт на GitHub"``` - Другой способ, если первый не работает;
* ```ls -a .ssh/``` - Вывести список SSH ключей.

### ***Связывание локального и удаленного репозитория***

* ```git remote add``` - Привязать удалённый репозиторий к локальному;
* ```git remote add origin git@github.com:%ИМЯ_АККАУНТА%/first-project.git``` - Команде необходимо передать два параметра: имя удалённого репозитория и его URL. В качестве имени используйте слово ```origin```. А URL скопировать со страницы удалённого репозитория;
* ```git remote -v``` - Убедиться, что репозитории связаны. В выводе должны появиться две строчки с оккончаниями (fetch) и (push).

### ***Синхронизирование локального и удаленного репозитория***

* ```git push``` - Отправить изменения на удалённый репозиторий;
* ```git push -u origin main``` - В первый раз необходимо вывести команду ```git push``` с флагом ```-u``` и параметрми ```origin master(main)```

## Как откатиться назад, если «всё сломалось»

### ***Выполнить unstage изменений***

* ```git restore --staged <file>``` - Допустим, вы создали или изменили какой-то файл и добавили его в список «на коммит» (staging area) с помощью ```git add```, но потом передумали включать его туда. Убрать файл из ```staging``` поможет команда ```git restore --staged <file> ```(от англ. restore — «восстановить»).

### ***«Откатить» коммит***

* ```git reset --hard <commit hash>``` - Иногда нужно «откатить» то, что уже было закоммичено, то есть вернуть состояние репозитория к более раннему. Для этого используют команду ```git reset --hard <commit hash>``` (от англ. reset  — «сброс», «обнуление» и hard — «суровый»).

### ***«Откатить» изменения, которые не попали ни в staging, ни в коммит***

* ```git restore <file>``` - Может быть так, что вы случайно изменили файл, который не планировали. Теперь он отображается в ```Changes not staged for commit (modified)```. Чтобы вернуть всё «как было», можно выполнить команду ```git restore <file>```.

## Изменение файлов

### Просмотр изменений

* ```git diff``` - Допустим, вы собираетесь сделать коммит, но хотите проверить какие изменения туда попадут. Прежде чем добавить этот файл в ```staged```, изпользуйте ```git diff``` для проверки изменений. Работает только при состоянии файла ```modified```;
* ```git diff --staged```- Если вы уже использовали ```git add <file name>``` и добавили файл в ```staged```, то проверить изменения можно, использовав ```git diff --staged```;
* ```git diff <first commit hash> <second commit hash>``` - Если вы уже сделали коммиты и хотите посмотреть разницу между ними, то используйте эту опцию. Вместо хеша последнего коммита можно использовать HEAD.

### Дописать строку в файл

* ```echo "Какой-то текст"``` - Просто выведет текст в терминале;
* ```echo "Какой-то текст" >> <file name>``` - Допишет строку с текстом в уазанном файле;
* ```echo "Какой-то текст" > <file name>``` - Удалит все строки в файле и оставит только одну введнную вами строку
