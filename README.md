# Bitrix snippets 2023

Сниппеты Bitrix для VS Code Editor

Расширение устанавливается глобально и не требует установки в рабочую область.

![Использование](images/sample.gif)
*в примере использована тема [Green Paper](https://marketplace.visualstudio.com/items?itemName=Suntechnic.green-papper)*

## Использование

Просто начните набирать что-нибудь типа CIBlock и нажмите Enter.
Шорткаты сниппетов совместимы с [Bitrix Snippet by Sumanai](https://marketplace.visualstudio.com/items?itemName=sumanai.bitrix-snippet)
Используйте префикс d7 для сниппетов [D7 API](https://dev.1c-bitrix.ru/api_d7/).
Используйте префикс bx для общих сниппетов, таких как подключение пролога.

Расширенные версии сниппетов теперь помечены "+" в имени. Если видите два вариант сниппета, например "d7Sale.BasketItem" и "d7Sale.BasketItem+", то имейте ввиду, что первый - короткая форма, предоставляющая именно то, что описано, а второй - расширенная, с некоторой дополнительной информацией. Так, в данном случае, первый сниппет вернет:
```php
$items = $basket->getBasketItems();
```
а второй:
```php
//https://mrcappuccino.ru/blog/post/work-with-basket-bitrix-d7
$items = $basket->getBasketItems();

foreach ($basket as item) { // сама корзина так же является итерируемым объектом
    echo $item->getField('NAME').': '.$item->getQuantity().'<br />';
    
    $item->getId();         // ID записи в корзине
    $item->getProductId();  // ID товара
    $item->getPrice();      // Цена за единицу
    $item->getQuantity();   // Количество
    $item->getFinalPrice(); // Сумма
    $item->getWeight();     // Вес
    $item->getField('NAME');// Любое поле товара в корзине
    $item->canBuy();        // true, если доступно для покупки
    $item->isDelay();       // true, если отложено
    
    $item->getPropertyCollection(); // Свойства товара в корзине
    
    //$item->setField('QUANTITY', quantity); // Изменение количества
    //$item->save(); // после изменения товар нужно сохранить
    
    //$item->delete(); // Удаление
    //$basket->save();
}
```
Таким образом, к приплюснутым сниппетам можно обращаться как к справочной информации.

## Форматирование кода

Форматирование кода внутри сниппетов опирается на следующие [соглашение](GUIDE.md)

## Сборка пакета из исходника

```sh
vsce package; # сборка
vsce publish; # публикация
```

## Благодарности

Спасибо **Sumanai** за расширение ["Bitrix Snippet"](https://marketplace.visualstudio.com/items?itemName=sumanai.bitrix-snippet), которое стало основой для данного.

Спасибо **ИП Эстрин** за ["Все сниппеты Битрикс d7"](https://estrin.pw/bitrix-d7-snippets/), **MR.CAPPUCCINO** за ["БИТРИКС D7"](https://mrcappuccino.ru/blog/category/bitrix-d7), **Веронике Малышевой** за ["Блог битрикс-программиста"](https://nikaverro.ru/blog/bitrix/) и компании **Интерволга** за [D7-аналоги любимых функций в 1С-Битрикс](https://www.intervolga.ru/blog/projects/d7-analogi-lyubimykh-funktsiy-v-1s-bitriks/), которые стали источником многих сниппетов и справочной информации по новом ядру Doctrine aka D7 Bitrix.
