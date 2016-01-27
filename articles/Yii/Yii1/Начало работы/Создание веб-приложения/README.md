# Начало работы с Yii

## Создание веб-приложения в Yii

#### 1. Загрузка/Установка Yii

* Переходим на сайт фреймворка - [yiiframework.com](http://www.yiiframework.com), загружаем архив с Yii.

* Далее разпаковываем архив, переносим содержимое папки *framework* в папку *Yii*.  
В корень веб-сервера: *localhost/Yii* или *remoteserver/Yii*.

#### 2. Новое приложение (сайт)
Теперь нужно развернуть проект для будущего приложения.  

Для этого, воспользуемся следующей коммандой:  
`command line> yiic webapp путь\к\приложению`

Итак, открываем консоль и переходим в папку, в которую распаковывали Yii:  
`cd \путь\к\папке\Yii`. 

Далее, запускаем команду:  
`yiic webapp ..\project_name`

*project_name* - имя папки нового приложения.  

Вводим *yes* и нажимаем *Enter*.

#### 3. Структура приложения

После выполненых комманд, появиться папка с именем *project_name*.  
В нутри папки находяться 5 папок и 2 файла:

[![Yii Basic Structure](http://dl1.joxi.net/drive/0006/3881/438057/160127/f914db8bd0.jpg)](http://joxi.ru/l2Ze3Xqi8VYLEm)

Папки *css, images, themes* должны быть видимыми для браузера  
и находиться в *DOCUMENT ROOT* папке приложения.

[![Yii Basic Structure](http://dl1.joxi.net/drive/0006/3881/438057/160127/db7a2a469f.jpg)](http://joxi.ru/DmBx7lYuN6pj6A)

Папка *protected* содержит файлы приложения Yii, она не должна  
находиться в *DOCUMENT ROOT* и не должна быть видна.

[![Yii Basic Structure](http://dl1.joxi.net/drive/0006/3881/438057/160127/1428710156.jpg)](http://joxi.ru/D2P86KnfdWElX2)

В папке проекта создадим 2 новые папки: *www, runtime*.  
Переносим папки/файлы в папку - *www*: 
* assets, 
* css, 
* images, 
* themes, 
* index.php, 
* index-test.php

Итоговая структура папок проекта:

[![Yii Advanced Structure](http://dl1.joxi.net/drive/0006/3881/438057/160127/f72a23dae7.jpg)](http://joxi.ru/VrwMpVxTKg0dM2)

#### 4. Базовая конфигурация

Следующее, что необходимо сделать, это изменить путь в соответствии с новой структурой приложения.

Для этого открываем файл: *project_name/www/index.php*

и изменяем пути в строчках:
```php
$yii=dirname(__FILE__).'/../Yii/yii.php';
$config=dirname(__FILE__).'/protected/config/main.php';
```

на следующие:
```php
$yii=dirname(__FILE__).'/../../Yii/yii.php';
$config=dirname(__FILE__).'/../protected/config/main.php';
```

### Ссылки

1. [Beginning Yii [Video] - Chris Backhouse](https://www.packtpub.com/web-development/beginning-yii-video)
2. [Yii: Выводим модальное окно (быстрая форма обратной связи) на CJuiDialog](http://loco.ru/materials/321-yii-cjuidialog-dlya-sozdaniya-modalnyh-okon)

* * *
&copy; <v.o.krasovsky@gmail.com>, 2015