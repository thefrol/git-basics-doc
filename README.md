# Основы `git`

Это небольшое руководство и шпаргалка по `git`, собранное из курса [Основы Git](https://practicum.yandex.ru/git-basics/)

# Перед началом

Чтобы освоить `git` все-таки хорошо знать командную строку. Если такие команды как `touch`, `ls`, `rm`, `cd` вызывают в вас чувство недоумения и ужас, то стоит попробовать свои силы в командной оболочке, тут может помочь эта [статья](https://habr.com/ru/articles/501442/)

В конце концов `git` это консольная команда, работает без графического интерфейса. И чтобы научиться ей пользоваться, вам надо уметь запускать саму консоль и в ней ориентироваться, иначе все дальнейшее изложение покажется вам билебердой. 

# Система контроля версий. Что такое `git`

Глеб написал хорошую статью, а ночью словил приступ ненависти к себе и всю ее переписал. Утром эту статью перечитал друг, и сказал, что раньше было лучше. Как откатиться к прошлой версии. Что там было? Может быть у кото-то в месседжере сохранилась часть. Остальное можно дописать. Глеб в ужасе. 

Такой проблемы не возникло бы, если бы Глеб пользовался системой контроля версий. Тогда бы у него был бы список изменений статьи с самого старта до последней версии. И если что мог бы откатиться. 

> Например, те же Яндекс.Документы имеют встроенную систему контроля версий.

`git` это система контроля версий. Это программа которая запоминает версии ваших файлов. И знает различия между этими версиями, может если что откатить файл к нужной версии.

Системы контроля версий очень хорошо прижились в программировании, потому что не просто позволяют программистам откатываться к прошлым версиям своих проектов, но и работать совместно над кодом.

Дело в том, что система контроля версий запоминает какие кусочки файлов были изменены, и потом может собрать итоговый файл от Глеба и Стаса, учитывая все их правки. Даже если никто из них еще не видел все правки вместе. А если возникнет конфликт правок, то поможет его опознать и разрешить. 

> Ко всему прочему `git` помогает осмысленно программировать. К каждому `коммиту`, коммиту требуется сопроводительное сообщение. Что сейчас было изменено. На первых порах очень сложно описать: а что я сейчас сделал в коде. Со временем становится проще, да и сам начинаешь понимать, что именно делаешь лучше.

# Основые команды

## Создание репозитория `git init`

Чтобы создать репозитой нужно в папке выполнить команду `git init`. Имейте в виду, что репозиторий охватывает ту папку в которой он был создан, и на все подкаталоги. Так что создавайте репозиторий в самой старшей папке текущего проекта. 

Это одна из самых редких команд. После создания в папке появится скрытая папка `.git`, в которой будет храниться вся служебная информация о репозитории. 

> Не стоит заводить вложенные репозитории, это может свести с ума git

Если нужно отменить репозиторий, нужно удалить папку `.git`

```bash
rm -rf .git
```

После этого вся информация о коммитах пропадет

## git status

Эта команда используется, чтобы узнать текущий статус файлов в репозитории:
+ Инициализирован ли репозиторий
+ какая ветвь активна
+ Какие файлы отслеживаются
+ какие будут добавлены в коммит
+ а какие не будут
 — вот на такие вопросы поможет ответить `git status`

 ```bash
On branch master // ветвь называется master
Your branch is up to date with 'origin/master'. // синхронизирована с удаленным репозиторием

Changes not staged for commit: // изменения, которые не войдут в коммит
  (use "git add <file>..." to update what will be committed) // подсказки
  (use "git restore <file>..." to discard changes in working directory)
        modified:   README.md // вот этот файл, что вы читаете изменен, но в коммит не добавлен пока

no changes added to commit (use "git add" and/or "git commit -a") // содержание коммита
 ```

А если, например, запустить в каталоге, в котором нет репозитория получим вот такое сообщения об ошибке

```bash
fatal: not a git repository (or any of the parent directories): .git
```

## Изменения и коммиты

## Добавление файла `git add`

Чтобы подготовить файл к оправке в репозиторий, нужно воспользоваться коммандой `git add`, например

```bash
git add README.md
```

Ещё можно вопспользоваться командой `git add --all`, тогда к отправке будут подготовленны все измененные с последнего коммита файлы. Ещё говорят файл **добавлен в индекс**. Я не просто так использую термин `подготовлены к отправке`. По сути команда `add` ещё не запоминает файлы, она их просто собирает, а чтобы сфотографировать и запомнить изменение, нужно воспользоваться следующей командой

## git commit

Если `git add` приглашала всех людей встать в кадр фотоаппарата, то `git commit` уже большая белая "сделать фотографию".

```bash
git commit -m "Сообщение"
```

После запуска этой команды `git` запомнит изменения, сделанные в проекте (когда, кем, и где) и к ним впоследствии можно будет вернуться. Изменения запоминаются как бы кусочками, не просто прошлая версия файла и новая, а где в старом файле были сделаны изменения: какая строка удалена, какая добавлена.

Самая распространенная ошибка при попытке коммита, это забыть добавить файлы в индекс(подготовить к коммиту), тогда коммит не получится. А в целом можно пользоваться командой

```bash
git commint -am "Сообщение"
```

Она добавит все файлы из текущей директории в индекс, и нажмет за затвор фотоаппарата.

Сообщение - очень важная часть коммита, она позволяет быстро посмотреть какие изменения сделаны, когда и кем, о чем мы можем убедиться, запустив следующую команду

## git log

## Ветки

#SSH

## добавление удаленного репозитория `git add remote`

## отправка `git push`

# Правила хорошего тона
## README.md


# Автор

Гайд был написан Дмитрием Фроленко, августовскими вечерами 2023 г на диване