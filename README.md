# MIPT: Dataton 2022. "Data Detectives"
### Финальный результат 
### Тема: Маркетплейсы
### Задача: Сбор и анализ данных из маркетплейсов для создания предсказательной модели на примере категории электроники (ноутбуки)
["Data Detectives" - информация о работе на Miro](https://miro.com/app/board/uXjVP4dIqYE=/?moveToWidget=3458764541734187484&cot=14)
### Члены команды:
- Козырева Алина
- Переверзев Петр
- Ли Диана
- Иванов Кирилл
- Остапенко Мария
- Виноградов Дмитрий


### Cтруктура репозитория: 
* main.py - реализует вызов необходимых функций
* browser.py - файл с функциями для поднятия браузера
* config.py - файл с необходимыми константами
* marketplaces/base.py - файл основной структуры класса для скраппинга, там находятся основные функции
* marketplaces/mvideo_base.py - содержит реализацию класса Mvideo для скраппинга данных с [М.Видео](https://www.mvideo.ru/product-list-page/f/tolko-v-nalichii=da?q=%D0%BD%D0%BE%D1%83%D1%82%D0%B1%D1%83%D0%BA&category=noutbuki-118 "Данные по ноутбукам")
* locators/mvideo.py - содержит локаторы для парсинга [М.Видео](https://www.mvideo.ru/product-list-page/f/tolko-v-nalichii=da?q=%D0%BD%D0%BE%D1%83%D1%82%D0%B1%D1%83%D0%BA&category=noutbuki-118 "Данные по ноутбукам")
_____
#### Как аналитика помогает селлеру начать продавать на маркетплейсах
___
##### ***Бизнес задача:***
**Маркетплейсы** — хороший вариант для начинающих предпринимателей. Можно стартовать на одной из популярных площадок, а потом выйти еще на несколько. 
Выход селлера на существующий маркетплейс – сложная задача, требующая предварительного анализа. 
Селлеры, которые изучают отчеты и знают, какие позиции продаются лучше, всегда на шаг впереди конкурентов. Они не тратят ресурсы на поставку нерентабельных товаров и экономят деньги. 
Анализ рынка нужен как новичкам, так и опытным продавцам:
* **Новичкам.** Когда предприниматель только выходит на любой маркетплейс, ему нужно заранее выбрать перспективную нишу, в которой реально продавать. С помощью анализа можно определить категорию, группы и даже отдельные товары, с которых стоит начать дело и заработать первые деньги. 
* **Опытным продавцам.** Невозможно постоянно продавать одно и то же и получать растущую прибыль. Нужно находиться в курсе всех изменений, заранее видеть падение или резкое повышение спроса, понимать, насколько продаваемая партия уместна и интересна аудитории на данный момент. Продавец должен точно знать, сколько товара ему еще потребуется, какие цены у конкурентов и как он назначает скидки.

##### ***Цель работы:***
Провести разведывательный анализ рынка ноутбуков на известных маркетплейсах для определения наиболее популярных товаров в зависимости от их технических характеристик и стоимости с целью подбора товаров для реализации.

#### ***Задачи работы:***
1. Сбор данных с маркетплейсов
2. Подготовка данных
3. Анализ и представление данных
4. Формирование рекомендаций
5. Дальнейшее развитие
____

#### ***Ход выполнения работы:***

##### 1.	Сбор данных с маркетплейсов:
* [М.Видео](https://ru.wikipedia.org/wiki/М.Видео "Источник: Википедия") - российская торговая сеть по продаже бытовой техники и электроники. Среди всех ритейлеров России занимает по объёмам продаж четвёртое место.
* [DNS](https://ru.wikipedia.org/wiki/DNS_(компания) "Источник: Википедия") - российская компания, владелец розничной сети, специализирующейся на продаже компьютерной, цифровой и бытовой техники. По итогам 2019 года стала 6-й крупнейшей ритейл-компанией в России. 
* [СберМегаМаркет](https://www.insales.ru/blogs/university/top-rating-marketpleysov "Источник: insales") – один из крупнейших мультикатегорийный маркетплейс России с широким ассортиментом товаров, входит в 4ку самых востребованных сервисов онлайн-продаж для интернет-магазинов. 
* [Wildberries](https://secrets.tinkoff.ru/biznes-s-nulya/issledovanie-marketpleysov/ "Источник: tinkoff") – международный маркетплейс одежды, обуви, электроники, детских товаров, товаров для дома и других товаров. 73% продавцов выбирают Wildberries в качестве первой площадки. 

Предварительно выделенные для сбора характеристики:
|№|	Характеристика|
--|---------------|
|1.	|	Цена с учетом скидки|
|2.	|	Цена без учета скидки|
|3.	|	Срок гарантии
|4.	|	Страна производитель
|5.	|	Производитель ноутбука
|6.	|	Модель ноутбука
|7.	|	Наличие предустановленной ОС
|8.	|	Наличие предустановленной ОС Windows
|9.	|	Количество ядер
|10.	|	Производитель процессора 
|11.	|	Модель процессора
|12.	|	Тип процессора
|13.	|	Тактовая частота процессора
|14.	|	Производитель видеопроцессора 
|15.	|	Модель графического контроллера
|16.	|	Объем видеопамяти
|17.	|	Размер экрана (диагональ)
|18.	|	Частота обновления экрана
|19.	|	Объем жесткого диска
|20.	|	Объем оперативной памяти
|21.	|	Тип оперативной памяти
|22.	|	Наличие HDMI
|23.	|	Материал корпуса 
|24.	|	Время работы от батареи
|25.	|	Вес

*Примечание – Выбор характеристик производился эмпирическим путем.*

**Инструменты:** 
Для автоматизации сбора данных с определенных сайтов, использовалась библиотека Selenium. С помощью него можно с легкостью имитировать поведение пользователей и обойти защиту веб-сайтов, которые мешают сбору данных.

Главными преимуществами выбранного способа:
* Легкость использования и кастомизации для каждого сайта
* Дает возможность обойти флуд-контроль на большинстве сайтов


**Выводы по этапу:**
* Сбор данных с применением API предпочтительнее, но не все маркетплейсы имеют бесплатные API, имеют ограничения по объему и частоте выгружаемых данных.
*	Сбор данных с применение web-scraper трудоемкий и требует много времени как для разработки (так как каждый сайт имеет уникальную структуру), так и для добычи данных.
*	Профильные сайты электроники (М.Видео, DNS) имеют более понятный для пользователя вид, а также более структурированный и удобный для web-scrapping.


##### 2. Подготовка данных
Данные из разных маркетплейсов объединены в единый датасеты, очищены от ошибочных (аномальных) данных, преобразованы к единому виду.
По предварительному анализу собранных датасетов с каждого маркетплейса были выявлены общие признаки, на основании этого был уточнен перечень характеристик:
|№|	Предварительная характеристика|	Результат анализа собранных датасетов|	Финальная характеристика|
--|--|--|--|
|0.|		-	|Добавить маркетплейс как источник данных|	Маркетплейс
|1.	|	Цена с учетом скидки|	-	|Цена с учетом скидки
|2.	|	Цена без учета скидки|	-	|Цена без учета скидки
|3.	|	Срок гарантии|	-|	Срок гарантии
|4.	|	Страна производитель	|Убрать, так как более 90 % товаров производятся в Китае, так же не во всех датасетах была эта характеристика	|-
|5.	|	Производитель ноутбука	|-	|Производитель ноутбука
|6.	|	Серия ноутбука	|-	|Серия ноутбука
|7.	|	Наличие предустановленной ОС|-	|Наличие предустановленной ОС
|8.	|	Наличие предустановленной ОС Windows|	Убрать, дублирует предыдущую характеристику	|-
|9.	|	Количество ядер	|-	|Количество ядер
|10.|		Производитель процессора |	-	|Производитель процессора 
|11.|		Модель процессора	|-	|Модель процессора
|12.|		Тип процессора	|-	|Тип процессора
|13.|		Тактовая частота процессора	|-	|Тактовая частота процессора
|14.|		Производитель видеопроцессора |	-	|Производитель видеопроцессора 
|15.|		Модель графического контроллера|	-	|Модель графического контроллера
|16.|		Объем видеопамяти	|Убрать, данные мало где заполнены|	-
|17.|		Размер экрана (диагональ)	|-	|Размер экрана (диагональ)
|18.|		Частота обновления экрана	|-	|Частота обновления экрана
|19.|		Объем жесткого диска	|-|	Объем жесткого диска
|20.|		Объем оперативной памяти	|-|	Объем оперативной памяти
|21.|		Тип оперативной памяти	|-|	Тип оперативной памяти
|22.|		Наличие HDMI	|-|	Наличие HDMI
|23.|		Материал корпуса |	-	|Материал корпуса 
|24.|		Время работы от батареи	|-|	Время работы от батареи
|25.|		Вес	|-|	Вес

**Финальный датасет имеет следующие данные**

|№|	Финальная характеристика|	Название в датасете	|Тип данных	|Примечание|
--|--|---|--|--|
|1.	|	Маркетплейс	|Marketplace |	String	|Откуда получили данные
|Производитель|
|2.	|	Производитель ноутбука	|Brand	|String	|
|3.	|	Серия ноутбука	|Series	|String	|
|Цена
|4.	|	Цена с учетом скидки	|PriceNow|	Int	|
|5.	|	Цена без учета скидки	|PriceOriginal	Int	|
|Дополнителные опции
|6.	|	Срок гарантии	|Guarantee_year	|int	|Гарантия в годах
|7.	|	Наличие предустановленной ОС	|OS	|String	|Название оси
|Процессор
|8.	|	Количество ядер|	CoresNumber	|Int|	
|.	|	Производитель процессора |	Processor|	String	|Производитель 
|10.	|	Модель процессора	|ProcessorType	|String	|Модель (core i7)
|11.	|	Тип процессора	|Processor Model|	String	|Серия (11260H)
|2.	|	Тактовая частота процессора|	ProcessorFrequency_GHz	|int	|Частота в ГГц
|Видеокарта
|13.	|	Производитель видеопроцессора |	GpuManufacter 	|String	|
|14.	|	Модель графического контроллера|	GpuController |	String	|
|Экран
|15.	|	Размер экрана (диагональ)	|ScreenSize_inch|	Int	|Размер в дюймах|
|16.	|	Частота обновления экрана	|ScreenFrequency_GHz	|Int|	
|Память
|17.	|	Объем жесткого диска	|SSDSize_GGb|	int	|Размер в ГГб|
|18.	|	Объем оперативной памяти|	RAM_GGb	|int	|Размер в ГГб|
|19.	|	Тип оперативной памяти	|RAM_type	|String	|
|Удобство эксплуатации
|20.	|	Наличие HDMI	|HDMI|	Boolean| 	Есть/нет|
|21.	|	Материал корпуса |	Material	|String 	
|22.	|	Время работы от батареи	|Battery_hour	|int	|Время работы в часах
|23.	|	Вес	Weight_kg	|int	|Вес в кг|

**Выводы по этапу:**
*	Предварительный подбор характеристик эмпирическим путем проведен корректно, практически все данные занесены в финальный датасет.
*	Непрофильные маркетплейсы дают не полную информацию о требуемых характеристиках, но было принято решение эти характеристики не убирать из финального датасета, так как эти данные могут быть полезны при анализе профильных маркетплейсов (М.Видео, DNS).

##### 3.Анализ и представление данных
Предлагается провести анализ технических харастеристик ноутбуков, представленных на разных маркетплейсах, для каждой ценовой категории:
* дешевые ноутбуки - от 0 до 50 000
* ноутбуки средней уеновой категории - от 50 000 до 90 000
* ноутюуки премиум класса - свыше 90 000

*График распределения стоимости ноутбуков для каждой категории*

**Определение значений популярных характеристик в каждой ценовой категории:**
3.1.	 Популярные производители ноутбуков: <br>
1.	n самых популярных (все маркетплейсы)
2.	n самых популярных (М.Видео)
3.	n самых популярных (DNS)
4.	n самых популярных (СберМегаМаркет)
5.	n самых популярных (Wildberries)

3.2.	Популярные процессоры и типы процессора:<br>
1.	n самых популярных (все маркетплейсы)
2.	n самых популярных (М.Видео)
3.	n самых популярных (DNS)
4.	n самых популярных (СберМегаМаркет)
5.	n самых популярных (Wildberries)

3.3.	 Популярные видеокарты:<br>
1.	n самых популярных (все маркетплейсы)
2.	n самых популярных (М.Видео)
3.	n самых популярных (DNS)
4.	n самых популярных (СберМегаМаркет)
5.	n самых популярных (Wildberries)

3.4.	Популярные значения размеров (и/или размеров и частоты) экрана:<br>
1.	n самых популярных (все маркетплейсы)
2.	n самых популярных (М.Видео)
3.	n самых популярных (DNS)
4.	n самых популярных (СберМегаМаркет)
5.	n самых популярных (Wildberries)

3.5.	Популярные значения объема жесткого диска:<br>
1.	n самых популярных (все маркетплейсы)
2.	n самых популярных (М.Видео)
3.	n самых популярных (DNS)
4.	n самых популярных (СберМегаМаркет)
5.	n самых популярных (Wildberries)

3.6.	Популярные значения размера и типа оперативной памяти:<br>
1.	n самых популярных (все маркетплейсы)
2.	n самых популярных (М.Видео)
3.	n самых популярных (DNS)
4.	n самых популярных (СберМегаМаркет)
5.	n самых популярных (Wildberries)

3.7.	Популярные значения дополнительных параметров - материал:<br>
1.	n самых популярных (все маркетплейсы)
2.	n самых популярных (М.Видео)
3.	n самых популярных (DNS)
4.	n самых популярных (СберМегаМаркет)
5.	n самых популярных (Wildberries)

3.8.	Популярные значения дополнительных параметров – работа от батареи:<br>
1.	n самых популярных (все маркетплейсы)
2.	n самых популярных (М.Видео)
3.	n самых популярных (DNS)
4.	n самых популярных (СберМегаМаркет)
5.	n самых популярных (Wildberries)

3.9.	Популярные значения дополнительных параметров – вес:<br>
6.	n самых популярных (все маркетплейсы)
7.	n самых популярных (М.Видео)
8.	n самых популярных (DNS)
9.	n самых популярных (СберМегаМаркет)
10.	n самых популярных (Wildberries)

По проведенному анализу были выбраны ноутбуки с самыми популярными параметрами в каждой категории: <br>
6.	все маркетплейсы - ноутбуки и стоимость(средняя)
7.	М.Видео- ноутбуки и стоимость(средняя)
8.	DNS- ноутбуки и стоимость(средняя)
9.	СберМегаМаркет- ноутбуки и стоимость(средняя)
10.	Wildberries- ноутбуки и стоимость(средняя)

**Выводы по этапу:**

##### 4. Дальнейшее развитие проекта
* Данный датасет может быть использован для предсказания стоимости товара по его техническим характеристикам
* 
