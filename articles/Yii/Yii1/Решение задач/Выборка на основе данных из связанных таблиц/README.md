# Yii 1. Решение задач

## Выборка на основе данных из связанных таблиц.

>**Задача:** Получить данные из таблицы БД, делая выборку по значениям полей связанной таблицы. Например, для реализации фильтров по полученным данным.


>**Решение:** Добавлено функцию в модель связанной таблицы, которая получает необходимые данные по заданному условию.

### Пример использования:

#### 1. Модель

В связанной модели **/models/modelName.php** в самый конец добавляем статическую функцию: **filterListData()**. Вместо `modelName` &ndash; имя модели, необходимо указать имя самой модели (*содержащая вызываемую функцию*).

```php
/**
* Возвращает массив данных (ID => Name) связанных моделей
* на основе данных в текущей модели. Сортирует полученный массив в
* порядке возрастания значений
* 
* @param string $relationName Имя связи из ф-ции Relations()
* @param string $valueField Имя поля (ID) по которому совершается связь
* с $relationName или имя поля (ID) для подсвязи $relationName
* @param string $textField Имя поля с значением (названием)
* для связанного поля $valueField
* @return array $listData Массив данных для фильтра
*/
public static function filterListData($relationName, $valueField, $textField)
{
  $criteria = new CDbCriteria;

  $criteria->with = array($relationName);
  $criteria->addCondition($valueField . ' IS NOT NULL');

  $model = modelName::model()->findAll($criteria);
  $listData = CHtml::listData($model, $valueField, $relationName .'.'. $textField);
  asort($listData);

  return $listData;
}
```
Также, необходимо проверить наличие необходимых моделей в **`relations()`**, при отсутствии добавить.

**Например:**

```php
public function relations()
{
  return array(
  	'profiles' => array(self::BELONGS_TO, 'Profiles', 'manager_expert_id')
  );
}
```

#### 2. Вывод

Для вывода достаточно вызвать созданную в модели функцию: `modelName::filterListData($relationName, $valueField, $textField)`, передав в нее необходимые параметры.

**Например, в форме (*фильтр*) в виде выпадающего списка:**

```php
<?php echo CHtml::activeDropDownList($dataProvider, 'manager_expert_id',
                  modelName::filterListData('profiles', 'manager_expert_id', 'lastname'),
                  array('empty' => '-- Всi --')
           )
?>
```

* * *
&copy; <v.o.krasovsky@gmail.com>, 2015