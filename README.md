# talgat-demo-store

Добро пожаловать в мой магазин!

Магазин запускается через docker-compose.yml:

- git clone https://github.com/talgat-alimbayev/talgat-demo-store

- перейти в директорию (cd talgat-demo-store)

- docker-compose up

Магазин может:

- Регистровать новых пользователей с добавление в БД
- Авторизовывать пользователей
- Админ может добавлять новые продукты в БД через отдельную страницу
- Пользователи и админ могут добавлять продукты в корзину
- Корзину можно редактировать
- Можно осуществить заказ
- Заказ добавляется в БД
- После заказа будет отправлено подтверждающее письмо на имейл, указанный при регистрации
- Сервис отправки писем получает сообщения на отправке через брокер очереди RabbitMQ


При запуске магазина будет запущено 5 контейнеров:

- reactive backend на порту 8080
- non-reactive frontend на порту 8081
- сервис отправки писем на порте 8082
- Postgres БД (стандартный порт)
- RabbitMQ брокер сообщений (стандартные порты)

Админский аккаунт: (admin, admin). Добавить других админов невозможно.

После запуска проекта, перейдите на http://localhost:8081. После чего вы будете переадресованы на страницу логина, где можно зарегистрировать нового пользователя или авторизоваться как админ. После регистрации вы будете перенаправлены на домашнюю страницу

![image](https://user-images.githubusercontent.com/60476903/211169010-4a072a5c-80e4-42f5-a315-d95feb1a12f9.png)

Авторизовавшись, вы будете переадресованы на домашнюю страницу. Админу будет показана ссылка добавления продуктов. Для пользователей ссылка неактивная и не отображается.
Админский акаунт (admin, admin).

![image](https://user-images.githubusercontent.com/60476903/211169410-5c2f1c20-8e56-4c98-8c98-a078d1ea7a30.png)

Добавив продукты в корзину, можно перейти на кассу. На кассе подтягиваются данные из БД о авторизованном пользователе и поля заполняются автоматически

![image](https://user-images.githubusercontent.com/60476903/211169834-745a60a8-2bfa-4c04-a4c9-53ad91aee2fc.png)

Нажав кнопку Submit order, заказ будет записан в БД и на указанную почту придет письмо с подтверждением.

![image](https://user-images.githubusercontent.com/60476903/211169905-7e9a7ca7-11b0-4bc8-b4f1-64a4f4f7df97.png)

