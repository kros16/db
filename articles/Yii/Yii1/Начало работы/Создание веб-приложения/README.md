# ������ ������ � Yii

## �������� ���-���������� � Yii

#### 1. ��������/��������� Yii

* ��������� �� ���� ���������� - [yiiframework.com](http://www.yiiframework.com), ��������� ����� � Yii.

* ����� ������������� �����, ��������� ���������� ����� *framework* � ����� *Yii*.  
� ������ ���-�������: *localhost/Yii* ��� *remoteserver/Yii*.

#### 2. ����� ���������� (����)
������ ����� ���������� ������ ��� �������� ����������.  

��� �����, ������������� ��������� ���������:  
`command line> yiic webapp ����\�\����������`

����, ��������� ������� � ��������� � �����, � ������� ������������� Yii:  
`cd \����\�\�����\Yii`. 

�����, ��������� �������:  
`yiic webapp ..\project_name`

*project_name* - ��� ����� ������ ����������.  

������ *yes* � �������� *Enter*.

#### 3. ��������� ����������

����� ���������� �������, ��������� ����� � ������ *project_name*.  
� ����� ����� ���������� 5 ����� � 2 �����:

[![Yii Basic Structure](http://dl1.joxi.net/drive/0006/3881/438057/160127/f914db8bd0.jpg)](http://joxi.ru/l2Ze3Xqi8VYLEm)

����� *css, images, themes* ������ ���� �������� ��� ��������  
� ���������� � *DOCUMENT ROOT* ����� ����������.

[![Yii Basic Structure](http://dl1.joxi.net/drive/0006/3881/438057/160127/db7a2a469f.jpg)](http://joxi.ru/DmBx7lYuN6pj6A)

����� *protected* �������� ����� ���������� Yii, ��� �� ������  
���������� � *DOCUMENT ROOT* � �� ������ ���� �����.

[![Yii Basic Structure](http://dl1.joxi.net/drive/0006/3881/438057/160127/1428710156.jpg)](http://joxi.ru/D2P86KnfdWElX2)

� ����� ������� �������� 2 ����� �����: *www, runtime*.  
��������� �����/����� � ����� - *www*: 
* assets, 
* css, 
* images, 
* themes, 
* index.php, 
* index-test.php

�������� ��������� ����� �������:

[![Yii Advanced Structure](http://dl1.joxi.net/drive/0006/3881/438057/160127/f72a23dae7.jpg)](http://joxi.ru/VrwMpVxTKg0dM2)

#### 4. ������� ������������

���������, ��� ���������� �������, ��� �������� ���� � ������������ � ����� ���������� ����������.

��� ����� ��������� ����: *project_name/www/index.php*

� �������� ���� � ��������:
```php
$yii=dirname(__FILE__).'/../Yii/yii.php';
$config=dirname(__FILE__).'/protected/config/main.php';
```

�� ���������:
```php
$yii=dirname(__FILE__).'/../../Yii/yii.php';
$config=dirname(__FILE__).'/../protected/config/main.php';
```

### ������

1. [Beginning Yii [Video] - Chris Backhouse](https://www.packtpub.com/web-development/beginning-yii-video)
2. [Yii: ������� ��������� ���� (������� ����� �������� �����) �� CJuiDialog](http://loco.ru/materials/321-yii-cjuidialog-dlya-sozdaniya-modalnyh-okon)

* * *
&copy; <v.o.krasovsky@gmail.com>, 2015