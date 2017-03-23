# JunkFood
Задание на отработку практических навыков Test Driven Development (TDD)

В рамках данного задания в познакомитесь с:

- Test-Driven Development
- Модульное тестирование (Unit testing)
- JUnit

# Тесты

В библиотеке [JUnit](http://junit.org/) тесты представляют собой специальные методы, которые

- имеют аннотацию `@Test`
- имя метода начинаются с

Пример:

```java
    /**
     * Демонстрирует базовые возможности библиотеки тестирования JUnit.
     * Можно задавать несколько видов тестов.
     */
    @Test
    public void testExample(){
        //Проверка на истину булевого выражения
        assertTrue("Это все знают! Да или нет?!", 2+2 == 4);
        //Проверка на равенство объектов. Объекты сравниваются методом @see Object.equals
        assertEquals(new Integer(10), new Integer(10));
        //Проверка на неравенство. Да! 10 и "10" не равны. Это вам не JavaScript ;)
        assertNotEquals(10, "10");
        //Проверка на не пустоту
        assertNotNull(new Tests());
        //Проверка на пустоту
        assertNull(null);
        //Order создан, заранее заготовлен в методе prepare. Проверим его на не пустоту. Отрабатывает ли prepare???
        assertNotNull(o);
    }
```

# Assert
Тестирование заключается в проверке соответствия работы программы заявленной спецификации, контракту. 

Assert - это утверждение о том, как себя ведет система. Например, когда мы реализуем операцию сложения, мы заведомо знаем, как она должна складывать.
Например 2+2 = 4 или 3+5 = 8. Тогда тестом будет являться проверка результата суммирования для значения 2 и 2 и сравнение его с 4. Мы утверждаем, что оно должно быть равно 4.

Рассмотрим пример утверждения:
```java
 assertTrue(sum(2,2) == 4);
```
В данном случае мы проверяем, что фактическое возвращаемое значение функции sum с заданными параметрами 2 и 2 совпадает с ожидаемым значением 4.

Дополнительно мы можем указать подпись для данного теста (утверждения). Эта подпись будет выдаваться в системе тестирования для упрощения идентификации проверяемого сценария.
```java
 assertTrue("Суммирование чисел 2 и 2 должно давать 4", sum(2,2) == 4);
```

Нетрудно догадаться, что все виды проверок возможно реализовать через `assertTrue`, но для упрощения код тестов в библиотеке имеется множество других методов.
Например, часто необходимо сравнивать ожидаемое значение с фактическим значением, полученным программой. Для этого имеется метод `assertEquals`

```java
 //ожидаем 4, фактическое значение - результат функции sum(2,2)
 assertEquals(4, sum(2,2));
 //эквивалентный вариант с подписью
 assertEquals("Суммирование чисел 2 и 2 должно давать 4", 4, sum(2,2));
```

> Обратите внимание, что сначала указывается ОЖИДАЕМОЕ значение, а затем ФАКТИЧЕСКОЕ значение. Тест провалится в любом случае, но автоматическая система тестирования будет вам писать: "ожидалось X, получили Y".

# Задачи
Вам необходимо реализовать сначала тесты, затем функциональность по следующим требованиям:

- При создании блюда можно указать его наименование и цену. Но менять в последствии нельзя
- Меню должен возвращать непустой список блюд не менее, чем из 10 элементов.
- Можно добавлять блюда в заказ только из меню
- Можно добавлять несколько экземпляров каждого блюда из меню
- Итоговая сумма учитывает все позиции заказа: цену блюда и количество

Для проверки правильности последовательности работы сначала должны идти коммиты с тестами (на какую-то функциональность, на какой-то метод), а затем коммиты с реализацией того или иного метода.

# Инструкции
> Примечание: данные пошаговые инструкции являются лишь одним из возможных вариантов. Вы вправе либо сразу реализовать все тесты и закоммитить их. Либо делать мелкие коммиты по одному тесту и затем реализовывать требуемую тестом функциональность. Затем реализовывать следующий тест и т.д.

## Тесты

### Блюдо
Для начала выберите, каким способом вы будете задавать наименование и цену блюда при создании. Либо через get-теры, либо через конструктор. 
Создайте соответствующие сигнатуры и напишите тест с их использованием. В тесте можете создать один или несколько блюд с указанием наименования и цены.
Затем проверьте, что фактическая цена и наименования блюда совпадают с ожидаемыми (указанными при создании).

Затем напишите тест, проверяющий, что два блюда с одинаковым названием являются эквивалентными.
При необходимости сделайте commit

### Меню
Напишите тест, проверяющий, что список блюд, возвращаемый меню, не пуст.

Напишите тест, проверяющий, что список блюда, возвращаемый меню, содержит не менее 10 элементов.

Напишите тест, проверяющий, что список блюд меню не содержит одинаковых блюд (блюд с одинаковыми именами)

При необходимости сделайте commit.

### Заказ

Напишите тест, проверяющий, что можно добавить в заказ блюдо из меню.

Напишите тест, проверяющий, что нельзя добавить в заказ блюдо не из меню.

Напишите тест, проверяющий, что можно добавить несколько экземпляров одного блюда. Лучше сделать/переделать метод
```java
    public void addMeal(Meal meal, int count)
```

Напишите тест, проверяющий правильность расчетов итоговой суммы для заказа.

Сделайте commit.

## Реализация

Реализуйте функциональность приложения (классы Meal, Order, Menu) так, чтобы все тесты проходили. 

Сделайте commit.

# Отчет

В качестве отчета 

- выполните pull-request.
- отправьте ссылку на репозиторий



