# Инструкция по работе с GIT
---
## Содержание
1. [Как задать имя пользователя и адрес электронной почты](#title1)
2. [Инициализация репозитория](#title2)
3. [Добавление файлов в индекс](#title3)
4. [Проверка статуса репозитория](#title4)
5. [Создание коммита](#title5)
6. [Просмотр истории коммитов с изменениями](#title6)
7. [Работа с коммитами](#title7)
8. [Просмотр изменений до коммита](#title8)
9. [Удаление отслеживаемых файлов из текущего рабочего дерева](#title9)
10. [Cоздание, удаление и перемещение по веткам](#title10)
11. [Дополнительная информация для работы](#title11)
12. [Работа с удаленными репозиториями](#title12)
---

### <a id="title1">1. Как задать имя пользователя и адрес электронной почты</a>
Имя пользователя нужно, чтобы привязывать коммиты к имени. Задать или изменить имя пользователя можно с помощью команды git config. Новое имя будет автоматически отображаться в последующих коммитах, отправленных на Git через командную строку. 
```sh
git config --global user.name "Указать имя"
```
Кроме того, можно изменять адрес электронной почты, привязанный к коммитам Git. Новый адрес электронной почты будет автоматически отображаться во всех дальнейших коммитах.
```sh
git config --global user.email "Указать емайл"
```
><span style="color:green">*Для чего это нужно и можно ли указывать рандомное имя?*</span>
>
> <span style="color:green">*указывать рандомное имя можно, но при командрой работе, особенно в крупных компаниях с файлом может работать не один специалист, поэтому желательно указывать реальное имя и рабочую почту, чтобы любому было понятно чьи были последние коммиты и как связаться с этим человеком.*</span>
### <a id="title2">2. Инициализация репозитория</a>
Создать пустой репозиторий Git или вновь инициализировать существующий можно параметром init. При инициализации он создаст скрытую папку. В ней содержатся все объекты и ссылки, которые Git использует и создаёт в истории работы над проектом.
```sh
git init
```
><span style="color:green">*Стартовая команда. Без этой команды не начнется контроль версий документа*</span>
### <a id="title3">3. Добавление файлов в индекс</a>
Индекс или стейджинг — это невидимая зона, туда сохраняются подготовленные к коммиту изменения. Добавляются изменения в индекс командой:
```sh
git add .\"Имя файла"
```
><span style="color:green">*Имя файла не обязательно набирать полностью, если отсутствуют похожие названия - достаточно ввести первые 4-5 символов и нажать Tab система дозаполнит имя файла.*</span>
### <a id="title4">4. Проверка статуса репозитория</a>
Просмотреть статус репозитория можно по ключевому слову "status"- его действие распространяется на подготовленные, неподготовленные и неотслеживаемые файлы. 

Команда показывает файлы состояния в рабочем каталоге и индексе: какие файлы изменены, но не добавлены в индекс; какие перспективы коммита в индексе.
```sh
git status
``` 
### <a id="title5">5. Создание коммита</a>
Отправляются изменения в репозиторий командой:
```sh
git commit -m «комментарий»
```
### <a id="title6">6. Просмотр истории коммитов с изменениями</a>
Просматривать изменения, внесённые в репозиторий, можно с помощью параметра log. Он отображает список последних коммитов в порядке выполнения.(вверху списка будет находиться последняя версия с указателем <span style="color:red">HEAD</span> - master). Показать журнал коммитов можно командой:
```sh
git log
```
для отображения сокращенной версии журнала используется команда:
```sh
git log --oneline
```
### <a id="title7">7. Работа с коммитами</a>
После отображения журнала коммитов естьь возможность переместиться в любую из версий, для этого необходисо задать команду:
```sh
git checkout идентификатор комита
```
><span style="color:green">*Если использовалась команда git log, то в данном случае нет необходимости копировать длинный индентификатор целиком. Достаточно скопировать первые 4-5 символов.*</span>

Для возвращения к рабочей (последней версии) необходимо задать команду 
```sh
git checkout master
``` 
### <a id="title8">8. Просмотр изменений до коммита</a>
Можно просматривать список изменений, внесённых в репозиторий, используя параметр diff. По умолчанию отображаются только изменения, не подготовленные для фикcации.
```sh
git diff
```
><span style="color:green">*Для выхода из команды необходимо нажать одну из следующих клавиш "q", "z" или "CTRL+Z"(в моем случае сработало именно CTRL+Z).*</span>
### <a id="title9">9. Удаление отслеживаемых файлов из текущего рабочего дерева</a>
Чтобы удалить неотслеживаемые файлы, мы должны использовать команду git clean с флагом -f.
```sh
git clean -f
```
><span style="color:green">*На семинаре были предложены две команды для удаления неотслеживаемого файла:*</span>
>* *del - для Windows*
>* *rm - для Linux, MacOn*
>
><span style="color:red">*Но ни один из предложенных вариантов не был рабочим. После нескольких тестов была найдена команда (git clean -f), удаляющая неотслеживаемый файл.* </span>
>
>Дополнительно про удаление можно прочитать [тут](https://translated.turbopages.org/proxy_u/en-ru.ru.e4dde08c-666d995b-515725ab-74722d776562/https/www.geeksforgeeks.org/how-to-remove-local-untracked-files-from-current-git-working-tree/).

### <a id="title10">10. Cоздание, удаление и перемещение по веткам</a>
Команда, отображающая текущие ветки:

```sh
git branch
```
> <span style="color:green"> _Символ * указывает на ту ветку, в которой мы работаем._

Создать новую ветку:
```sh
git branch "Название ветки"
```
Переключение между ветками через команду:
```sh
git checkout "Наименование ветки"
```
Слияние веток:

```sh
git merge "Наименование ветки"
```
> <span style="color:green">_Для корректности слияния необходимо сначала перейти на ветку master, после чего ввести команду merge и указать имя файла, который будет вливаться в ветку master._ </span>

Удаление ветки:

```sh
git branch -d "Наименование ветки, которую нужно удалить"
```
Просмотр коммитов всего дерева: 

```sh
git log --graph
```

или

```sh
git log --oneline --graph
```

### <a id="title11">11. Дополнительная информация для работы</a>
Упростить работу с терминалом можно используя стрелки вверх и вниз, которые перебирают ранее используемые в терминале команды.

Выше были указаны основные команды для работы с GIT.

Краткая логическая схема работы с git-репозиторием может выглядеть так:

![Схема](https://static.1cloud.ru/img/blog/948.png)

```sh
cd ~/Desktop/"наименование папки"
```
Более широкий список команд и примеры их использования можно посмотреть дополнительно по [ссылке](https://habr.com/ru/companies/ruvds/articles/599929/).


## <span style="color:yellow">Отработка ситуаций (тестирование)</span>

<span style="color:blue">"Здесь будет добавлен иной текст. Чтобы создать и отработать конфликтную ситуацию.
То есть в ветке lists  и в ветке master в одном и том же разделе внесена разная информация. Теперь проведем тест на слияние и посмотрим, что случится:"</span>_(Текст из ветки master)_

<span style="color:yellow">"Создаем конфликт для теста."</span>_(Текст из ветки lists)_

### _Итог:_ 

![Результат слияния](conflict.jpg)

Далее пользователь решает для себя самостоятельно оставляет ли он один из вариантов или оставляет оба варианта.
Над выделенными областями есть функциональные кнопки для выбора, можно воспользоваться как ими, так и в ручном режиме отредактировать текст.

### <a id="title12">12. Работа с удаленными репозиториями</a>

копирование репозитория с GitHub
```sh
git clone <вставляем адрес с гитХаб>
```
Примечания на GitHub основная ветка называется не  master, а main.

Создание новой папки
```sh
mkdir <название новой папки>
```

Переименование ветки мастер в мэин

```sh
git branch -M main
```

устоновка репозитория по умолчанию

```sh
git remote add origin <ссылка с GitHub>
```

отправление информации с локального репозитория на сервер

```sh
git push -u origin main
```
проверить привязку удаленного репозитория

```sh
git remote -v
```
посмотреть информацию о удаленном репозитории

```sh
git remote show origin
```
получение информации с удаленного репозитория

```sh
git pull
```

слияние с браузером с конфликтом

```sh
git pull --rebase
```