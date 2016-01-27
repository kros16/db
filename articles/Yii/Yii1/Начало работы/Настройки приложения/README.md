# ������ ������ � Yii

## ��������� ����������

### ����������:
1. [��������� �����](#user-content-1-���������-�����)
2. [������ ���������](#user-content-2-������-���������)
3. [������](#user-content-������)

##### 1. ��������� �����

����� ����� ��������� ����������, ����������, ������� ��� ��������� � ���������� Yii.  
��� ����� ��������� ���� ��������: *project_name/protected/config/main.php*.

���������� ��������� ����� ���� ��� �����: *protected* - `'basePath'` � *runtime* - `'runtimePath'`.

���� ��������: `'basePath'`. ��� ��������, �� ���������:

```php
'basePath'=>dirname(__FILE__).DIRECTORY_SEPARATOR.'..';
```

� ������ �����, ��� �������� ��������, ����� �������� ��������� ���:

```php
function _joinpath($dir1, $dir2) {
	return realpath($dir1 . '/' . $dir2);
}

$homePath      = dirname(__FILE__) . '\..\..';
$protectedPath = _joinpath($homePath, 'protected');
$webrootPath   = _joinpath($homePath, 'wwww');
$runtimePath   = _joinpath($homePath, 'runtime');
```

�������� �������� �������� `'basePath'` ��:
```php
'basePath' => $protectedPath,
```

���� ������� �������� `'runtimePath'`, � ���������:
```php
'runtimePath' => $runtimePath,
```
##### 2. ������ ���������

* � ��������� �������� `'name'` - �������� ��� ����������.  
�������� ���, ����� ������: `Yii::app()->name;`

* ���������� �����, � �������� `'modules'` ����������������� `'gii'` - ��� ������������� ���������� ����.

* � �������� `'components'` ����������������� `'urlManager'` - ��� ������������� ���. ������� � ���� �������� `'showScriptName'=>false,` - ��� ����, ��� �� ������ �������� ������������ ������� �� URL.

* ��� ������������� ��� ������ *mysql* ����� ����������������� ��������������� �������� `'db'` ��� �������� *mysql* � ��������������� `'db'` ��� *sqlite*.  
����� ��� �������� *mysql*, ������� ��������� �������: ��� *��������� ��������� � ��������� �����������*  
```php
'charset' => 'utf8',
'enableParamLogging' => true,
'enableProfiling' => true,
```

* �������� `'params'` �������� ������ � ���������  ���������� ����������� ��� ����������. �������� ������� �����, ������: `Yii::app()->param['parametr_name']`.

### ������

1. [Beginning Yii [Video] - Chris Backhouse](https://www.packtpub.com/web-development/beginning-yii-video)

* * *
&copy; <v.o.krasovsky@gmail.com>, 2016