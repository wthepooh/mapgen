﻿Задача касается карт и маркеров в майнкрафте.
Нужно было сделать веб-страницу с такими возможностями:
- добавление карты
- просмотр маркеров выбранной карты
- редактирование маркеров
- добавление новых маркеров
- генерация команды для получения карты со всеми маркерами

Как хранятся данные:
Карты и маркеры хранятся в свойсве maps объекта localStorage в таком виде:
[
[mapName, [iconType,x,z],...,[iconType,x,z]],
...
[mapName, [iconType,x,z],...,[iconType,x,z]],
]

Для наглядности в папке testdata/ есть файл testdata.txt с тестовыми данными:
([["map1",[8,-174,180],[8,-1532,615],[8,-1325,1077],[8,-1754,1380],[8,-1163,1766],[0,-941,1700],[8,-318,1588],[8,-509,1267]],
["map2",[5,42,163],[8,325,103],[8,710,373],[0,1157,323]]]).
Загрузить можно так:
В левом верхнем углу страницы - Load from file -> выбираем testdata/testdata.txt

Каке элементы есть на странице:

1. Кнопкa 'Add map'
При нажатии на нее открывается форма добавления карты. В ней можно ввести имя карты, 
сохранить карту ('Save map') или отменить добавление ('Close form'). При сохранении карты ее имя добавляется в выпадающий 
список карт ('Maps list') и становится выбранным.

2. Список карт 'Maps list'.

3. Таблица с маркерами. Содержит 4 колонки:
-MarkerID
-IconType (тип иконки данного маркера)
-X (координата x данного маркера)
-Z (координата z данного маркера)
В таблице видимыми являются только строки с маркерами, принадлежащими выбранной карте (остальные маркеры скрыты).
Последняя строка - новый (несохраненный) маркер, для которого можно указать IconType, X, Z (в поля X и Z можно вводить только целые числа). MarkerID у него устанавливается автоматически.

4. Кнопка 'Generate command'. При нажатии на нее в текстовом поле ниже появляется команда для генерации карты.
Команда - это строка вида:
/give <User name> filled_map 1 <map name> {Decorations:[{id:<MarkerID>,rot:180d,type:<IconType>b,x:<X>d,z:<Z>d},...,{id:<MarkerID>,rot:180d,type:<IconType>b,x:<X>d,z:<Z>d}]}
Несохраненный маркер тоже участвует в команде.

5. Текстовое поле 'User name' (это имя используется в команде для генерации карты).

6. Кнопка 'Save marker'. При нажатии на нее несохраненный маркер (последняя строка) сохраняется, появляется новый несохраненный маркер.

7. При клике на любой сохраненный маркер появляется форма редактирования этого маркера (можно отредактировать iconType, X, Z).

Комментарии к элементам страницы, фукнциям, обработчикам событий - в коде.









