# Оформление комментариев и именование

## Функции

Имена функций должны:
* начинаться с глагола
* иметь валидную формулировку
* иметь орфографически правильное написание

```php
    public function setParams($aBody)
    public function setUserErrorHandler()
    public function isDataSet($aBody)
```

В комментарии функций входит:
* описание параметров, их тип и значение
* описание возврата из функции

```php
    /**
     * @param string $aKey - строковый ключ в целевом массиве
     * @param array $aSet - массив значений для поиска
     * @return null
     */
    public function hasKeyNotEmpty($aKey, $aSet)
    {
        return key_exists($aKey, $aSet) && $aSet[$aKey] ? $aSet[$aKey] : null;
    }
```

Если функция пораждает исключение к ней может добавляться параметр **@throws**

```php
    /**
     * @throws Exception
     * @return null
     */
    protected function checkWorkTime()
    {
        throw new Exception('new error');
    }
```


Если функция считается устаревшей и её использование невозможно то должен добавиться **@deprecated**.

Также если функция устарела можно больше не указывать остальные комментарии для неё.

Однострочные комментарии могут использовать короткую запись.

Каждая функция должна иметь модификатор доступа:
* private
* protected
* public

```php
    /** @deprecated */
    private function getTelegramUrlPath($sTelegramUserId)
    {
        return 1;
    }
```

Название функции записывается двумя словами в camelCase, реже тремя иил четырьмя.

Обычно первое слово в названии функции определяет возвращаемое значение.

* **is** или **has** - предполагают, что функция будет возвращать булев тип
* **search** - предполагают, что функция будет возвращать *целое число*, индекс элемента
* **fetch** - получает значение, или null в случае неудачи
* **get** - получает некоторую порцию данных, может быть из поля класса или обращение к базе, или из переменой
* **replace** - возвращает *строку*, с изменениями
* **set** - устанавливает некоторое свойство класса
* **to** - приводит результат к искомому типу
* **map** - возвращает *массив*, после каких-либо изменений

```php
    public function isArray($mValue) {}
    public function toUtf8($mValue) {}
    protected function mapInternal($aFixture, $aParams)
```

## Переменные

Переменные по своему префиксу разделяются на типы:
* **b** - булев тип
* **i** - целое число
* **f** - число с плавающей точкой
* **r** - ресурс
* **o** - объект
* **s** - строка
* **m** - псевдо тип mixed

```php
    $sAnyText = strval($sAnyText);
    $iNumber = 1;
    $bThirdElement = false;
```

Названия переменных начинаются с существительного и содержат информацию о данных, которые эти переменные хранят.

Поля классов подчиняются тем же правилам в названиях, что и локальные переменные, как и параметры, передаваемые в функции.

```php
   $rDepth = fopen('w', 'https://foo');
   $this->rDepth = fopen('w', 'https://foo');
   public function isSip($sSip, $isStrict = true, $mContext) {}
```

Переменные обычно не перезаписывают семантически другими данными, тем более другим типом.

Когда нужно записать новые данные, создают новую переменную, даже если старая больше не используется.

```php
    $sStageOne = 'stage';
    $iStageTwo = 2;
    $sReplacedStage = str_replace('stage', 'replaced', $sStageOne);
```

Переменные обычно состоят из одного или более слов с префиксом типа данных.

Для итераторов циклов допустимы названия в одну букву.

```php
    $oPdoLive = new PDO();
    foreach ($aHaystack as $k => $v)
    for ($i = 0; $i < 10; $i++))
```

Для полей классов предусмотрены однострочные комментарии.

```php
    /** @var DataQueryReflect $fixture */
    protected $fixture;
    
    /** @var string $sReplaceMarker */
    public $sReplaceMarker = '.';
```

Для дополнительной ясности переменные, которые являются экземплярами классов возвращаемых 
из других функций, подписываются строчными комментариями

```php
    /** @var FooObject $oFooObject  */
    $oFooObject = someFunctionReturnedFooObjectTeoreticaly();
```