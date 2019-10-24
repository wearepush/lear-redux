## Тестовое задание #2

Проверяем начальные навыки: redux

#### Задача

Установить [redux](https://redux.js.org/introduction/getting-started) в приложении из Тестового задания #1.
Разобраться с базовыми компонентам redux.

1. [actions](https://redux.js.org/basics/actions)
2. [reducers](https://redux.js.org/basics/reducers)
3. [store](https://redux.js.org/basics/store)
4. [data-flow](https://redux.js.org/basics/data-flow)
5. [react-redux](https://redux.js.org/basics/usage-with-react)
6. [example of redux app](https://redux.js.org/introduction/examples#todos)


Форма входа (/login) принимает “фейковые” данные:
```
username: **admin**
password: 12345
```
Если введены другие данные, то показывается сообщения:
Имя пользователя или пароль введены не верно
Если введены корректные данные, то перебрасывать на страницу `/profile`
Информацию об авторизации пользователя можно хранить в localStorage, простым параметром true/false.

+ `/login` - страница ввода логина и пароля, если введены корректные данные, то перебрасывать на страницу `/profile`
+ `/news` - страница со списком новостей, вывести начальные данные из редьюсера новостей
+ `/profile` - страница с произвольным текстом, недоступная без авторизации, если пользователь кликает на страницу “профиля” и он не “авторизован” - перекидывать на страницу /login
