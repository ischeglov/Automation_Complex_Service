# Описание

Автоматизация тестирования комплексного сервиса, взаимодействующего с СУБД и API банка.

### Бизнес-часть

Приложение — это веб-сервис, который предлагает купить тур по определённой цене двумя способами:
1. Обычная оплата по дебетовой карте.
2. Уникальная технология: выдача кредита по данным банковской карты.

![](pic/service.png)

Приложение в собственной СУБД должно сохранять информацию о том, успешно ли был совершён платёж и каким способом. Данные карт сохранять не допускается.

### СУБД

* MySQL

Сервис обрабатывает только специальные номера карт, которые даны для тестирования:
* APPROVED карта — `1111 2222 3333 4444`;
* DECLINED карта — `5555 6666 7777 8888`.

Остальные данные карт могут быть любыми, но необходимо учесть, что год не должен быть прошлым, CVC состоит из трёх цифр и т. д.

## Задача

Автоматизировать позитивные и негативные сценарии покупки тура

**(выбрана форма покупки тура дебетовой картой)**

## Тестовая документация:

1. [План автоматизации тестирования](documentation/Plan.md)
2. [Отчёт по итогам тестирования](documentation/Report.md)
3. [Отчет по итогам автоматизации](documentation/Summary.md)

## Шаги для воспроизведения:

### Подготовительный этап

1. Установить и запустить IntelliJ IDEA;
2. Установить и запустить Docker Desktop;
3. Склонировать репозиторий с Github командой через терминал:
```
git clone git@github.com:ischeglov/Automation_Complex_Service.git
```
4. Открыть проект в IntelliJ IDEA.

### Запуск тестового приложения 

1. Запустить в контейнере базe данных — Mysql командой в терминале
```
docker-compose up
```
2. Запустить тестируемое приложение, находясь в корне проекта, выполнив в терминале команду:
```
java -jar ./artifacts/aqa-shop.jar
```
4.  Перейти на страницу, открыв в браузере страницу:
```
http://localhost:8080/
```

### Запуск тестов

5. В новой вкладке терминала запустить тесты:
 ```
./gradlew clean test
```
### Остановка, перезапуск тестов и приложения

Для остановки приложения в окне терминала ввести команду 
`Ctrl+С`

Для перезапуска приложения повторить необходимые действия из предыдущих разделов.

### Формирование отчёта

6. Для формирования отчета в новой вкладке терминала ввести команду
```
./gradlew allureServe
```



