# Начало работы с Yii

## Настройки приложения

### Содержание:
1. [Настройка путей](#user-content-1-Настройка-путей)
2. [Другие настройки](#user-content-2-Другие-настройки)
3. [Ссылки](#user-content-Ссылки)

##### 1. Настройка путей

После смены структуры приложения, необходимо, указать эти изменения в настройках Yii.  
Для этого открываем файл настроек: *project_name/protected/config/main.php*.

Необходимо прописать новый путь для папок: *protected* - `'basePath'` и *runtime* - `'runtimePath'`.

Ищем свойство: `'basePath'`. Его значение, по умолчанию:

```php
'basePath'=>dirname(__FILE__).DIRECTORY_SEPARATOR.'..';
```

В начале файла, над массивом настроек, нужно добавить следующий код:

```php
function _joinpath($dir1, $dir2) {
	return realpath($dir1 . '/' . $dir2);
}

$homePath      = dirname(__FILE__) . '\..\..';
$protectedPath = _joinpath($homePath, 'protected');
$webrootPath   = _joinpath($homePath, 'wwww');
$runtimePath   = _joinpath($homePath, 'runtime');
```

Заменяем значение свойства `'basePath'` на:
```php
'basePath' => $protectedPath,
```

Ниже добавим свойство `'runtimePath'`, с значением:
```php
'runtimePath' => $runtimePath,
```
##### 2. Другие настройки

* В следующем свойстве `'name'` - задается имя приложения.  
Получить его, можно вызвав: `Yii::app()->name;`

* Необходимо также, в свойстве `'modules'` раскомментировать `'gii'` - для использования генератора кода.

* В свойстве `'components'` разкоментривовать `'urlManager'` - для использования ЧПУ. Добавим в него свойство `'showScriptName'=>false,` - для того, что бы убрать название выполняемого скрипта из URL.

* Для использования баз данных *mysql* нужно раскомментировать соответствующее свойство `'db'` для настроек *mysql* и закоментировать `'db'` для *sqlite*.  
Также для настроек *mysql*, добавим несколько свойств: это *настройки кодировки и параметры логирования*  
```php
'charset' => 'utf8',
'enableParamLogging' => true,
'enableProfiling' => true,
```

* Свойство `'params'` содержит массив с заданными  различными параметрами для приложения. Получить которые можно, вызвав: `Yii::app()->param['parametr_name']`.

### Ссылки

1. [Beginning Yii [Video] - Chris Backhouse](https://www.packtpub.com/web-development/beginning-yii-video)

* * *
&copy; <v.o.krasovsky@gmail.com>, 2016