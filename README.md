# Задание 
1. Выписать набор граничных примеров и контрпримеров, демонстрирующих уточнение языка. Составить КС-грамматику языка.
2. Прописать грамматический разбор одного примера.
3. Проверить, удовлетворяет ли грамматика однозначности ветвления по первому символу. Если не удовлетворяет, то изменить грамматику так, чтобы она удовлетворяла.
4. По грамматике составить синтаксические диаграммы.
5. Написать программу по синтаксическим диаграммам (выбрать можно любый язык программирования). Проверить примеры и контрпримеры из первого пункта. 
### Язык записи шестнадцатеричных чисел, кратных 3.
- Список символов: 0123456789ABCDEF
```python
s = ['0', '1', '2', '3', '4', '5', '6', '7', '8', '9', 'A', 'B', 'C', 'D', 'E', 'F']
```
# Признак делимости на 3 для 16-ричных чисел:
if Сумма цифр в числа mod 3 == 0 => число mod 3 == 0 

# Пункт 1: 
### Выписать набор граничных примеров и контрпримеров, демонстрирующих уточнение языка. Составить КС-грамматику языка.
#### Грамматика:
![Грамматика](/img/Грамматика.png)
Данная грамматика строиться по принципу (число + остаток суммы цифр на 3), где 

|Значение|Остаток|
|--- | --- |
|o|0|
|e|1|
|d|2|

Мы используем **свойство**:
```
(N + M) mod 3 = (N mod 3 + M mod 3) mod 3
```

##### Проведем разбор
|Число в 10-й системе|Число в 16-й системе|Принадлежит системе|Разбор|
|--- | --- | --- | --- |
|0|0|True|o => 0o => 0|
|12|C|True|o => Co => C|
|30|1E|True|o => 1e => 1Eo => 1E|
|34|22|False|o => 2d => 22e|
|56|38|False|o => 3o => 38d|
|23|17|False|o => 1e => 17d|
|99|63|True|o => 6o => 63o => 63|
|19273|4B49|False|o => 4e => 4Bo => 4B4e => 4B49e|
|27483467|1A35D4B|False|o => 1e => 1Ad => 1A3d => 1A35e => 1A35Dd => 1A35D4o => 1A35D4Bd|
|92745628|5872F9C|False|o => 5d => 58e => 587d => 5872e => 5872Fe => 5872F9e => 5872F9Ce|
|929273723|3763977B|False|o => 3o => 37e => 376e => 3763e => 37639e => 376397d => 3763977o => 3763977Bd|
|89762198638|14E63E746E|False|o => 1e => 14d => 14Ee => 14E6e => 14E63e => 14E63Eo => 14E63E7e => 14E63E74d => 14E63E746d => 14E63E746Ee|
|129867387126|1E3CB310F6|True|o => 1e => 1Eo => 1E3o => 1E3Co => 1E3CBd => 1E3CB3d => 1E3CB31o => 1E3CB310o => 1E3CB310Fo => 1E3CB310F6o => 1E3CB310F6|