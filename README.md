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