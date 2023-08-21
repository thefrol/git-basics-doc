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
