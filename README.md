# Задача Магазин

## Описание
Это финальная задача! В этом задании попрактикуемся с правилами чистого кода и принципами SOLID.

Нужно написать программу-магазин, в которой пользователи заказывают товары. Вам предоставляется свобода в продумывании функциональности вашей программы, как и в проектировании её структуры. В процессе реализации вы должны применить принцип избегания магических чисел, DRY и как минимум 4 из 5 принципов SOLID, причём явно комментариями в коде или при отправке решения указать по одному примеру применения каждого принципа в вашем решении со ссылками на конкретные места кода на гитхабе.

Примеры возможностей программы:
* Вывод доступных для покупки товаров
* Фильтрация товаров по ключевым словам, ценам, производителям
* Составление продуктовой корзины пользователя
* Трекинг заказа в системе доставки
* Возврат заказа, повтороение заказа
* Система рейтинга для товаров
* Простая рекомендательная система для покупок

## Реализация
1. Продумайте и зафиксируйте список возможностей вашей программы.
2. Продумайте консольный интерфейс взаимодействия пользователя с вашей программой.
3. Продумайте систему классов, которые вам понадобятся для реализации вашей программы.
4. Напишите вашу программу, явно применив вышеперечисленные принципы хорошего кода.
5. При отправке решения укажите, в чём именно было применение каждого этого принципа (по одному примеру) со ссылками на конкретные места кода на гитхабе.
6. Протестируйте работу программы. Не забывайте про правила форматирования кода (для автоформата можете выделить код в идее и нажать **Ctrl+Alt+L**).

## Магические числа (Magics).
В программе отсутствуют магические числа, используются класс ProductType типа enum. 
https://github.com/InfernalBeard/Java-Desing-Patterns_Magics_DRY_SOLID/blob/126b5cf75dd9d0110ebf1b79f40fa5d6af415b26/src/com/company/products/ProductType.java#L3C2-L3C23

## Повторения (DRY).
Все повторяющиеся блоки кода вынесены в отдельные методы. (Строки в классе Main: 26, 47, 76, 172)
https://github.com/InfernalBeard/Java-Desing-Patterns_Magics_DRY_SOLID/blob/126b5cf75dd9d0110ebf1b79f40fa5d6af415b26/src/com/company/Main.java#L26-L47
https://github.com/InfernalBeard/Java-Desing-Patterns_Magics_DRY_SOLID/blob/b1494335613bbd9dedaec29912aaf0c0707a6d21/src/com/company/Main.java#L50-L76
https://github.com/InfernalBeard/Java-Desing-Patterns_Magics_DRY_SOLID/blob/b1494335613bbd9dedaec29912aaf0c0707a6d21/src/com/company/Main.java#L79-L117
https://github.com/InfernalBeard/Java-Desing-Patterns_Magics_DRY_SOLID/blob/b1494335613bbd9dedaec29912aaf0c0707a6d21/src/com/company/Main.java#L122C1-L141
https://github.com/InfernalBeard/Java-Desing-Patterns_Magics_DRY_SOLID/blob/b1494335613bbd9dedaec29912aaf0c0707a6d21/src/com/company/Main.java#L144-L162
https://github.com/InfernalBeard/Java-Desing-Patterns_Magics_DRY_SOLID/blob/b1494335613bbd9dedaec29912aaf0c0707a6d21/src/com/company/Main.java#L164-L172


## SOLID.

**1. Принцип единой ответственности (SRP).**

В программе реализован класс ShoppingCart. В нем реализован функционал работы с продуктовой корзиной. Все вервисы класса направлены на обеспечение этого функционала.
https://github.com/InfernalBeard/Java-Desing-Patterns_Magics_DRY_SOLID/blob/b1494335613bbd9dedaec29912aaf0c0707a6d21/src/com/company/shoppingcart/ShoppingCart.java#L8-L34

В программе реализован класс ShopWindow. В нем реализован функционал работы с витриной магазина. Все вервисы класса направлены на обеспечение этого функционала.
https://github.com/InfernalBeard/Java-Desing-Patterns_Magics_DRY_SOLID/blob/b1494335613bbd9dedaec29912aaf0c0707a6d21/src/com/company/shopwindow/ShopWindow.java#L12-L63

При изменении данных класов не будет влияния на другие объеты.

**2. Принцип открытости/закрытости (OCP).**

Класс Product расширяют классы Fridge и Dishwasher, при этом сам класс не изменяется.
https://github.com/InfernalBeard/Java-Desing-Patterns_Magics_DRY_SOLID/blob/b1494335613bbd9dedaec29912aaf0c0707a6d21/src/com/company/products/Dishwasher.java#L7-L10
https://github.com/InfernalBeard/Java-Desing-Patterns_Magics_DRY_SOLID/blob/b1494335613bbd9dedaec29912aaf0c0707a6d21/src/com/company/products/Fridge.java#L7-L10

**3. Принцип подстановки Барбары Лисков (LSP).**

Классы Fridge и Dishwasher переопределяют метод toString() класса Product с соответствии со своими потребностями, при этом не нарушая поведения переопределенного метода.
https://github.com/InfernalBeard/Java-Desing-Patterns_Magics_DRY_SOLID/blob/b1494335613bbd9dedaec29912aaf0c0707a6d21/src/com/company/products/Dishwasher.java#L22-L29
https://github.com/InfernalBeard/Java-Desing-Patterns_Magics_DRY_SOLID/blob/b1494335613bbd9dedaec29912aaf0c0707a6d21/src/com/company/products/Fridge.java#L22-L29

**4. Принцип разделения интерфейса (ISP).**

У нас есть 2 интерфейса ListPrinter и Sorting. Класс ShopWindow расширяет оба интерфеса, в то время как классу ShoppingCart необходим функционал только одного интерфейса ListPrinter.
https://github.com/InfernalBeard/Java-Desing-Patterns_Magics_DRY_SOLID/blob/b1494335613bbd9dedaec29912aaf0c0707a6d21/src/com/company/products/Fridge.java#L22-L29
https://github.com/InfernalBeard/Java-Desing-Patterns_Magics_DRY_SOLID/blob/bdb7f63a88bf2229c04956467d9858a29bd3beb2/src/com/company/shopwindow/ShopWindow.java#L42-L45
https://github.com/InfernalBeard/Java-Desing-Patterns_Magics_DRY_SOLID/blob/bdb7f63a88bf2229c04956467d9858a29bd3beb2/src/com/company/shopwindow/ShopWindow.java#L48-L51

**5. Принцип инверсии зависимостей (DIP).**

В классe Main создаются объекты типа Product (223 - 243 строки). Класс Main не знает о классах Fridge и Dishwasher, он взаимодействует с ними с помощью абстрактного класса Product.
