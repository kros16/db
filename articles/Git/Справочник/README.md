# Система контроля версий Git

Справочник по коммандам git [статья на Хабре](http://habrahabr.ru/post/60347/)


### 1. Базовые команды

**`git help commandName`** &ndash; справка git комманд  

**`git status`** &ndash; статус git [ Главная комманда ]  
**`git status --untracked-files=all`** &ndash; показать все untracked-files  

**`git init`** &ndash; новый репозиторий


### 2. Комманды конфигурации

**`git config --list`** &ndash; список всех настроек  

**`git config --global user.name "Vladyslav Krasovsky"`** &ndash; глобальная настройка имени автора  
**`git config --global user.email "v.o.krasovsky"`** &ndash; глобальная настройка email автора  

**`git config --global core.editor "'D:\Soft\Portable\ST3\sublime_text.exe' -multiInst -notabbar -nosession -noPlugin"`** &ndash; глобальная настройка редактора комментариев  

**`git config --global merge.tool kdiff3`** &ndash; глобальная настройка утилиты слияния веток  
**`git config --global mergetool.kdiff3.cmd '"C:\\Program Files\\KDiff3\\kdiff3" $BASE $LOCAL $REMOTE -o $MERGED'`** &ndash; глобальная настройка пути утилиты  

**`git config --global push.default matching`** &ndash; глобальная настройка для push  

**`git config --system core.autocrlf false`** &ndash; отключение: warning: LF will be replaced by CRLF


### 3. Файлы

**`git add .`** &ndash; добавление всех файлов в индекс  
**`git add fileName`** &ndash; добавление файла в индекс  
**`git add "*.php"`** &ndash; добавление всех php файлов в индекс  

**`git rm --chached fileName`** &ndash; удаление файла из индекса  
**`git rm -r --cached folderName`** &ndash; удаление папки (рекурсивно) можно сделать так  
**`git rm --cached fileName`** &ndash; удаление файла из git-репозитория без его физического удаления  


### 4. Совершение коммита

**`git commit -a -m"comment"`** &ndash; коммит всех файлов, с комментарием  
**`git commit -m"comment"`** &ndash; коммит проиндексированных файлов + коммент  

**`git reset`** &ndash; возврат к определенному коммиту, откат изменений, «жесткий» или «мягкий»  
**Пример:**
```
	1. git commit… — некорректный коммит; 
	2. git reset --soft HEAD^ — переходим к работе над уже совершенным коммитом, сохраняя все состояние проекта и проиндексированные файлы 
	3. edit WRONGFILE 
	4. edit ANOTHERWRONGFILE 
	5. add.
	6. git commit -c ORIG_HEAD — вернутся к последнему коммиту, будет предложено редактировать его сообщение. Если сообщение оставить прежним, то достаточно изменить регистр ключа -с:
	7. git commit -C ORIG_HEAD
```


### 5. Работа с ветками

**`git checkout -- fileName`** &ndash; откат untracked файла, до состояния из репозитория  
**`git checkout -b new_f`** &ndash; создание новой ветки и переход в нее  
**`git checkout branchName`** &ndash; переключиться на ветку  

**`git branch`** &ndash; просмотр веток  
**`git branch new_f2`** &ndash; создание новой ветки  
**`git branch -v`** &ndash; подробный просмотр веток  

**`git merge branchName`** &ndash; слияние веток [ Добавит указанную ветку к текущей ]  
**`git mergetool`** &ndash; запус утилиты слияния веток [ Если авто-слияние не отработало ]


### 6. Логи

**`git log`** &ndash; история коммитов [ Выход из журнала - клавиша Q ]  
**`git log --pretty=format:"%h - %an, %ar : %s"`** &ndash; история коммитов в заданном формате  
**`git log --since=2.weeks`** &ndash; история коммитов за 2 недели  
**`git log -p -2`** &ndash; показать изменения в 2 коммитах


### 7. Удаленный репозитарий

**`git remote -v`** &ndash; удаленные репозитории  
**`git remote add origin https://kros16@bitbucket.org/kros16/lider.git`** &ndash; добавление нового репозитория [*remote* - удаленный; *origin* - название]  

**`git push -u origin master`** &ndash; добавить все закомеченые изменения в репозиторий *origin* ветку *master* [ -u ]  
**`git push -u origin --all`** &ndash; pushes up the repo and its refs for the first time  
**`git push -u origin --tags`** &ndash; pushes up any tags  

**`git fetch`** &ndash; Получить последние изменения из репозитория (не сливаются)  
**`git pull`** &ndash; Получить последние изменения из репозитория и объединить

* * *
&copy; <v.o.krasovsky@gmail.com>, 2015 