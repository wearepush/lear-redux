## Тестовое задание #4

Проверяем начальные навыки: авторизации, аунтификации, redux-form, cookies

#### Задача

Создать форму регистрации и авторизации. Вывести список новостей для авторизованного пользователя. Создать форму для создания новости. Создать форму для редактирования выбранной новости.

1. [jwt, header, token ](https://jwt.io/introduction/)
1. [теория jwt](https://www.youtube.com/watch?v=vQldMjSJ6-w)
2. [jwt](https://gist.github.com/zmts/802dc9c3510d79fd40f9dc38a12bccfc)
3. [jwt](https://proglib.io/p/json-tokens)
4. [jwt](https://codex.so/jwt)
5. [redux-form](https://redux-form.com/)

Приложение использует простой «бэк» расположенный на heroku. Свой бэкэнд делать не нужно.
Для проверки доступности бэкэнда, можете перейти по адресу:

https://wearepush-learn-redux-task4.herokuapp.com/


***

### Форма регистрации

Форма регистрации содержит в себе следующие поля: email, password, confirm_password, fname, lname.
По нажатию на «зарегестрироваться» (или после нажатия клавиши Enter) уходит POST запрос с введенными данными на бэкэнд.

В форме должна быть валидация на поля: email (обязательное поле, валидации на email адресс), password (обязательное поле, минимальная длина пароля 7, должен быть введен хотя бы один спец символ, должен быть введена хотябы одна цифра), fname (обязательное поле), lname (обязательное поле), confirm_password (потверждение правильного введенного пароля).

Пример валидного пароля *welcome1@*

Адрес и метод для запроса:

```
POST https://wearepush-learn-redux-task4.herokuapp.com/api/v1/auth/register

{
  email: "test@test.com",
  password: "test123",
  fname: "Test name",
  lname: "Test lname"
}
```

Необходимо также обрабатывать любые ошибки которые может вернуть сервер при неуспешной отправки данных. Например если такой пользователь уже существует сервер вернет ошибку. Ее необходимо вывести внутри формы, как правило ее выводят перед кнопкой регистрации. После успешной регистрации необходимо выдать сообщение что пользователь был успешно зарегестрирован и очистить форму регистрации.


### Форма логина

Форма логина содержит в себе следующие поля: email, password.
По нажатию на «зарегестрироваться» (или после нажатия клавиши Enter) уходит POST запрос с введенными данными на бэкэнд.


В форме должна быть валидация на поля: email (обязательное поле, валидации на email адресс), password (обязательное поле).

Адрес и метод для запроса:

```
POST https://wearepush-learn-redux-task4.herokuapp.com/api/v1/auth/login

{
  email: "test@test.com",
  password: "test123"
}
```

Необходимо также обрабатывать любые ошибки которые может вернуть сервер при неуспешной отправки данных. Например если авторизация была неудачной. Ее необходимо вывести внутри формы, как правило ее выводят перед кнопкой регистрации. После упешного логина пользователя нужно перебросить на страницу списка новостей текущего пользователя `/news/{userId}`.

В ответе успешной авторизации возвращается токен и
 информация пользователя

```
{
    "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc0FjdGl2ZSI6dHJ1ZSwiX2lkIjoiNWRmN2M4YTcxNThhMzYwMDE3ZDY5MjgxIiwiZW1haWwiOiJ0ZXN0QHRlc3QuY29tIiwiZmlyc3ROYW1lIjoiSXVyaWkiLCJsYXN0TmFtZSI6IkJ1bmRpa292IiwiY3JlYXRlZEF0IjoiMjAxOS0xMi0xNlQxODoxMDo0Ny43NzZaIiwiaWF0IjoxNTc3MjAzODk3LCJleHAiOjE1NzcyMDUzMzd9.GpW2uNosuelmMhobf-U9pWd4jaMXN0_4W51bUKTksRQ",
    "user": {
        "isActive": true,
        "_id": "5df7c8a7158a360017d69281",
        "email": "test@test.com",
        "firstName": "Iurii",
        "lastName": "Bundikov",
        "createdAt": "2019-12-16T18:10:47.776Z"
    }
}
```

Перейдите по ссылки https://jwt.io/ и вставьте в поле декода token. Посмотрите на результат.

Сохраните токен в cookies с ключем *token*. Установить expire date из дэкодированого token exp значения ключа.

Сохраните ответ user в редьюсер. Сделайте проверку авторизированого пользователя по наличию cookies token.
