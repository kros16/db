# Yii 1. Решение задач

## Сообщение пользователю. Диалог в модальном окне

>**Задача:** Вывод сообщения пользователю, о результате отправки данных на сервер с помощью формы (добавления/изменения). Выводить сообщение в модальном окне, после перезагрузки страницы.


>**Решение:** Для хранения результата отправки формы использовать встроенную функцию Фреймворка `Yii::app()->user->setFlash();`, а для его получения, функцию `Yii::app()->user->getFlash();`.  
Для вывода, использовать встроенный в Yii клас &ndash; **CJuiDialog**.

### Пример использования:

#### 1. Модель

В моделях, создаём модель **/models/Dialog.php** со статической функцией: **Message()** в ней.

```php
<?php
class Dialog {

  /**
   * Выводит сообщение в модальном окне, после перезагрузки страницы
   * 
   * @param string $type Тип (Класс CSS в котором нужно вывести текс сообщения)
   * @param string $title Заголовок сообщения
   * @param string $message Текст сообщения
   * @param integer $id ID для setflash()
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

#### 2. Контроллер

В нужном контроллере обращаемся к функции **Message()** модели **Dialog**.  
Проверяем успешно ли выполнен запрос, если да, то передаем сообщение об успехе, нет сообщение об ошибке.

```php
if($model->save()){
  Dialog::message('success', 'Результат запроса', 'Данные сохранены!');
} else {
  Dialog::message('error', 'Результат запроса', 'Не удалось сохранить данные!');
}
```

#### 3. Вид

Для вывода сообщения создаём файл вида **views/site/dialog.php**  

В котором, получаем данные сообщений из `Yii::app()->user->getFlash();` и с помощью `foreach($flashes as $key => $message)` &ndash; вызываем виджет **CJuiDialog**, для каждого полученного сообщения.  

**Заполняем виджет полученными данными.**  
В атрибуте `'title'` &ndash; указываем заголовок сообщения `$message['title']`, в `'open'` &ndash; делаем проверку, если тип сообщения об успехе выполнения, то вызываем JS функцию (автоматически закрыть окно диалога), если пришла ошибка &ndash; оставляем диалог открытым. Чтобы диалог открывался при перезагрузке страницы указываем &ndash; `'autoOpen'  => true`.

С помощью функции `printf()` обрабатываем текст полученного сообщения `$message['content']`, выводим в теге `<span>`, задавая ему класс с названием, полученным из типа сообщения `$message['type']`.

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

#### 4. Вывод

В файле **layout** (часто это **views/layouts/main.php**), перед `<?php echo $content; ?>` добавляем код с вызовом метода **renderPartial()**, для файла вида **views/site/dialog.php**

### Ссылки

1. [Yii 1.1: Using CJuiDialog to display flash Messages in Dialogues](http://www.yiiframework.com/wiki/79/using-cjuidialog-to-display-flash-messages-in-dialogues/)
2. [Yii: Выводим модальное окно (быстрая форма обратной связи) на CJuiDialog](http://loco.ru/materials/321-yii-cjuidialog-dlya-sozdaniya-modalnyh-okon)

* * *
&copy; <v.o.krasovsky@gmail.com>, 2015