# Rud

Библиотека предназначена для представления дат в человекочитаемом формате,
привычном русскоязычной аудитории.

## Формат Ymd

Одним из форматов стандарта [`ISO 8601`](https://ru.wikipedia.org/wiki/ISO_8601)
является `YYYYMMDD` или сокращённо `Ymd`. Это восьмиразрядное число в
десятичной системе счисления, старшие четыре разряда которого представляют год,
далее два разряда — месяц, и два младших — день. Преимуществом такого формата
для представления дат является удобство хранения числа в БД, а так же удобство
сравнения (число, выражающее дату `A` всегда будет больше числа, выражающего
дату `B`, если дата `A` позже даты `B`).

## Представление дат в русскоязычных приложениях

Насколько удобен формат `Ymd` для хранения и операций, настолько же он неудобен
для чтения.

## Установка

Установите `rud` при помощи [`npm`](https://www.npmjs.com/):

```bash
npm i rud
```

## Подключение

С применением CommonJS:

```javascript
const { rudDigits, rudString, rudInterval } = require('rud');
```

С применением ES Modules:

```javascript
import { rudDigits, rudString, rudInterval } from 'rud';
```

## Использование

Цифровое представление:

```javascript
// С разделителем по умолчанию (точка)
rudDigits(20200101); // 01.01.2020

// С заданным разделителем
rudDigits(20200101, '/'); // 01/01/2020
```

Строковое представление:

```javascript
// По умолчанию выходная строка содержит год
rudString(20190507); // '7 мая 2019'

// Если требуется, год можно скрыть
rudString(20190507, false); // '7 мая'
```

При построении интервалов дат, функция `rudInterval` по возможности сокращает
представление повторяющихся элементов:

```javascript
rudInterval(20191201, 20200130); // 1 декабря 2019 — 30 января 2020

rudInterval(20200110, 20200220); // 10 января — 20 февраля 2020

rudInterval(20200211, 20200221); // 11 — 21 февраля 2020

rudInterval(20200222, 20200222); // 22 февраля 2020
```
