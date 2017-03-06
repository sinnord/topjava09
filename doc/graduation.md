# Онлайн проекта <a href="https://github.com/JavaWebinar/topjava09">Topjava</a>

## Graduation project

Design and implement a JSON API using Hibernate/Spring/SpringMVC (or Spring-Boot) **without frontend**.

The task is:

Build a voting system for deciding where to have lunch.

 * 2 types of users: admin and regular users
 * Admin can input a restaurant and it's lunch menu of the day (2-5 items usually, just a dish name and price)
 * Menu changes each day (admins do the updates)
 * Users can vote on which restaurant they want to have lunch at
 * Only one vote counted per user
 * If user votes again the same day:
    - If it is before 11:00 we asume that he changed his mind.
    - If it is after 11:00 then it is too late, vote can't be changed

Each restaurant provides new menu each day.

As a result, provide a link to github repository. It should contain the code, README.md with API documentation and couple curl commands to test it.

-----------------------------
<a href="http://blog.mwaysolutions.com/2014/06/05/10-best-practices-for-better-restful-api/">10 Best Practices for Better RESTful API</a>

P.S.: Make sure everything works with latest version that is on github :)

P.P.S.: Asume that your API will be used by a frontend developer to build frontend on top of that.

-----------------------------

Из отзыва: 
> Организация работы с таблицами `restaurants` и `dishes` очень сильно похожа работе с таблицами `users` и `meals` в Topjava. И это достаточно удобно - идя по Topjava, параллельно делать этот выпускной. При этом довольно часто возникает ситуация, что вроде делаешь все полностью аналогично, а оно не работает. И приходится сильно попотеть, чтобы найти и исправить все ошибки в написанном самостоятельно. Но при этом многие вещи начинаешь понимать гораздо глубже. Я бы даже предположить не мог, со сколькими трудностями можно столкнуться, если не проделать все то же, что в Topjava, самому. Очень многого не видно, пока просто смотришь видео и патчами накатываешь себе готовый работающий код. Так что у кого есть время, очень советую не полениться, и проделать этот выпускной проект в вараинте, максимально приближенном к тому, что в Topjava. Совсем другое ощущение будет от проекта.

### ![error](https://cloud.githubusercontent.com/assets/13649199/13672935/ef09ec1e-e6e7-11e5-9f79-d1641c05cbe6.png) Рекомендации

- В проекте (и тестовом задании на работу) в отличии от нашего учебного topjava оставляйте только необходимый для работы приложения код, ничего лишнего:
  - НЕ надо делать разные профили базы и работы с ней. 
  - НЕ надо делать абстрактных контроллеров на всякий случай. 
  - НЕ надо делать делегирование классов репозиториев data-jpa, если там нет логики (например `CrudMealRepository` можно инжектить примо в `MealServiceImpl`). 
  - Из потребностей приложения (которую надо самим придумать) реализовывать только очевидные сценарии. Те.- НИЧЕГО ЛИШНЕГО, особенно если не готово полностью все ТЗ
- **читаем ТЗ ОЧЕНЬ внимательно, НЕ надо ничего своего туда домысливать и творчески изменять**
- НЕ надо все бездумно кэшировать
- если приложению в объекте требуется только его id, используйте reference (как мы при сохранении еды вставляем туда юзера)
- базу лучше взять без установки (H2 или HSQLDB)
- не смешивайте TO и Entity вместе. Лучше всего, если они будут независимыми друг от друга.
- по возможности сделать JUnit тесты
- уделяйте внимание обработке ошибок
- далаем REST API в соответствии с <a href="http://blog.mwaysolutions.com/2014/06/05/10-best-practices-for-better-restful-api/">концепцией REST</a>, с учетом принадлежности объектов
