# Yii 1. ������� �����

## ��������� ������������. ������ � ��������� ����

>**������:** ����� ��������� ������������, � ���������� �������� ������ �� ������ � ������� ����� (����������/���������). �������� ��������� � ��������� ����, ����� ������������ ��������.


>**�������:** ��� �������� ���������� �������� ����� ������������ ���������� ������� ���������� `Yii::app()->user->setFlash();`, � ��� ��� ���������, ������� `Yii::app()->user->getFlash();`.  
��� ������, ������������ ���������� � Yii ���� &ndash; **CJuiDialog**.

### ������ �������������:

#### 1. ������

� �������, ������ ������ **/models/Dialog.php** �� ����������� ��������: **Message()** � ���.

```php
<?php
class Dialog {

  /**
   * ������� ��������� � ��������� ����, ����� ������������ ��������
   * 
   * @param string $type ��� (����� CSS � ������� ����� ������� ���� ���������)
   * @param string $title ��������� ���������
   * @param string $message ����� ���������
   * @param integer $id ID ��� setflash()
   */
  public static function Message($type, $title, $message, $id = 0) 
  {
    $id = $id ? $id : rand(1, 999999);

    Yii::app()->user->setflash($id, array('type'    => $type,
                                          'title'   => $title, 
                                          'content' => $message
                                    ) 
                              );
  }

}
```

#### 2. ����������

� ������ ����������� ���������� � ������� **Message()** ������ **Dialog**.  
��������� ������� �� �������� ������, ���� ��, �� �������� ��������� �� ������, ��� ��������� �� ������.

```php
if($model->save()){
  Dialog::message('success', '��������� �������', '������ ���������!');
} else {
  Dialog::message('error', '��������� �������', '�� ������� ��������� ������!');
}
```

#### 3. ���

��� ������ ��������� ������ ���� ���� **views/site/dialog.php**  

� �������, �������� ������ ��������� �� `Yii::app()->user->getFlash();` � � ������� `foreach($flashes as $key => $message)` &ndash; �������� ������ **CJuiDialog**, ��� ������� ����������� ���������.  

**��������� ������ ����������� �������.**  
� �������� `'title'` &ndash; ��������� ��������� ��������� `$message['title']`, � `'open'` &ndash; ������ ��������, ���� ��� ��������� �� ������ ����������, �� �������� JS ������� (������������� ������� ���� �������), ���� ������ ������ &ndash; ��������� ������ ��������. ����� ������ ���������� ��� ������������ �������� ��������� &ndash; `'autoOpen'  => true`.

� ������� ������� `printf()` ������������ ����� ����������� ��������� `$message['content']`, ������� � ���� `<span>`, ������� ��� ����� � ���������, ���������� �� ���� ��������� `$message['type']`.

```php
<?php
if($flashes = Yii::app()->user->getFlashes()) {
  foreach($flashes as $key => $message) {
    if($key != 'counters') {
      $this->beginWidget('zii.widgets.jui.CJuiDialog', array(
        'id'=>$key,
        'options'=>array(
          'show'      => 'blind',
          'hide'      => 'explode',
          'modal'     => 'true',
          'title'     => $message['title'],
          'autoOpen'  => true,
          'resizable' => 'false',
          'open' => $message['type'] !== 'error' ? 'js:function(event, ui){
            setTimeout("$(\'#'.$key.'\').dialog(\'close\')",3000);
            }' : '',
          'hide' => array(
            'effect'   => 'explode',
            'duration' => 500,
          ),
        ),
      ));

      printf('<span class="%s">%s</span>', $message['type'], $message['content']);

      $this->endWidget('zii.widgets.jui.CJuiDialog');
    }
  }
}
```

#### 4. �����

� ����� **layout** (����� ��� **views/layouts/main.php**), ����� `<?php echo $content; ?>` ��������� ��� � ������� ������ **renderPartial()**, ��� ����� ���� **views/site/dialog.php**

### ������

1. [Yii 1.1: Using CJuiDialog to display flash Messages in Dialogues](http://www.yiiframework.com/wiki/79/using-cjuidialog-to-display-flash-messages-in-dialogues/)
2. [Yii: ������� ��������� ���� (������� ����� �������� �����) �� CJuiDialog](http://loco.ru/materials/321-yii-cjuidialog-dlya-sozdaniya-modalnyh-okon)

* * *
&copy; <v.o.krasovsky@gmail.com>, 2015