# Ревью лист

## Порядок
## Кодстиль
## Файлы и паки
## Архитектура
## Зависимости

Зависимости должны находиться в компоненте в папка **dependencies** в файле **dependencies.js**

Шаблон выглядит примерно так.

```json
{
    "namespace": "app\\components\\mitrushov\\event_loop",
    "storage": {
      "event_ck": "event_exchange"
    },
    "composer": {
        "php": ">=5.4.0",
        "yiisoft/yii2": "~2.0.5",
        "yiisoft/yii2-gii": "~2.0.0",
        "raveren/kint": "^1.0",
        "nesbot/carbon": "^1.21",
        "phpunit/phpunit": "^5.7.21"
    },
    "classes": {
      "CoreArrayProcessor": "app\\components\\common\\core_array_processor\\CoreArrayProcessor",
      "HandleErrors": "app\\components\\common\\entities\\HandleErrors",
      "ReturnStatement": "app\\components\\common\\statement\\ReturnStatement",
      "EventList": "app\\components\\mitrushov\\event_loop\\interfaces\\EventList",
      "SharedConfig": "app\\components\\mitrushov\\shared_config\\SharedConfig",
      "EventExchange": "app\\models\\EventExchange",
      "Exception": "\\Exception",
      "Yii": "\\Yii",
      "Carbon": "Carbon\\Carbon"
    }
}
```
## Тесты