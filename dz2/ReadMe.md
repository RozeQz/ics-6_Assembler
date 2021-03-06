# Домашнее задание по теме: "Лексические и синтаксические анализаторы"

## Цель работы
Закрепление знаний теоретических основ и основных методов приемов разработки лексических и синтаксических анализаторов регулярных и контекстно-свободных формальных языков.

## Задание
Разработать грамматику и распознаватель имени процедуры с параметрами процедурного типа для языка программирования [C++][1]. Считать, что параметры функций-параметров только стандартных (скалярных) типов.

### Пример входных данных
```cpp
void f1(int (*a)(int a, float b), float (*fff)(long k));
```

## Ход работы

### Форма Бэкуса — Наура

```bash
<Процедура> ::= void <Идентификатор>(<Параметры процедуры>);
<Идентификатор> ::= <Символ>|<Идентификатор><Цифра>|<Идентификатор><Символ>
<Параметры процедуры> ::= <Тип> (*<Идентификатор>)(<Параметры функции>)|<Параметры процедуры>, <Тип> (*<Идентификатор>)(<Параметры функции>)|e
<Параметры функции> ::= <Тип> <Идентификатор>|<Параметры функции>, <Тип> <Идентификатор>|e
<Цифра> ::= 0|1|2|3|4|5|6|7|8|9
<Символ> ::= a|…|z|A|…|Z|_
<Тип> ::= char|int|float|double|bool|short|long
```

### Грамматика
Грамматика относится к *третьему типу* [по Хомскому][2], поскольку самое сложное рекурсивное правило содержит левостороннюю рекурсию.
Так как есть левосторонняя рекурсия, то мы не можем использовать нисходящий грамматический разбор.
Правосторонней рекурсии нет, значит левосторонний восходящий грамматический разбор нам подходит.

[1]: <https://ru.wikipedia.org/wiki/C%2B%2B> "C++ (язык программирования)"
[2]: <https://ru.wikipedia.org/wiki/Иерархия_Хомского> "Классификация грамматик"
