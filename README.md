# TaskTracker
___
Многопользовательский TODO лист.
## Использованные технологии
___
+ Java
+ Maven
+ Spring Boot, Spring Security, Spring Scheduler, Spring Mail, Spring Data JPA
+ JWT
+ PostgreSQL
+ Docker -  Dockerfile, Docker Compose
+ Apache Kafka
+ GitHub Actions
## Микросервисы
___
+ [REST API](https://github.com/yeodi/task-tracker-rest-api)
+ [Email Sender](https://github.com/yeodi/task-tracker-email-sender)
+ [Scheduler](https://github.com/yeodi/task-tracker-scheduler)
### REST API
Spring Boot приложение, реализующее REST API для работы с пользователями и задачами.
Авторизация происходит при помощи JWT.

Работа с пользователями:
+ Регистрация
+ Авторизация

Работа с задачами (доступно только авторизованым пользователям):
+ Создание
+ Чтение
+ Редактирование(Изменение заголовка и описания, пометка задачи, как сделанной)
+ Удаление
### Email Sender
Spring Boot приложение получающее сообщения от других микросервисов через Apache Kafka и отправляющее их на почту пользователя.
### Scheduler
Spring Boot приложение задача которого - раз в сутки итерировать всех пользователей, формировать для них отчёты об итогах дня, а также формировать email для отправки. Сформированные сообщения отправляются в Apache Kafka очередь.
## CI/CD
___
При помощи GitHub Actions была реализована автоматическая сборка docker образов и их публикация на [dockerhub](https://hub.docker.com/) при push или pull request в ветку main.
## Инструкция по запуску проекта
___
+ Установить Docker — https://docs.docker.com/get-docker/
+ Склонировать репозиторий task-tracker-stack
```
git clone https://github.com/yeodi/task-tracker-compose
+ ```
+ Заполнить SMTP-конфигурацию в .env. [Инструкция по созданию пароля](https://support.google.com/mail/answer/185833?hl=ru) для SMTP-сервиса gmail.
```
#Пример заполнения конфигурации:
SMTP_USERNAME=user@gmail.com
SMTP_PASSWORD=qwer tyui asdf ghjk
```
Запустить docker-compose файл
```
docker-compose up
```
+ Страница с документацией будет доступна по ссылке: http://localhost:8080/swagger-ui/index.html