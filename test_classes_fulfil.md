# Шаблон оформления тетса

## Архитектура

Тесты в PHP должны оформляться в едином стиле.

И находиться в своём компоненте в папке **tests**.

```php
    components\common\api\models\CallResultGeneralApi.php
    components\common\api\tests\CallResultGeneralApiTest.php
    components\common\api\models\FormReceiverGeneralApi.php
    components\common\api\tests\FormReceiverGeneralApiTest.php
```
---

Тесты имеют неймспейс своего компонента. И обычно используют вспомогательный трейт **TestUsing**.

```php
    namespace app\components\common\api;
    
    use app\components\common\entities\TestUsing;
```
---

Все тесты подключают в себя файл entrance.php. Он всегда находится по адресу **modules/mvc/entrance.php**. 
Путь следует рассчитывать до каждого файла с тестом самостояетльно.

```php
    require_once(__DIR__ . '/../../../modules/mvc/entrance.php');
```
---

Каждый тест содержит четыре необходимых элемента:
* **$fixture** - некоторая структура данных, которая передаётся от теста к тесту
* **dataProvider** - функция, которая возвращает наборы тестовых данных
* **setUp** - функция, которая выполняется перед каждым тестом
* **testFirst** - хотя бы одна функция с тестом

## Общие советы

Функция assert и её производные должны проверять елемент, ради которого запускался тест. assertTrue - это не проверка.

Тест должен охватывать максимальное количество ветвлений внутри тестируемого компонента.

Жизненный цикл теста:
* подготовка тестовых данных
* запуск тестируемого компонента
* проверка результатов на выходе

Тест должен "тестировать" конкретные методы классов, а не абстрактные действия над данными.

## Пример класса

```php
    <?php
    
    namespace app\components\common\api;
    
    require_once(__DIR__ . '/../../../modules/mvc/entrance.php');
    
    use app\components\common\entities\TestUsing;
    
    class DeleteReportsTest extends \PHPUnit_Framework_TestCase
    {
        use TestUsing;
    
        protected $fixture;
    
        public function dataProvider()
        {
            return [
                ['arguments', 'success', 'fail'],
            ];
        }
    
        public function setUp()
        {
            // do something
        }
    
        /**
         * @dataProvider dataProvider
         */
        public function testFirst($mArguments, $mSuccess, $mFail)
        {
            // this is first test
        }
    }
```

## Пример шаблона для PhpStorm

```text
<?php
#parse("PHP File Header.php")

#if (${NAMESPACE})
namespace ${NAMESPACE};
#end

require_once(__DIR__ . '/../../../modules/mvc/entrance.php');

use app\components\common\entities\TestUsing;
#if (${TESTED_NAME} && ${NAMESPACE} && !${TESTED_NAMESPACE})
use ${TESTED_NAME};
#elseif (${TESTED_NAME} && ${TESTED_NAMESPACE} && ${NAMESPACE} != ${TESTED_NAMESPACE})
use ${TESTED_NAMESPACE}\\${TESTED_NAME};
#end

class ${NAME} extends#if(${NAMESPACE}) \PHPUnit_Framework_TestCase #else PHPUnit_Framework_TestCase #end
{
    use TestUsing;

    protected $fixture;
    
    public function dataProvider()
    {
        return [
            ['arguments', 'success', 'fail']
        ];
    }
    
    public function setUp()
    {
        // do something
    }
    
     /**
     * @dataProvider dataProvider
     */
    public function testFirst($mArguments, $mSuccess, $mFail)
    {
        // this is first test
    }
}
```