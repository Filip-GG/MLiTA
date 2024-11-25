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

#### Проведем разбор:
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
|79762198638|129232906E|True|o => 1e => 12o => 129o => 1292d => 12923d => 129232e => 1292329e => 12923290e => 129232906e => 129232906Eo => 129232906E|
|129867387126|1E3CB310F6|True|o => 1e => 1Eo => 1E3o => 1E3Co => 1E3CBd => 1E3CB3d => 1E3CB31o => 1E3CB310o => 1E3CB310Fo => 1E3CB310F6o => 1E3CB310F6|

# Пункт 2:
### Прописать грамматический разбор одного примера.
#### Проведем разбор числа 32908371287624190234678
Данное число в 16-й системе имеед вид **6F7F764D212100B9036**
Разбор имеет вид: o => 6o => 6Fo => 6F7e => 6F7Fe => 6F7F7d => 6F7F76d => 6F7F764o => 6F7F764De => 6F7F764D2o => 6F7F764D21e => 6F7F764D212o => 6F7F764D2121e => 6F7F764D21210e => 6F7F764D212100e => 6F7F764D212100Bo => 6F7F764D212100B9o => 6F7F764D212100B90o => 6F7F764D212100B903o => 6F7F764D212100B9036o => 6F7F764D212100B9036



# Таблица грамматики от 0 до 1 000 

|Число в 10-й системе|Число в 16-й системе|Принадлежит системе|Разбор|
|--- | --- | --- | --- |
|0|0|True|o => 0o => 0|
|1|1|False|o => 1e|
|2|2|False|o => 2d|
|3|3|True|o => 3o => 3|
|4|4|False|o => 4e|
|5|5|False|o => 5d|
|6|6|True|o => 6o => 6|
|7|7|False|o => 7e|
|8|8|False|o => 8d|
|9|9|True|o => 9o => 9|
|10|A|False|o => Ae|
|11|B|False|o => Bd|
|12|C|True|o => Co => C|
|13|D|False|o => De|
|14|E|False|o => Ed|
|15|F|True|o => Fo => F|
|16|10|False|o => 1e => 10e|
|17|11|False|o => 1e => 11d|
|18|12|True|o => 1e => 12o => 12|
|19|13|False|o => 1e => 13e|
|20|14|False|o => 1e => 14d|
|21|15|True|o => 1e => 15o => 15|
|22|16|False|o => 1e => 16e|
|23|17|False|o => 1e => 17d|
|24|18|True|o => 1e => 18o => 18|
|25|19|False|o => 1e => 19e|
|26|1A|False|o => 1e => 1Ad|
|27|1B|True|o => 1e => 1Bo => 1B|
|28|1C|False|o => 1e => 1Ce|
|29|1D|False|o => 1e => 1Dd|
|30|1E|True|o => 1e => 1Eo => 1E|
|31|1F|False|o => 1e => 1Fe|
|32|20|False|o => 2d => 20d|
|33|21|True|o => 2d => 21o => 21|
|34|22|False|o => 2d => 22e|
|35|23|False|o => 2d => 23d|
|36|24|True|o => 2d => 24o => 24|
|37|25|False|o => 2d => 25e|
|38|26|False|o => 2d => 26d|
|39|27|True|o => 2d => 27o => 27|
|40|28|False|o => 2d => 28e|
|41|29|False|o => 2d => 29d|
|42|2A|True|o => 2d => 2Ao => 2A|
|43|2B|False|o => 2d => 2Be|
|44|2C|False|o => 2d => 2Cd|
|45|2D|True|o => 2d => 2Do => 2D|
|46|2E|False|o => 2d => 2Ee|
|47|2F|False|o => 2d => 2Fd|
|48|30|True|o => 3o => 30o => 30|
|49|31|False|o => 3o => 31e|
|50|32|False|o => 3o => 32d|
|51|33|True|o => 3o => 33o => 33|
|52|34|False|o => 3o => 34e|
|53|35|False|o => 3o => 35d|
|54|36|True|o => 3o => 36o => 36|
|55|37|False|o => 3o => 37e|
|56|38|False|o => 3o => 38d|
|57|39|True|o => 3o => 39o => 39|
|58|3A|False|o => 3o => 3Ae|
|59|3B|False|o => 3o => 3Bd|
|60|3C|True|o => 3o => 3Co => 3C|
|61|3D|False|o => 3o => 3De|
|62|3E|False|o => 3o => 3Ed|
|63|3F|True|o => 3o => 3Fo => 3F|
|64|40|False|o => 4e => 40e|
|65|41|False|o => 4e => 41d|
|66|42|True|o => 4e => 42o => 42|
|67|43|False|o => 4e => 43e|
|68|44|False|o => 4e => 44d|
|69|45|True|o => 4e => 45o => 45|
|70|46|False|o => 4e => 46e|
|71|47|False|o => 4e => 47d|
|72|48|True|o => 4e => 48o => 48|
|73|49|False|o => 4e => 49e|
|74|4A|False|o => 4e => 4Ad|
|75|4B|True|o => 4e => 4Bo => 4B|
|76|4C|False|o => 4e => 4Ce|
|77|4D|False|o => 4e => 4Dd|
|78|4E|True|o => 4e => 4Eo => 4E|
|79|4F|False|o => 4e => 4Fe|
|80|50|False|o => 5d => 50d|
|81|51|True|o => 5d => 51o => 51|
|82|52|False|o => 5d => 52e|
|83|53|False|o => 5d => 53d|
|84|54|True|o => 5d => 54o => 54|
|85|55|False|o => 5d => 55e|
|86|56|False|o => 5d => 56d|
|87|57|True|o => 5d => 57o => 57|
|88|58|False|o => 5d => 58e|
|89|59|False|o => 5d => 59d|
|90|5A|True|o => 5d => 5Ao => 5A|
|91|5B|False|o => 5d => 5Be|
|92|5C|False|o => 5d => 5Cd|
|93|5D|True|o => 5d => 5Do => 5D|
|94|5E|False|o => 5d => 5Ee|
|95|5F|False|o => 5d => 5Fd|
|96|60|True|o => 6o => 60o => 60|
|97|61|False|o => 6o => 61e|
|98|62|False|o => 6o => 62d|
|99|63|True|o => 6o => 63o => 63|
|100|64|False|o => 6o => 64e|
|101|65|False|o => 6o => 65d|
|102|66|True|o => 6o => 66o => 66|
|103|67|False|o => 6o => 67e|
|104|68|False|o => 6o => 68d|
|105|69|True|o => 6o => 69o => 69|
|106|6A|False|o => 6o => 6Ae|
|107|6B|False|o => 6o => 6Bd|
|108|6C|True|o => 6o => 6Co => 6C|
|109|6D|False|o => 6o => 6De|
|110|6E|False|o => 6o => 6Ed|
|111|6F|True|o => 6o => 6Fo => 6F|
|112|70|False|o => 7e => 70e|
|113|71|False|o => 7e => 71d|
|114|72|True|o => 7e => 72o => 72|
|115|73|False|o => 7e => 73e|
|116|74|False|o => 7e => 74d|
|117|75|True|o => 7e => 75o => 75|
|118|76|False|o => 7e => 76e|
|119|77|False|o => 7e => 77d|
|120|78|True|o => 7e => 78o => 78|
|121|79|False|o => 7e => 79e|
|122|7A|False|o => 7e => 7Ad|
|123|7B|True|o => 7e => 7Bo => 7B|
|124|7C|False|o => 7e => 7Ce|
|125|7D|False|o => 7e => 7Dd|
|126|7E|True|o => 7e => 7Eo => 7E|
|127|7F|False|o => 7e => 7Fe|
|128|80|False|o => 8d => 80d|
|129|81|True|o => 8d => 81o => 81|
|130|82|False|o => 8d => 82e|
|131|83|False|o => 8d => 83d|
|132|84|True|o => 8d => 84o => 84|
|133|85|False|o => 8d => 85e|
|134|86|False|o => 8d => 86d|
|135|87|True|o => 8d => 87o => 87|
|136|88|False|o => 8d => 88e|
|137|89|False|o => 8d => 89d|
|138|8A|True|o => 8d => 8Ao => 8A|
|139|8B|False|o => 8d => 8Be|
|140|8C|False|o => 8d => 8Cd|
|141|8D|True|o => 8d => 8Do => 8D|
|142|8E|False|o => 8d => 8Ee|
|143|8F|False|o => 8d => 8Fd|
|144|90|True|o => 9o => 90o => 90|
|145|91|False|o => 9o => 91e|
|146|92|False|o => 9o => 92d|
|147|93|True|o => 9o => 93o => 93|
|148|94|False|o => 9o => 94e|
|149|95|False|o => 9o => 95d|
|150|96|True|o => 9o => 96o => 96|
|151|97|False|o => 9o => 97e|
|152|98|False|o => 9o => 98d|
|153|99|True|o => 9o => 99o => 99|
|154|9A|False|o => 9o => 9Ae|
|155|9B|False|o => 9o => 9Bd|
|156|9C|True|o => 9o => 9Co => 9C|
|157|9D|False|o => 9o => 9De|
|158|9E|False|o => 9o => 9Ed|
|159|9F|True|o => 9o => 9Fo => 9F|
|160|A0|False|o => Ae => A0e|
|161|A1|False|o => Ae => A1d|
|162|A2|True|o => Ae => A2o => A2|
|163|A3|False|o => Ae => A3e|
|164|A4|False|o => Ae => A4d|
|165|A5|True|o => Ae => A5o => A5|
|166|A6|False|o => Ae => A6e|
|167|A7|False|o => Ae => A7d|
|168|A8|True|o => Ae => A8o => A8|
|169|A9|False|o => Ae => A9e|
|170|AA|False|o => Ae => AAd|
|171|AB|True|o => Ae => ABo => AB|
|172|AC|False|o => Ae => ACe|
|173|AD|False|o => Ae => ADd|
|174|AE|True|o => Ae => AEo => AE|
|175|AF|False|o => Ae => AFe|
|176|B0|False|o => Bd => B0d|
|177|B1|True|o => Bd => B1o => B1|
|178|B2|False|o => Bd => B2e|
|179|B3|False|o => Bd => B3d|
|180|B4|True|o => Bd => B4o => B4|
|181|B5|False|o => Bd => B5e|
|182|B6|False|o => Bd => B6d|
|183|B7|True|o => Bd => B7o => B7|
|184|B8|False|o => Bd => B8e|
|185|B9|False|o => Bd => B9d|
|186|BA|True|o => Bd => BAo => BA|
|187|BB|False|o => Bd => BBe|
|188|BC|False|o => Bd => BCd|
|189|BD|True|o => Bd => BDo => BD|
|190|BE|False|o => Bd => BEe|
|191|BF|False|o => Bd => BFd|
|192|C0|True|o => Co => C0o => C0|
|193|C1|False|o => Co => C1e|
|194|C2|False|o => Co => C2d|
|195|C3|True|o => Co => C3o => C3|
|196|C4|False|o => Co => C4e|
|197|C5|False|o => Co => C5d|
|198|C6|True|o => Co => C6o => C6|
|199|C7|False|o => Co => C7e|
|200|C8|False|o => Co => C8d|
|201|C9|True|o => Co => C9o => C9|
|202|CA|False|o => Co => CAe|
|203|CB|False|o => Co => CBd|
|204|CC|True|o => Co => CCo => CC|
|205|CD|False|o => Co => CDe|
|206|CE|False|o => Co => CEd|
|207|CF|True|o => Co => CFo => CF|
|208|D0|False|o => De => D0e|
|209|D1|False|o => De => D1d|
|210|D2|True|o => De => D2o => D2|
|211|D3|False|o => De => D3e|
|212|D4|False|o => De => D4d|
|213|D5|True|o => De => D5o => D5|
|214|D6|False|o => De => D6e|
|215|D7|False|o => De => D7d|
|216|D8|True|o => De => D8o => D8|
|217|D9|False|o => De => D9e|
|218|DA|False|o => De => DAd|
|219|DB|True|o => De => DBo => DB|
|220|DC|False|o => De => DCe|
|221|DD|False|o => De => DDd|
|222|DE|True|o => De => DEo => DE|
|223|DF|False|o => De => DFe|
|224|E0|False|o => Ed => E0d|
|225|E1|True|o => Ed => E1o => E1|
|226|E2|False|o => Ed => E2e|
|227|E3|False|o => Ed => E3d|
|228|E4|True|o => Ed => E4o => E4|
|229|E5|False|o => Ed => E5e|
|230|E6|False|o => Ed => E6d|
|231|E7|True|o => Ed => E7o => E7|
|232|E8|False|o => Ed => E8e|
|233|E9|False|o => Ed => E9d|
|234|EA|True|o => Ed => EAo => EA|
|235|EB|False|o => Ed => EBe|
|236|EC|False|o => Ed => ECd|
|237|ED|True|o => Ed => EDo => ED|
|238|EE|False|o => Ed => EEe|
|239|EF|False|o => Ed => EFd|
|240|F0|True|o => Fo => F0o => F0|
|241|F1|False|o => Fo => F1e|
|242|F2|False|o => Fo => F2d|
|243|F3|True|o => Fo => F3o => F3|
|244|F4|False|o => Fo => F4e|
|245|F5|False|o => Fo => F5d|
|246|F6|True|o => Fo => F6o => F6|
|247|F7|False|o => Fo => F7e|
|248|F8|False|o => Fo => F8d|
|249|F9|True|o => Fo => F9o => F9|
|250|FA|False|o => Fo => FAe|
|251|FB|False|o => Fo => FBd|
|252|FC|True|o => Fo => FCo => FC|
|253|FD|False|o => Fo => FDe|
|254|FE|False|o => Fo => FEd|
|255|FF|True|o => Fo => FFo => FF|
|256|100|False|o => 1e => 10e => 100e|
|257|101|False|o => 1e => 10e => 101d|
|258|102|True|o => 1e => 10e => 102o => 102|
|259|103|False|o => 1e => 10e => 103e|
|260|104|False|o => 1e => 10e => 104d|
|261|105|True|o => 1e => 10e => 105o => 105|
|262|106|False|o => 1e => 10e => 106e|
|263|107|False|o => 1e => 10e => 107d|
|264|108|True|o => 1e => 10e => 108o => 108|
|265|109|False|o => 1e => 10e => 109e|
|266|10A|False|o => 1e => 10e => 10Ad|
|267|10B|True|o => 1e => 10e => 10Bo => 10B|
|268|10C|False|o => 1e => 10e => 10Ce|
|269|10D|False|o => 1e => 10e => 10Dd|
|270|10E|True|o => 1e => 10e => 10Eo => 10E|
|271|10F|False|o => 1e => 10e => 10Fe|
|272|110|False|o => 1e => 11d => 110d|
|273|111|True|o => 1e => 11d => 111o => 111|
|274|112|False|o => 1e => 11d => 112e|
|275|113|False|o => 1e => 11d => 113d|
|276|114|True|o => 1e => 11d => 114o => 114|
|277|115|False|o => 1e => 11d => 115e|
|278|116|False|o => 1e => 11d => 116d|
|279|117|True|o => 1e => 11d => 117o => 117|
|280|118|False|o => 1e => 11d => 118e|
|281|119|False|o => 1e => 11d => 119d|
|282|11A|True|o => 1e => 11d => 11Ao => 11A|
|283|11B|False|o => 1e => 11d => 11Be|
|284|11C|False|o => 1e => 11d => 11Cd|
|285|11D|True|o => 1e => 11d => 11Do => 11D|
|286|11E|False|o => 1e => 11d => 11Ee|
|287|11F|False|o => 1e => 11d => 11Fd|
|288|120|True|o => 1e => 12o => 120o => 120|
|289|121|False|o => 1e => 12o => 121e|
|290|122|False|o => 1e => 12o => 122d|
|291|123|True|o => 1e => 12o => 123o => 123|
|292|124|False|o => 1e => 12o => 124e|
|293|125|False|o => 1e => 12o => 125d|
|294|126|True|o => 1e => 12o => 126o => 126|
|295|127|False|o => 1e => 12o => 127e|
|296|128|False|o => 1e => 12o => 128d|
|297|129|True|o => 1e => 12o => 129o => 129|
|298|12A|False|o => 1e => 12o => 12Ae|
|299|12B|False|o => 1e => 12o => 12Bd|
|300|12C|True|o => 1e => 12o => 12Co => 12C|
|301|12D|False|o => 1e => 12o => 12De|
|302|12E|False|o => 1e => 12o => 12Ed|
|303|12F|True|o => 1e => 12o => 12Fo => 12F|
|304|130|False|o => 1e => 13e => 130e|
|305|131|False|o => 1e => 13e => 131d|
|306|132|True|o => 1e => 13e => 132o => 132|
|307|133|False|o => 1e => 13e => 133e|
|308|134|False|o => 1e => 13e => 134d|
|309|135|True|o => 1e => 13e => 135o => 135|
|310|136|False|o => 1e => 13e => 136e|
|311|137|False|o => 1e => 13e => 137d|
|312|138|True|o => 1e => 13e => 138o => 138|
|313|139|False|o => 1e => 13e => 139e|
|314|13A|False|o => 1e => 13e => 13Ad|
|315|13B|True|o => 1e => 13e => 13Bo => 13B|
|316|13C|False|o => 1e => 13e => 13Ce|
|317|13D|False|o => 1e => 13e => 13Dd|
|318|13E|True|o => 1e => 13e => 13Eo => 13E|
|319|13F|False|o => 1e => 13e => 13Fe|
|320|140|False|o => 1e => 14d => 140d|
|321|141|True|o => 1e => 14d => 141o => 141|
|322|142|False|o => 1e => 14d => 142e|
|323|143|False|o => 1e => 14d => 143d|
|324|144|True|o => 1e => 14d => 144o => 144|
|325|145|False|o => 1e => 14d => 145e|
|326|146|False|o => 1e => 14d => 146d|
|327|147|True|o => 1e => 14d => 147o => 147|
|328|148|False|o => 1e => 14d => 148e|
|329|149|False|o => 1e => 14d => 149d|
|330|14A|True|o => 1e => 14d => 14Ao => 14A|
|331|14B|False|o => 1e => 14d => 14Be|
|332|14C|False|o => 1e => 14d => 14Cd|
|333|14D|True|o => 1e => 14d => 14Do => 14D|
|334|14E|False|o => 1e => 14d => 14Ee|
|335|14F|False|o => 1e => 14d => 14Fd|
|336|150|True|o => 1e => 15o => 150o => 150|
|337|151|False|o => 1e => 15o => 151e|
|338|152|False|o => 1e => 15o => 152d|
|339|153|True|o => 1e => 15o => 153o => 153|
|340|154|False|o => 1e => 15o => 154e|
|341|155|False|o => 1e => 15o => 155d|
|342|156|True|o => 1e => 15o => 156o => 156|
|343|157|False|o => 1e => 15o => 157e|
|344|158|False|o => 1e => 15o => 158d|
|345|159|True|o => 1e => 15o => 159o => 159|
|346|15A|False|o => 1e => 15o => 15Ae|
|347|15B|False|o => 1e => 15o => 15Bd|
|348|15C|True|o => 1e => 15o => 15Co => 15C|
|349|15D|False|o => 1e => 15o => 15De|
|350|15E|False|o => 1e => 15o => 15Ed|
|351|15F|True|o => 1e => 15o => 15Fo => 15F|
|352|160|False|o => 1e => 16e => 160e|
|353|161|False|o => 1e => 16e => 161d|
|354|162|True|o => 1e => 16e => 162o => 162|
|355|163|False|o => 1e => 16e => 163e|
|356|164|False|o => 1e => 16e => 164d|
|357|165|True|o => 1e => 16e => 165o => 165|
|358|166|False|o => 1e => 16e => 166e|
|359|167|False|o => 1e => 16e => 167d|
|360|168|True|o => 1e => 16e => 168o => 168|
|361|169|False|o => 1e => 16e => 169e|
|362|16A|False|o => 1e => 16e => 16Ad|
|363|16B|True|o => 1e => 16e => 16Bo => 16B|
|364|16C|False|o => 1e => 16e => 16Ce|
|365|16D|False|o => 1e => 16e => 16Dd|
|366|16E|True|o => 1e => 16e => 16Eo => 16E|
|367|16F|False|o => 1e => 16e => 16Fe|
|368|170|False|o => 1e => 17d => 170d|
|369|171|True|o => 1e => 17d => 171o => 171|
|370|172|False|o => 1e => 17d => 172e|
|371|173|False|o => 1e => 17d => 173d|
|372|174|True|o => 1e => 17d => 174o => 174|
|373|175|False|o => 1e => 17d => 175e|
|374|176|False|o => 1e => 17d => 176d|
|375|177|True|o => 1e => 17d => 177o => 177|
|376|178|False|o => 1e => 17d => 178e|
|377|179|False|o => 1e => 17d => 179d|
|378|17A|True|o => 1e => 17d => 17Ao => 17A|
|379|17B|False|o => 1e => 17d => 17Be|
|380|17C|False|o => 1e => 17d => 17Cd|
|381|17D|True|o => 1e => 17d => 17Do => 17D|
|382|17E|False|o => 1e => 17d => 17Ee|
|383|17F|False|o => 1e => 17d => 17Fd|
|384|180|True|o => 1e => 18o => 180o => 180|
|385|181|False|o => 1e => 18o => 181e|
|386|182|False|o => 1e => 18o => 182d|
|387|183|True|o => 1e => 18o => 183o => 183|
|388|184|False|o => 1e => 18o => 184e|
|389|185|False|o => 1e => 18o => 185d|
|390|186|True|o => 1e => 18o => 186o => 186|
|391|187|False|o => 1e => 18o => 187e|
|392|188|False|o => 1e => 18o => 188d|
|393|189|True|o => 1e => 18o => 189o => 189|
|394|18A|False|o => 1e => 18o => 18Ae|
|395|18B|False|o => 1e => 18o => 18Bd|
|396|18C|True|o => 1e => 18o => 18Co => 18C|
|397|18D|False|o => 1e => 18o => 18De|
|398|18E|False|o => 1e => 18o => 18Ed|
|399|18F|True|o => 1e => 18o => 18Fo => 18F|
|400|190|False|o => 1e => 19e => 190e|
|401|191|False|o => 1e => 19e => 191d|
|402|192|True|o => 1e => 19e => 192o => 192|
|403|193|False|o => 1e => 19e => 193e|
|404|194|False|o => 1e => 19e => 194d|
|405|195|True|o => 1e => 19e => 195o => 195|
|406|196|False|o => 1e => 19e => 196e|
|407|197|False|o => 1e => 19e => 197d|
|408|198|True|o => 1e => 19e => 198o => 198|
|409|199|False|o => 1e => 19e => 199e|
|410|19A|False|o => 1e => 19e => 19Ad|
|411|19B|True|o => 1e => 19e => 19Bo => 19B|
|412|19C|False|o => 1e => 19e => 19Ce|
|413|19D|False|o => 1e => 19e => 19Dd|
|414|19E|True|o => 1e => 19e => 19Eo => 19E|
|415|19F|False|o => 1e => 19e => 19Fe|
|416|1A0|False|o => 1e => 1Ad => 1A0d|
|417|1A1|True|o => 1e => 1Ad => 1A1o => 1A1|
|418|1A2|False|o => 1e => 1Ad => 1A2e|
|419|1A3|False|o => 1e => 1Ad => 1A3d|
|420|1A4|True|o => 1e => 1Ad => 1A4o => 1A4|
|421|1A5|False|o => 1e => 1Ad => 1A5e|
|422|1A6|False|o => 1e => 1Ad => 1A6d|
|423|1A7|True|o => 1e => 1Ad => 1A7o => 1A7|
|424|1A8|False|o => 1e => 1Ad => 1A8e|
|425|1A9|False|o => 1e => 1Ad => 1A9d|
|426|1AA|True|o => 1e => 1Ad => 1AAo => 1AA|
|427|1AB|False|o => 1e => 1Ad => 1ABe|
|428|1AC|False|o => 1e => 1Ad => 1ACd|
|429|1AD|True|o => 1e => 1Ad => 1ADo => 1AD|
|430|1AE|False|o => 1e => 1Ad => 1AEe|
|431|1AF|False|o => 1e => 1Ad => 1AFd|
|432|1B0|True|o => 1e => 1Bo => 1B0o => 1B0|
|433|1B1|False|o => 1e => 1Bo => 1B1e|
|434|1B2|False|o => 1e => 1Bo => 1B2d|
|435|1B3|True|o => 1e => 1Bo => 1B3o => 1B3|
|436|1B4|False|o => 1e => 1Bo => 1B4e|
|437|1B5|False|o => 1e => 1Bo => 1B5d|
|438|1B6|True|o => 1e => 1Bo => 1B6o => 1B6|
|439|1B7|False|o => 1e => 1Bo => 1B7e|
|440|1B8|False|o => 1e => 1Bo => 1B8d|
|441|1B9|True|o => 1e => 1Bo => 1B9o => 1B9|
|442|1BA|False|o => 1e => 1Bo => 1BAe|
|443|1BB|False|o => 1e => 1Bo => 1BBd|
|444|1BC|True|o => 1e => 1Bo => 1BCo => 1BC|
|445|1BD|False|o => 1e => 1Bo => 1BDe|
|446|1BE|False|o => 1e => 1Bo => 1BEd|
|447|1BF|True|o => 1e => 1Bo => 1BFo => 1BF|
|448|1C0|False|o => 1e => 1Ce => 1C0e|
|449|1C1|False|o => 1e => 1Ce => 1C1d|
|450|1C2|True|o => 1e => 1Ce => 1C2o => 1C2|
|451|1C3|False|o => 1e => 1Ce => 1C3e|
|452|1C4|False|o => 1e => 1Ce => 1C4d|
|453|1C5|True|o => 1e => 1Ce => 1C5o => 1C5|
|454|1C6|False|o => 1e => 1Ce => 1C6e|
|455|1C7|False|o => 1e => 1Ce => 1C7d|
|456|1C8|True|o => 1e => 1Ce => 1C8o => 1C8|
|457|1C9|False|o => 1e => 1Ce => 1C9e|
|458|1CA|False|o => 1e => 1Ce => 1CAd|
|459|1CB|True|o => 1e => 1Ce => 1CBo => 1CB|
|460|1CC|False|o => 1e => 1Ce => 1CCe|
|461|1CD|False|o => 1e => 1Ce => 1CDd|
|462|1CE|True|o => 1e => 1Ce => 1CEo => 1CE|
|463|1CF|False|o => 1e => 1Ce => 1CFe|
|464|1D0|False|o => 1e => 1Dd => 1D0d|
|465|1D1|True|o => 1e => 1Dd => 1D1o => 1D1|
|466|1D2|False|o => 1e => 1Dd => 1D2e|
|467|1D3|False|o => 1e => 1Dd => 1D3d|
|468|1D4|True|o => 1e => 1Dd => 1D4o => 1D4|
|469|1D5|False|o => 1e => 1Dd => 1D5e|
|470|1D6|False|o => 1e => 1Dd => 1D6d|
|471|1D7|True|o => 1e => 1Dd => 1D7o => 1D7|
|472|1D8|False|o => 1e => 1Dd => 1D8e|
|473|1D9|False|o => 1e => 1Dd => 1D9d|
|474|1DA|True|o => 1e => 1Dd => 1DAo => 1DA|
|475|1DB|False|o => 1e => 1Dd => 1DBe|
|476|1DC|False|o => 1e => 1Dd => 1DCd|
|477|1DD|True|o => 1e => 1Dd => 1DDo => 1DD|
|478|1DE|False|o => 1e => 1Dd => 1DEe|
|479|1DF|False|o => 1e => 1Dd => 1DFd|
|480|1E0|True|o => 1e => 1Eo => 1E0o => 1E0|
|481|1E1|False|o => 1e => 1Eo => 1E1e|
|482|1E2|False|o => 1e => 1Eo => 1E2d|
|483|1E3|True|o => 1e => 1Eo => 1E3o => 1E3|
|484|1E4|False|o => 1e => 1Eo => 1E4e|
|485|1E5|False|o => 1e => 1Eo => 1E5d|
|486|1E6|True|o => 1e => 1Eo => 1E6o => 1E6|
|487|1E7|False|o => 1e => 1Eo => 1E7e|
|488|1E8|False|o => 1e => 1Eo => 1E8d|
|489|1E9|True|o => 1e => 1Eo => 1E9o => 1E9|
|490|1EA|False|o => 1e => 1Eo => 1EAe|
|491|1EB|False|o => 1e => 1Eo => 1EBd|
|492|1EC|True|o => 1e => 1Eo => 1ECo => 1EC|
|493|1ED|False|o => 1e => 1Eo => 1EDe|
|494|1EE|False|o => 1e => 1Eo => 1EEd|
|495|1EF|True|o => 1e => 1Eo => 1EFo => 1EF|
|496|1F0|False|o => 1e => 1Fe => 1F0e|
|497|1F1|False|o => 1e => 1Fe => 1F1d|
|498|1F2|True|o => 1e => 1Fe => 1F2o => 1F2|
|499|1F3|False|o => 1e => 1Fe => 1F3e|
|500|1F4|False|o => 1e => 1Fe => 1F4d|
|501|1F5|True|o => 1e => 1Fe => 1F5o => 1F5|
|502|1F6|False|o => 1e => 1Fe => 1F6e|
|503|1F7|False|o => 1e => 1Fe => 1F7d|
|504|1F8|True|o => 1e => 1Fe => 1F8o => 1F8|
|505|1F9|False|o => 1e => 1Fe => 1F9e|
|506|1FA|False|o => 1e => 1Fe => 1FAd|
|507|1FB|True|o => 1e => 1Fe => 1FBo => 1FB|
|508|1FC|False|o => 1e => 1Fe => 1FCe|
|509|1FD|False|o => 1e => 1Fe => 1FDd|
|510|1FE|True|o => 1e => 1Fe => 1FEo => 1FE|
|511|1FF|False|o => 1e => 1Fe => 1FFe|
|512|200|False|o => 2d => 20d => 200d|
|513|201|True|o => 2d => 20d => 201o => 201|
|514|202|False|o => 2d => 20d => 202e|
|515|203|False|o => 2d => 20d => 203d|
|516|204|True|o => 2d => 20d => 204o => 204|
|517|205|False|o => 2d => 20d => 205e|
|518|206|False|o => 2d => 20d => 206d|
|519|207|True|o => 2d => 20d => 207o => 207|
|520|208|False|o => 2d => 20d => 208e|
|521|209|False|o => 2d => 20d => 209d|
|522|20A|True|o => 2d => 20d => 20Ao => 20A|
|523|20B|False|o => 2d => 20d => 20Be|
|524|20C|False|o => 2d => 20d => 20Cd|
|525|20D|True|o => 2d => 20d => 20Do => 20D|
|526|20E|False|o => 2d => 20d => 20Ee|
|527|20F|False|o => 2d => 20d => 20Fd|
|528|210|True|o => 2d => 21o => 210o => 210|
|529|211|False|o => 2d => 21o => 211e|
|530|212|False|o => 2d => 21o => 212d|
|531|213|True|o => 2d => 21o => 213o => 213|
|532|214|False|o => 2d => 21o => 214e|
|533|215|False|o => 2d => 21o => 215d|
|534|216|True|o => 2d => 21o => 216o => 216|
|535|217|False|o => 2d => 21o => 217e|
|536|218|False|o => 2d => 21o => 218d|
|537|219|True|o => 2d => 21o => 219o => 219|
|538|21A|False|o => 2d => 21o => 21Ae|
|539|21B|False|o => 2d => 21o => 21Bd|
|540|21C|True|o => 2d => 21o => 21Co => 21C|
|541|21D|False|o => 2d => 21o => 21De|
|542|21E|False|o => 2d => 21o => 21Ed|
|543|21F|True|o => 2d => 21o => 21Fo => 21F|
|544|220|False|o => 2d => 22e => 220e|
|545|221|False|o => 2d => 22e => 221d|
|546|222|True|o => 2d => 22e => 222o => 222|
|547|223|False|o => 2d => 22e => 223e|
|548|224|False|o => 2d => 22e => 224d|
|549|225|True|o => 2d => 22e => 225o => 225|
|550|226|False|o => 2d => 22e => 226e|
|551|227|False|o => 2d => 22e => 227d|
|552|228|True|o => 2d => 22e => 228o => 228|
|553|229|False|o => 2d => 22e => 229e|
|554|22A|False|o => 2d => 22e => 22Ad|
|555|22B|True|o => 2d => 22e => 22Bo => 22B|
|556|22C|False|o => 2d => 22e => 22Ce|
|557|22D|False|o => 2d => 22e => 22Dd|
|558|22E|True|o => 2d => 22e => 22Eo => 22E|
|559|22F|False|o => 2d => 22e => 22Fe|
|560|230|False|o => 2d => 23d => 230d|
|561|231|True|o => 2d => 23d => 231o => 231|
|562|232|False|o => 2d => 23d => 232e|
|563|233|False|o => 2d => 23d => 233d|
|564|234|True|o => 2d => 23d => 234o => 234|
|565|235|False|o => 2d => 23d => 235e|
|566|236|False|o => 2d => 23d => 236d|
|567|237|True|o => 2d => 23d => 237o => 237|
|568|238|False|o => 2d => 23d => 238e|
|569|239|False|o => 2d => 23d => 239d|
|570|23A|True|o => 2d => 23d => 23Ao => 23A|
|571|23B|False|o => 2d => 23d => 23Be|
|572|23C|False|o => 2d => 23d => 23Cd|
|573|23D|True|o => 2d => 23d => 23Do => 23D|
|574|23E|False|o => 2d => 23d => 23Ee|
|575|23F|False|o => 2d => 23d => 23Fd|
|576|240|True|o => 2d => 24o => 240o => 240|
|577|241|False|o => 2d => 24o => 241e|
|578|242|False|o => 2d => 24o => 242d|
|579|243|True|o => 2d => 24o => 243o => 243|
|580|244|False|o => 2d => 24o => 244e|
|581|245|False|o => 2d => 24o => 245d|
|582|246|True|o => 2d => 24o => 246o => 246|
|583|247|False|o => 2d => 24o => 247e|
|584|248|False|o => 2d => 24o => 248d|
|585|249|True|o => 2d => 24o => 249o => 249|
|586|24A|False|o => 2d => 24o => 24Ae|
|587|24B|False|o => 2d => 24o => 24Bd|
|588|24C|True|o => 2d => 24o => 24Co => 24C|
|589|24D|False|o => 2d => 24o => 24De|
|590|24E|False|o => 2d => 24o => 24Ed|
|591|24F|True|o => 2d => 24o => 24Fo => 24F|
|592|250|False|o => 2d => 25e => 250e|
|593|251|False|o => 2d => 25e => 251d|
|594|252|True|o => 2d => 25e => 252o => 252|
|595|253|False|o => 2d => 25e => 253e|
|596|254|False|o => 2d => 25e => 254d|
|597|255|True|o => 2d => 25e => 255o => 255|
|598|256|False|o => 2d => 25e => 256e|
|599|257|False|o => 2d => 25e => 257d|
|600|258|True|o => 2d => 25e => 258o => 258|
|601|259|False|o => 2d => 25e => 259e|
|602|25A|False|o => 2d => 25e => 25Ad|
|603|25B|True|o => 2d => 25e => 25Bo => 25B|
|604|25C|False|o => 2d => 25e => 25Ce|
|605|25D|False|o => 2d => 25e => 25Dd|
|606|25E|True|o => 2d => 25e => 25Eo => 25E|
|607|25F|False|o => 2d => 25e => 25Fe|
|608|260|False|o => 2d => 26d => 260d|
|609|261|True|o => 2d => 26d => 261o => 261|
|610|262|False|o => 2d => 26d => 262e|
|611|263|False|o => 2d => 26d => 263d|
|612|264|True|o => 2d => 26d => 264o => 264|
|613|265|False|o => 2d => 26d => 265e|
|614|266|False|o => 2d => 26d => 266d|
|615|267|True|o => 2d => 26d => 267o => 267|
|616|268|False|o => 2d => 26d => 268e|
|617|269|False|o => 2d => 26d => 269d|
|618|26A|True|o => 2d => 26d => 26Ao => 26A|
|619|26B|False|o => 2d => 26d => 26Be|
|620|26C|False|o => 2d => 26d => 26Cd|
|621|26D|True|o => 2d => 26d => 26Do => 26D|
|622|26E|False|o => 2d => 26d => 26Ee|
|623|26F|False|o => 2d => 26d => 26Fd|
|624|270|True|o => 2d => 27o => 270o => 270|
|625|271|False|o => 2d => 27o => 271e|
|626|272|False|o => 2d => 27o => 272d|
|627|273|True|o => 2d => 27o => 273o => 273|
|628|274|False|o => 2d => 27o => 274e|
|629|275|False|o => 2d => 27o => 275d|
|630|276|True|o => 2d => 27o => 276o => 276|
|631|277|False|o => 2d => 27o => 277e|
|632|278|False|o => 2d => 27o => 278d|
|633|279|True|o => 2d => 27o => 279o => 279|
|634|27A|False|o => 2d => 27o => 27Ae|
|635|27B|False|o => 2d => 27o => 27Bd|
|636|27C|True|o => 2d => 27o => 27Co => 27C|
|637|27D|False|o => 2d => 27o => 27De|
|638|27E|False|o => 2d => 27o => 27Ed|
|639|27F|True|o => 2d => 27o => 27Fo => 27F|
|640|280|False|o => 2d => 28e => 280e|
|641|281|False|o => 2d => 28e => 281d|
|642|282|True|o => 2d => 28e => 282o => 282|
|643|283|False|o => 2d => 28e => 283e|
|644|284|False|o => 2d => 28e => 284d|
|645|285|True|o => 2d => 28e => 285o => 285|
|646|286|False|o => 2d => 28e => 286e|
|647|287|False|o => 2d => 28e => 287d|
|648|288|True|o => 2d => 28e => 288o => 288|
|649|289|False|o => 2d => 28e => 289e|
|650|28A|False|o => 2d => 28e => 28Ad|
|651|28B|True|o => 2d => 28e => 28Bo => 28B|
|652|28C|False|o => 2d => 28e => 28Ce|
|653|28D|False|o => 2d => 28e => 28Dd|
|654|28E|True|o => 2d => 28e => 28Eo => 28E|
|655|28F|False|o => 2d => 28e => 28Fe|
|656|290|False|o => 2d => 29d => 290d|
|657|291|True|o => 2d => 29d => 291o => 291|
|658|292|False|o => 2d => 29d => 292e|
|659|293|False|o => 2d => 29d => 293d|
|660|294|True|o => 2d => 29d => 294o => 294|
|661|295|False|o => 2d => 29d => 295e|
|662|296|False|o => 2d => 29d => 296d|
|663|297|True|o => 2d => 29d => 297o => 297|
|664|298|False|o => 2d => 29d => 298e|
|665|299|False|o => 2d => 29d => 299d|
|666|29A|True|o => 2d => 29d => 29Ao => 29A|
|667|29B|False|o => 2d => 29d => 29Be|
|668|29C|False|o => 2d => 29d => 29Cd|
|669|29D|True|o => 2d => 29d => 29Do => 29D|
|670|29E|False|o => 2d => 29d => 29Ee|
|671|29F|False|o => 2d => 29d => 29Fd|
|672|2A0|True|o => 2d => 2Ao => 2A0o => 2A0|
|673|2A1|False|o => 2d => 2Ao => 2A1e|
|674|2A2|False|o => 2d => 2Ao => 2A2d|
|675|2A3|True|o => 2d => 2Ao => 2A3o => 2A3|
|676|2A4|False|o => 2d => 2Ao => 2A4e|
|677|2A5|False|o => 2d => 2Ao => 2A5d|
|678|2A6|True|o => 2d => 2Ao => 2A6o => 2A6|
|679|2A7|False|o => 2d => 2Ao => 2A7e|
|680|2A8|False|o => 2d => 2Ao => 2A8d|
|681|2A9|True|o => 2d => 2Ao => 2A9o => 2A9|
|682|2AA|False|o => 2d => 2Ao => 2AAe|
|683|2AB|False|o => 2d => 2Ao => 2ABd|
|684|2AC|True|o => 2d => 2Ao => 2ACo => 2AC|
|685|2AD|False|o => 2d => 2Ao => 2ADe|
|686|2AE|False|o => 2d => 2Ao => 2AEd|
|687|2AF|True|o => 2d => 2Ao => 2AFo => 2AF|
|688|2B0|False|o => 2d => 2Be => 2B0e|
|689|2B1|False|o => 2d => 2Be => 2B1d|
|690|2B2|True|o => 2d => 2Be => 2B2o => 2B2|
|691|2B3|False|o => 2d => 2Be => 2B3e|
|692|2B4|False|o => 2d => 2Be => 2B4d|
|693|2B5|True|o => 2d => 2Be => 2B5o => 2B5|
|694|2B6|False|o => 2d => 2Be => 2B6e|
|695|2B7|False|o => 2d => 2Be => 2B7d|
|696|2B8|True|o => 2d => 2Be => 2B8o => 2B8|
|697|2B9|False|o => 2d => 2Be => 2B9e|
|698|2BA|False|o => 2d => 2Be => 2BAd|
|699|2BB|True|o => 2d => 2Be => 2BBo => 2BB|
|700|2BC|False|o => 2d => 2Be => 2BCe|
|701|2BD|False|o => 2d => 2Be => 2BDd|
|702|2BE|True|o => 2d => 2Be => 2BEo => 2BE|
|703|2BF|False|o => 2d => 2Be => 2BFe|
|704|2C0|False|o => 2d => 2Cd => 2C0d|
|705|2C1|True|o => 2d => 2Cd => 2C1o => 2C1|
|706|2C2|False|o => 2d => 2Cd => 2C2e|
|707|2C3|False|o => 2d => 2Cd => 2C3d|
|708|2C4|True|o => 2d => 2Cd => 2C4o => 2C4|
|709|2C5|False|o => 2d => 2Cd => 2C5e|
|710|2C6|False|o => 2d => 2Cd => 2C6d|
|711|2C7|True|o => 2d => 2Cd => 2C7o => 2C7|
|712|2C8|False|o => 2d => 2Cd => 2C8e|
|713|2C9|False|o => 2d => 2Cd => 2C9d|
|714|2CA|True|o => 2d => 2Cd => 2CAo => 2CA|
|715|2CB|False|o => 2d => 2Cd => 2CBe|
|716|2CC|False|o => 2d => 2Cd => 2CCd|
|717|2CD|True|o => 2d => 2Cd => 2CDo => 2CD|
|718|2CE|False|o => 2d => 2Cd => 2CEe|
|719|2CF|False|o => 2d => 2Cd => 2CFd|
|720|2D0|True|o => 2d => 2Do => 2D0o => 2D0|
|721|2D1|False|o => 2d => 2Do => 2D1e|
|722|2D2|False|o => 2d => 2Do => 2D2d|
|723|2D3|True|o => 2d => 2Do => 2D3o => 2D3|
|724|2D4|False|o => 2d => 2Do => 2D4e|
|725|2D5|False|o => 2d => 2Do => 2D5d|
|726|2D6|True|o => 2d => 2Do => 2D6o => 2D6|
|727|2D7|False|o => 2d => 2Do => 2D7e|
|728|2D8|False|o => 2d => 2Do => 2D8d|
|729|2D9|True|o => 2d => 2Do => 2D9o => 2D9|
|730|2DA|False|o => 2d => 2Do => 2DAe|
|731|2DB|False|o => 2d => 2Do => 2DBd|
|732|2DC|True|o => 2d => 2Do => 2DCo => 2DC|
|733|2DD|False|o => 2d => 2Do => 2DDe|
|734|2DE|False|o => 2d => 2Do => 2DEd|
|735|2DF|True|o => 2d => 2Do => 2DFo => 2DF|
|736|2E0|False|o => 2d => 2Ee => 2E0e|
|737|2E1|False|o => 2d => 2Ee => 2E1d|
|738|2E2|True|o => 2d => 2Ee => 2E2o => 2E2|
|739|2E3|False|o => 2d => 2Ee => 2E3e|
|740|2E4|False|o => 2d => 2Ee => 2E4d|
|741|2E5|True|o => 2d => 2Ee => 2E5o => 2E5|
|742|2E6|False|o => 2d => 2Ee => 2E6e|
|743|2E7|False|o => 2d => 2Ee => 2E7d|
|744|2E8|True|o => 2d => 2Ee => 2E8o => 2E8|
|745|2E9|False|o => 2d => 2Ee => 2E9e|
|746|2EA|False|o => 2d => 2Ee => 2EAd|
|747|2EB|True|o => 2d => 2Ee => 2EBo => 2EB|
|748|2EC|False|o => 2d => 2Ee => 2ECe|
|749|2ED|False|o => 2d => 2Ee => 2EDd|
|750|2EE|True|o => 2d => 2Ee => 2EEo => 2EE|
|751|2EF|False|o => 2d => 2Ee => 2EFe|
|752|2F0|False|o => 2d => 2Fd => 2F0d|
|753|2F1|True|o => 2d => 2Fd => 2F1o => 2F1|
|754|2F2|False|o => 2d => 2Fd => 2F2e|
|755|2F3|False|o => 2d => 2Fd => 2F3d|
|756|2F4|True|o => 2d => 2Fd => 2F4o => 2F4|
|757|2F5|False|o => 2d => 2Fd => 2F5e|
|758|2F6|False|o => 2d => 2Fd => 2F6d|
|759|2F7|True|o => 2d => 2Fd => 2F7o => 2F7|
|760|2F8|False|o => 2d => 2Fd => 2F8e|
|761|2F9|False|o => 2d => 2Fd => 2F9d|
|762|2FA|True|o => 2d => 2Fd => 2FAo => 2FA|
|763|2FB|False|o => 2d => 2Fd => 2FBe|
|764|2FC|False|o => 2d => 2Fd => 2FCd|
|765|2FD|True|o => 2d => 2Fd => 2FDo => 2FD|
|766|2FE|False|o => 2d => 2Fd => 2FEe|
|767|2FF|False|o => 2d => 2Fd => 2FFd|
|768|300|True|o => 3o => 30o => 300o => 300|
|769|301|False|o => 3o => 30o => 301e|
|770|302|False|o => 3o => 30o => 302d|
|771|303|True|o => 3o => 30o => 303o => 303|
|772|304|False|o => 3o => 30o => 304e|
|773|305|False|o => 3o => 30o => 305d|
|774|306|True|o => 3o => 30o => 306o => 306|
|775|307|False|o => 3o => 30o => 307e|
|776|308|False|o => 3o => 30o => 308d|
|777|309|True|o => 3o => 30o => 309o => 309|
|778|30A|False|o => 3o => 30o => 30Ae|
|779|30B|False|o => 3o => 30o => 30Bd|
|780|30C|True|o => 3o => 30o => 30Co => 30C|
|781|30D|False|o => 3o => 30o => 30De|
|782|30E|False|o => 3o => 30o => 30Ed|
|783|30F|True|o => 3o => 30o => 30Fo => 30F|
|784|310|False|o => 3o => 31e => 310e|
|785|311|False|o => 3o => 31e => 311d|
|786|312|True|o => 3o => 31e => 312o => 312|
|787|313|False|o => 3o => 31e => 313e|
|788|314|False|o => 3o => 31e => 314d|
|789|315|True|o => 3o => 31e => 315o => 315|
|790|316|False|o => 3o => 31e => 316e|
|791|317|False|o => 3o => 31e => 317d|
|792|318|True|o => 3o => 31e => 318o => 318|
|793|319|False|o => 3o => 31e => 319e|
|794|31A|False|o => 3o => 31e => 31Ad|
|795|31B|True|o => 3o => 31e => 31Bo => 31B|
|796|31C|False|o => 3o => 31e => 31Ce|
|797|31D|False|o => 3o => 31e => 31Dd|
|798|31E|True|o => 3o => 31e => 31Eo => 31E|
|799|31F|False|o => 3o => 31e => 31Fe|
|800|320|False|o => 3o => 32d => 320d|
|801|321|True|o => 3o => 32d => 321o => 321|
|802|322|False|o => 3o => 32d => 322e|
|803|323|False|o => 3o => 32d => 323d|
|804|324|True|o => 3o => 32d => 324o => 324|
|805|325|False|o => 3o => 32d => 325e|
|806|326|False|o => 3o => 32d => 326d|
|807|327|True|o => 3o => 32d => 327o => 327|
|808|328|False|o => 3o => 32d => 328e|
|809|329|False|o => 3o => 32d => 329d|
|810|32A|True|o => 3o => 32d => 32Ao => 32A|
|811|32B|False|o => 3o => 32d => 32Be|
|812|32C|False|o => 3o => 32d => 32Cd|
|813|32D|True|o => 3o => 32d => 32Do => 32D|
|814|32E|False|o => 3o => 32d => 32Ee|
|815|32F|False|o => 3o => 32d => 32Fd|
|816|330|True|o => 3o => 33o => 330o => 330|
|817|331|False|o => 3o => 33o => 331e|
|818|332|False|o => 3o => 33o => 332d|
|819|333|True|o => 3o => 33o => 333o => 333|
|820|334|False|o => 3o => 33o => 334e|
|821|335|False|o => 3o => 33o => 335d|
|822|336|True|o => 3o => 33o => 336o => 336|
|823|337|False|o => 3o => 33o => 337e|
|824|338|False|o => 3o => 33o => 338d|
|825|339|True|o => 3o => 33o => 339o => 339|
|826|33A|False|o => 3o => 33o => 33Ae|
|827|33B|False|o => 3o => 33o => 33Bd|
|828|33C|True|o => 3o => 33o => 33Co => 33C|
|829|33D|False|o => 3o => 33o => 33De|
|830|33E|False|o => 3o => 33o => 33Ed|
|831|33F|True|o => 3o => 33o => 33Fo => 33F|
|832|340|False|o => 3o => 34e => 340e|
|833|341|False|o => 3o => 34e => 341d|
|834|342|True|o => 3o => 34e => 342o => 342|
|835|343|False|o => 3o => 34e => 343e|
|836|344|False|o => 3o => 34e => 344d|
|837|345|True|o => 3o => 34e => 345o => 345|
|838|346|False|o => 3o => 34e => 346e|
|839|347|False|o => 3o => 34e => 347d|
|840|348|True|o => 3o => 34e => 348o => 348|
|841|349|False|o => 3o => 34e => 349e|
|842|34A|False|o => 3o => 34e => 34Ad|
|843|34B|True|o => 3o => 34e => 34Bo => 34B|
|844|34C|False|o => 3o => 34e => 34Ce|
|845|34D|False|o => 3o => 34e => 34Dd|
|846|34E|True|o => 3o => 34e => 34Eo => 34E|
|847|34F|False|o => 3o => 34e => 34Fe|
|848|350|False|o => 3o => 35d => 350d|
|849|351|True|o => 3o => 35d => 351o => 351|
|850|352|False|o => 3o => 35d => 352e|
|851|353|False|o => 3o => 35d => 353d|
|852|354|True|o => 3o => 35d => 354o => 354|
|853|355|False|o => 3o => 35d => 355e|
|854|356|False|o => 3o => 35d => 356d|
|855|357|True|o => 3o => 35d => 357o => 357|
|856|358|False|o => 3o => 35d => 358e|
|857|359|False|o => 3o => 35d => 359d|
|858|35A|True|o => 3o => 35d => 35Ao => 35A|
|859|35B|False|o => 3o => 35d => 35Be|
|860|35C|False|o => 3o => 35d => 35Cd|
|861|35D|True|o => 3o => 35d => 35Do => 35D|
|862|35E|False|o => 3o => 35d => 35Ee|
|863|35F|False|o => 3o => 35d => 35Fd|
|864|360|True|o => 3o => 36o => 360o => 360|
|865|361|False|o => 3o => 36o => 361e|
|866|362|False|o => 3o => 36o => 362d|
|867|363|True|o => 3o => 36o => 363o => 363|
|868|364|False|o => 3o => 36o => 364e|
|869|365|False|o => 3o => 36o => 365d|
|870|366|True|o => 3o => 36o => 366o => 366|
|871|367|False|o => 3o => 36o => 367e|
|872|368|False|o => 3o => 36o => 368d|
|873|369|True|o => 3o => 36o => 369o => 369|
|874|36A|False|o => 3o => 36o => 36Ae|
|875|36B|False|o => 3o => 36o => 36Bd|
|876|36C|True|o => 3o => 36o => 36Co => 36C|
|877|36D|False|o => 3o => 36o => 36De|
|878|36E|False|o => 3o => 36o => 36Ed|
|879|36F|True|o => 3o => 36o => 36Fo => 36F|
|880|370|False|o => 3o => 37e => 370e|
|881|371|False|o => 3o => 37e => 371d|
|882|372|True|o => 3o => 37e => 372o => 372|
|883|373|False|o => 3o => 37e => 373e|
|884|374|False|o => 3o => 37e => 374d|
|885|375|True|o => 3o => 37e => 375o => 375|
|886|376|False|o => 3o => 37e => 376e|
|887|377|False|o => 3o => 37e => 377d|
|888|378|True|o => 3o => 37e => 378o => 378|
|889|379|False|o => 3o => 37e => 379e|
|890|37A|False|o => 3o => 37e => 37Ad|
|891|37B|True|o => 3o => 37e => 37Bo => 37B|
|892|37C|False|o => 3o => 37e => 37Ce|
|893|37D|False|o => 3o => 37e => 37Dd|
|894|37E|True|o => 3o => 37e => 37Eo => 37E|
|895|37F|False|o => 3o => 37e => 37Fe|
|896|380|False|o => 3o => 38d => 380d|
|897|381|True|o => 3o => 38d => 381o => 381|
|898|382|False|o => 3o => 38d => 382e|
|899|383|False|o => 3o => 38d => 383d|
|900|384|True|o => 3o => 38d => 384o => 384|
|901|385|False|o => 3o => 38d => 385e|
|902|386|False|o => 3o => 38d => 386d|
|903|387|True|o => 3o => 38d => 387o => 387|
|904|388|False|o => 3o => 38d => 388e|
|905|389|False|o => 3o => 38d => 389d|
|906|38A|True|o => 3o => 38d => 38Ao => 38A|
|907|38B|False|o => 3o => 38d => 38Be|
|908|38C|False|o => 3o => 38d => 38Cd|
|909|38D|True|o => 3o => 38d => 38Do => 38D|
|910|38E|False|o => 3o => 38d => 38Ee|
|911|38F|False|o => 3o => 38d => 38Fd|
|912|390|True|o => 3o => 39o => 390o => 390|
|913|391|False|o => 3o => 39o => 391e|
|914|392|False|o => 3o => 39o => 392d|
|915|393|True|o => 3o => 39o => 393o => 393|
|916|394|False|o => 3o => 39o => 394e|
|917|395|False|o => 3o => 39o => 395d|
|918|396|True|o => 3o => 39o => 396o => 396|
|919|397|False|o => 3o => 39o => 397e|
|920|398|False|o => 3o => 39o => 398d|
|921|399|True|o => 3o => 39o => 399o => 399|
|922|39A|False|o => 3o => 39o => 39Ae|
|923|39B|False|o => 3o => 39o => 39Bd|
|924|39C|True|o => 3o => 39o => 39Co => 39C|
|925|39D|False|o => 3o => 39o => 39De|
|926|39E|False|o => 3o => 39o => 39Ed|
|927|39F|True|o => 3o => 39o => 39Fo => 39F|
|928|3A0|False|o => 3o => 3Ae => 3A0e|
|929|3A1|False|o => 3o => 3Ae => 3A1d|
|930|3A2|True|o => 3o => 3Ae => 3A2o => 3A2|
|931|3A3|False|o => 3o => 3Ae => 3A3e|
|932|3A4|False|o => 3o => 3Ae => 3A4d|
|933|3A5|True|o => 3o => 3Ae => 3A5o => 3A5|
|934|3A6|False|o => 3o => 3Ae => 3A6e|
|935|3A7|False|o => 3o => 3Ae => 3A7d|
|936|3A8|True|o => 3o => 3Ae => 3A8o => 3A8|
|937|3A9|False|o => 3o => 3Ae => 3A9e|
|938|3AA|False|o => 3o => 3Ae => 3AAd|
|939|3AB|True|o => 3o => 3Ae => 3ABo => 3AB|
|940|3AC|False|o => 3o => 3Ae => 3ACe|
|941|3AD|False|o => 3o => 3Ae => 3ADd|
|942|3AE|True|o => 3o => 3Ae => 3AEo => 3AE|
|943|3AF|False|o => 3o => 3Ae => 3AFe|
|944|3B0|False|o => 3o => 3Bd => 3B0d|
|945|3B1|True|o => 3o => 3Bd => 3B1o => 3B1|
|946|3B2|False|o => 3o => 3Bd => 3B2e|
|947|3B3|False|o => 3o => 3Bd => 3B3d|
|948|3B4|True|o => 3o => 3Bd => 3B4o => 3B4|
|949|3B5|False|o => 3o => 3Bd => 3B5e|
|950|3B6|False|o => 3o => 3Bd => 3B6d|
|951|3B7|True|o => 3o => 3Bd => 3B7o => 3B7|
|952|3B8|False|o => 3o => 3Bd => 3B8e|
|953|3B9|False|o => 3o => 3Bd => 3B9d|
|954|3BA|True|o => 3o => 3Bd => 3BAo => 3BA|
|955|3BB|False|o => 3o => 3Bd => 3BBe|
|956|3BC|False|o => 3o => 3Bd => 3BCd|
|957|3BD|True|o => 3o => 3Bd => 3BDo => 3BD|
|958|3BE|False|o => 3o => 3Bd => 3BEe|
|959|3BF|False|o => 3o => 3Bd => 3BFd|
|960|3C0|True|o => 3o => 3Co => 3C0o => 3C0|
|961|3C1|False|o => 3o => 3Co => 3C1e|
|962|3C2|False|o => 3o => 3Co => 3C2d|
|963|3C3|True|o => 3o => 3Co => 3C3o => 3C3|
|964|3C4|False|o => 3o => 3Co => 3C4e|
|965|3C5|False|o => 3o => 3Co => 3C5d|
|966|3C6|True|o => 3o => 3Co => 3C6o => 3C6|
|967|3C7|False|o => 3o => 3Co => 3C7e|
|968|3C8|False|o => 3o => 3Co => 3C8d|
|969|3C9|True|o => 3o => 3Co => 3C9o => 3C9|
|970|3CA|False|o => 3o => 3Co => 3CAe|
|971|3CB|False|o => 3o => 3Co => 3CBd|
|972|3CC|True|o => 3o => 3Co => 3CCo => 3CC|
|973|3CD|False|o => 3o => 3Co => 3CDe|
|974|3CE|False|o => 3o => 3Co => 3CEd|
|975|3CF|True|o => 3o => 3Co => 3CFo => 3CF|
|976|3D0|False|o => 3o => 3De => 3D0e|
|977|3D1|False|o => 3o => 3De => 3D1d|
|978|3D2|True|o => 3o => 3De => 3D2o => 3D2|
|979|3D3|False|o => 3o => 3De => 3D3e|
|980|3D4|False|o => 3o => 3De => 3D4d|
|981|3D5|True|o => 3o => 3De => 3D5o => 3D5|
|982|3D6|False|o => 3o => 3De => 3D6e|
|983|3D7|False|o => 3o => 3De => 3D7d|
|984|3D8|True|o => 3o => 3De => 3D8o => 3D8|
|985|3D9|False|o => 3o => 3De => 3D9e|
|986|3DA|False|o => 3o => 3De => 3DAd|
|987|3DB|True|o => 3o => 3De => 3DBo => 3DB|
|988|3DC|False|o => 3o => 3De => 3DCe|
|989|3DD|False|o => 3o => 3De => 3DDd|
|990|3DE|True|o => 3o => 3De => 3DEo => 3DE|
|991|3DF|False|o => 3o => 3De => 3DFe|
|992|3E0|False|o => 3o => 3Ed => 3E0d|
|993|3E1|True|o => 3o => 3Ed => 3E1o => 3E1|
|994|3E2|False|o => 3o => 3Ed => 3E2e|
|995|3E3|False|o => 3o => 3Ed => 3E3d|
|996|3E4|True|o => 3o => 3Ed => 3E4o => 3E4|
|997|3E5|False|o => 3o => 3Ed => 3E5e|
|998|3E6|False|o => 3o => 3Ed => 3E6d|
|999|3E7|True|o => 3o => 3Ed => 3E7o => 3E7|
|1000|3E8|False|o => 3o => 3Ed => 3E8e|
