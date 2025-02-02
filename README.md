 # <a name="up" />Проект SQL.requests


## Содержание
- [Описание проекта](#описание-проекта)
- [Требования к проекту](#требования-к-проекту)
- [Задачи](#задачи)
- [Выполнение](#выполнение)
- [Инструменты](#инструменты)

## Описание проекта

<details>
<summary> Описание проекта </summary>

  **Проект: задания**
В проекте требуется проанализировать данные о фондах и инвестициях и написать запросы к базе. 

***

</details>

## Требования к проекту
<details>
<summary> Требования к проекту </summary> 

<img width="728" alt="Снимок экрана 2025-01-22 в 21 38 11" src="https://github.com/user-attachments/assets/e8e7c823-2474-4a63-ab19-58bd8bdef506" />

**acquisition**

Содержит информацию о покупках одних компаний другими.

Таблица включает такие поля:

первичный ключ id — идентификатор или уникальный номер покупки;

внешний ключ acquiring_company_id — ссылается на таблицу company — идентификатор компании-покупателя, то есть той, что покупает другую компанию;

внешний ключ acquired_company_id — ссылается на таблицу company — идентификатор компании, которую покупают;

term_code — способ оплаты сделки:

cash — наличными;

stock — акциями компании;

cash_and_stock — смешанный тип оплаты: наличные и акции.

price_amount — сумма покупки в долларах;

acquired_at — дата совершения сделки;

created_at — дата и время создания записи в таблице;

updated_at — дата и время обновления записи в таблице.

**company**

Содержит информацию о компаниях-стартапах.

первичный ключ id — идентификатор, или уникальный номер компании;

name — название компании;

category_code — категория деятельности компании, например:

news — специализируется на работе с новостями;

social — специализируется на социальной работе.

status — статус компании:

acquired — приобретена;

operating — действует;

ipo — вышла на IPO;

closed — перестала существовать.

founded_at — дата основания компании;

closed_at — дата закрытия компании, которую указывают в том случае, если компании больше не существует;

domain — домен сайта компании;

network_username — профиль фонда в корпоративной сети биржи;

country_code — код страны, например, USA для США, GBR для Великобритании;

investment_rounds — число раундов, в которых компания участвовала как инвестор;

funding_rounds — число раундов, в которых компания привлекала инвестиции;

funding_total — сумма привлечённых инвестиций в долларах;

milestones — количество важных этапов в истории компании;

created_at — дата и время создания записи в таблице;

updated_at — дата и время обновления записи в таблице.

**education**

Хранит информацию об уровне образования сотрудников компаний.

первичный ключ id — уникальный номер записи с информацией об образовании;

внешний ключ person_id — ссылается на таблицу people — идентификатор человека, информация о котором представлена в записи;

degree_type — учебная степень, например:

BA — Bachelor of Arts — бакалавр гуманитарных наук;

MS — Master of Science — магистр естественных наук.

instituition — учебное заведение, название университета;

graduated_at — дата завершения обучения, выпуска;

created_at — дата и время создания записи в таблице;

updated_at — дата и время обновления записи в таблице.

**fund**

Хранит информацию о венчурных фондах.

первичный ключ id — уникальный номер венчурного фонда;

name — название венчурного фонда;

founded_at — дата основания фонда;

domain — домен сайта фонда;

network_username — профиль фонда в корпоративной сети биржи;

country_code — код страны фонда;

investment_rounds — число инвестиционных раундов, в которых фонд принимал участие;

invested_companies — число компаний, в которые инвестировал фонд;

milestones — количество важных этапов в истории фонда;

created_at — дата и время создания записи в таблице;

updated_at — дата и время обновления записи в таблице.

**funding_round**

Содержит информацию о раундах инвестиций. 

первичный ключ id — уникальный номер инвестиционного раунда;

внешний ключ company_id — ссылается на таблицу company — уникальный номер компании, участвовавшей в инвестиционном раунде;

funded_at — дата проведения раунда;

funding_round_type — тип инвестиционного раунда, например:

venture — венчурный раунд;

angel — ангельский раунд;

series_a — раунд А.

raised_amount — сумма инвестиций, которую привлекла компания в этом раунде в долларах;

pre_money_valuation — предварительная, проведённая до инвестиций оценка стоимости компании в долларах;

participants — количество участников инвестиционного раунда;

is_first_round — является ли этот раунд первым для компании;

is_last_round — является ли этот раунд последним для компании;

created_at — дата и время создания записи в таблице;

updated_at — дата и время обновления записи в таблице.

**investment**

Содержит информацию об инвестициях венчурных фондов в компании-стартапы.

первичный ключ id — уникальный номер инвестиции;

внешний ключ funding_round_id — ссылается на таблицу funding_round — уникальный номер раунда инвестиции;

внешний ключ company_id — ссылается на таблицу company — уникальный номер компании-стартапа, в которую инвестируют;

внешний ключ fund_id — ссылается на таблицу fund — уникальный номер фонда, инвестирующего в компанию-стартап;

created_at — дата и время создания записи в таблице;

updated_at — дата и время обновления записи в таблице.

**people**

Содержит информацию о сотрудниках компаний-стартапов.

первичный ключ id — уникальный номер сотрудника;

first_name — имя сотрудника;

last_name — фамилия сотрудника;

внешний ключ company_id — ссылается на таблицу company — уникальный номер компании-стартапа;

network_username — профиль фонда в корпоративной сети биржи;

created_at — дата и время создания записи в таблице;

updated_at — дата и время обновления записи в таблице.

***

</details>


## Задачи

<details>
<summary> Задачи </summary

1. Посчитай, сколько компаний закрылось.
2. Отобрази количество привлечённых средств для новостных компаний США. Используй данные из таблицы company. Отсортируй таблицу по убыванию значений в поле funding_total.
3. Отобрази имя, фамилию и названия профиля в поле network_username, которые начинаются на 'Silver'.
4. Выведи на экран всю информацию о людях, у которых названия профиля фондов в поле network_username содержат подстроку 'money', а фамилия начинается на 'K'.
5. Для каждой страны отобрази общую сумму привлечённых инвестиций, которые получили компании, зарегистрированные в этой стране. Страну, в которой зарегистрирована компания, можно определить по коду страны. Отсортируй данные по убыванию суммы.
6. Отобрази имя и фамилию всех сотрудников стартапов. Добавь поле с названием учебного заведения, которое окончил сотрудник, если эта информация известна.
7. Найди общую сумму сделок по покупке одних компаний другими в долларах. Отбери сделки, которые осуществлялись только за наличные с 2011 по 2013 год включительно.
8. Выясни, в каких странах находятся фонды, которые чаще всего инвестируют в стартапы. 
Для каждой страны посчитай минимальное, максимальное и среднее число компаний, в которые инвестировали фонды этой страны, основанные с 2010 по 2012 год включительно. Исключи страны с фондами, у которых минимальное число компаний, получивших инвестиции, равно нулю. 
Выгрузи десять самых активных стран-инвесторов: отсортируй таблицу по среднему количеству компаний от большего к меньшему. Затем добавь сортировку по коду страны в лексикографическом порядке.

***

</details>

## Выполнение

<details>
<summary> Выполнение </summary

1.<img width="307" alt="Снимок экрана 2025-01-23 в 16 10 10" src="https://github.com/user-attachments/assets/3e8d1ce1-722d-465e-a79b-581f29c14597" />

2.<img width="575" alt="Снимок экрана 2025-01-23 в 16 10 17" src="https://github.com/user-attachments/assets/123d9f06-76a5-4cfe-b921-4ad2b949075d" />

3.<img width="330" alt="Снимок экрана 2025-01-23 в 16 10 28" src="https://github.com/user-attachments/assets/6c6e586f-f65e-4e88-a8be-710513065f65" />

4.<img width="682" alt="Снимок экрана 2025-01-23 в 16 10 36" src="https://github.com/user-attachments/assets/b734d621-8708-490d-8509-990f6a7e56c7" />

5.<img width="682" alt="Снимок экрана 2025-01-23 в 16 12 15" src="https://github.com/user-attachments/assets/7ac6a5fb-892b-430c-994f-070f19c3a132" />

6.<img width="383" alt="Снимок экрана 2025-01-23 в 16 12 23" src="https://github.com/user-attachments/assets/b4de57f8-f629-46ec-a040-4fa5fe2ee28b" />

7.<img width="465" alt="Снимок экрана 2025-01-23 в 16 12 30" src="https://github.com/user-attachments/assets/9e64ce5b-d9bc-4e53-856d-a394476b80ab" />

8.<img width="433" alt="Снимок экрана 2025-01-23 в 16 12 37" src="https://github.com/user-attachments/assets/7710c2ed-3e09-4fd0-8fca-98b3bad96695" />

***

</details>

## Инструменты
<p align="left"> 
<a href="https://www.postgresql.org/" target="_blank" rel="noreferrer"><img src="https://raw.githubusercontent.com/danielcranney/readme-generator/main/public/icons/skills/postgresql-colored.svg" width="36" height="36" alt="PostgreSQL" /></a>
</p> 
