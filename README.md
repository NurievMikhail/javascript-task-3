# Задача «0b11 друзей Оушена»

Перед выполнением задания внимательно прочитайте:

- [О всех этапах проверки задания](https://github.com/urfu-2016/guides/blob/master/workflow/overall.md)
- [Как отправить пулл](https://github.com/urfu-2016/guides/blob/master/workflow/pull.md)
- [Как пройти тесты](https://github.com/urfu-2016/guides/blob/master/workflow/test.md)
- Правила оформления [javascript](https://github.com/urfu-2016/guides/blob/master/codestyle/js.md), [HTML](https://github.com/urfu-2016/guides/blob/master/codestyle/html.md) и [CSS](https://github.com/urfu-2016/guides/blob/master/codestyle/css.md) кода
- Лекцию [«Типы данных: продолжение»](https://urfu-2016.github.io/javascript-slides/03-types/#/)

## Основное задание

> Мы очень хотим, чтобы код вы написали сами, а не пользовались внешними библиотеками.

Три компаньона – «Danny», «Rusty» и «Linus» – частенько проворачивают тёмные делишки под покровом ночи: пишут на PHP, едят после шести и изредка грабят банки.

Сегодня они подумали, что настало время завязать с тёмными делами. Поэтому решили пойти на последнее ограбление, а после изучить javascript и стать законопослушными фронтедерами.

Сейчас уже понедельник, а в четверг в банк поставят новую сигнализацию. И у них есть только три дня (понедельник, вторник и среда), чтобы выбрать подходящее время. Во-первых, это должно быть в рабочие часы банка – так легче проникнуть в него. Во-вторых, все трое должны быть свободны. И в-третьих, должно быть достаточно времени, чтобы провернуть дело.

Компаньоны быстро составили расписание – когда и кто занят  
(заметьте, что грабители находятся в разных часовых поясах):

```js
{
    Danny: [
        { from: 'ПН 12:00+5', to: 'ПН 17:00+5' },
        { from: 'ВТ 13:00+5', to: 'ВТ 16:00+5' }
    ],
    Rusty: [
        { from: 'ПН 11:30+5', to: 'ПН 16:30+5' },
        { from: 'ВТ 13:00+5', to: 'ВТ 16:00+5' }
    ],
    Linus: [
        { from: 'ПН 09:00+3', to: 'ПН 14:00+3' },
        { from: 'ПН 21:00+3', to: 'ВТ 09:30+3' },
        { from: 'СР 09:30+3', to: 'СР 15:00+3' }
    ]
}
```

![example](https://cloud.githubusercontent.com/assets/4534405/19563495/a0ec90be-96f9-11e6-978e-826bcae3628b.png)

И нашли в интернете часы работы банка:

```js
{ from: '10:00+5', to: '18:00+5' }
```

Но выбрать время для ограбления сходу не получилось, поэтому предлагаем вам написать скриптик с методом (getAppropriateMoment), который на вход принимает расписание (schedule), необходимое для ограбления время (time) в минутах и время работы банка (workingHours), вычисляет подходящее время и на выходе предоставляет объект для работы с ним:

* `.exists()` – отвечает на вопрос найдено ли время вообще
* `.format(template)` – выводит время ограбления в часовом поясе банка и согласно переданному шаблону, который может включать в себя часы **HH**, минуты **MM** и день недели **DD**. Например, _«Начинаем в %HH:%MM (%DD)»_. Если время не найдено, метод возвращает пустую строку.

__Дополнительные условия и ограничения:__

* Все время задачи ограничено неделей c ПН 00:00 до ВС 23:59 в часовом поясе банка
* Время ограбления должно попадать в промежуток c ПН 00:00 до СР 23:59 в часовом поясе банка
* Банк работает всю неделю
    * Но работает в рамках только одного дня (не может открыться в один день, а закрыться в другой)
    * И может открыться в 00:00, а закрыться аж в 23:59
* Временная зона задана в часах. Всегда целое число, может быть только положительным – «+5»
* Даты приходят всегда правильно, можно опустить обработку неправильных дат и интервалов
* Гарантируется одинаковость часового пояса в одном контексте: в рамках расписания одного члена банды, в рамках часов работы банка

В файле _index.js_ и в тестах вы можете найти примеры использования получившегося скриптика.

## Дополнительное задание (+16 к смекалке)

> Перед выполнением внимательно прочитайте [про особенности](https://github.com/urfu-2016/guides/blob/master/workflow/extra.md)

Реализовать метод `.tryLater()`, который находит следующее подходящее время **через полчаса** от предыдущего. Если найти не получается, то время остается прежнее. Метод возращает true, если получилось найти и false, если нет.

Пример работы этого метода вы может отыскать в _index.js_ и в тестах.
Будет по-настоящему здорово, если вы его осилите!

<img width="1447" alt="11" src="https://cloud.githubusercontent.com/assets/4534405/19563484/95006636-96f9-11e6-9b37-8fd4e9734002.png">

:warning: Грабить банки – нехорошо, не повторяйте этого дома!
