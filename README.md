# AngularJS Junior developer vacancy test#

![geeks](https://github.com/geeksteam/VacancyFrontendTest/raw/master/logo-git.png)

We are looking for a junior `AngularJS` developer (version 1 not TypeScript).
There is a small challenge to test your HTML, CSS, AngularJS basic skills:

Asume we have up and running backend server wich listen for `POST` requests in `JSON` format (default AngularJS post format), and reply to our frontend in `JSON` format too.

Your tasks are:

- [x] Create authentication form using Bootstrap from sketch image attached below. Auth page must look __exactly__ as on a sketch image ! (Test your basic HTML, CSS);
- [x] Create AngularJS authentication logic depending on requests described below;
- [x] Use __Components__ in your project (latest Angularjs 1.5) and camelCase names.
- [x] Create a mock server for testing your angularjs application (You know, that you can't post request to another domain, because AJAX origin policy, so you need a simple mock server);
- [x] Your code must be good commented;
- [x] Test it;
- [x] Upload your code to your github repository and send the link to _vacancy @ geeks.team_;
- [x] Got a job of your dream B)

If any questions about task, mailto _vacancy @ geeks.team_.

### Sketches for auth web page: ###

| Basic login form:  | Login success: |
|--------------------|----------------|
| ![alt tag](https://raw.githubusercontent.com/geeksteam/VcFrontendTest/master/sketch/LoginPage.png) | ![alt tag](https://raw.githubusercontent.com/geeksteam/VcFrontendTest/master/sketch/Success.png) |

| Login failed: | HOTP code required: |
|---------------|---------------------|
![alt tag](https://raw.githubusercontent.com/geeksteam/VcFrontendTest/master/sketch/LoginFailed.png) | ![alt tag](https://raw.githubusercontent.com/geeksteam/VcFrontendTest/master/sketch/HOTPcode.png)


### Description of JSON request fields (in Russian) to backend:###
### Описание JSON полей запроса к backend серверу для авторизации: ###

URL для авторизации `/login`

* __Login__: 
		
	Используется имя пользователя.
* __Password__: 
		
	Пароль пользователя панели.
* __Hotp__: 
		
	Используется только если у пользователя под которым происходит авторизация включена "Двух уровневая авторизация" (Авторизация через Google Authenticator).
***

### JSON Ответы от backend сервера: ###

#### Успешная авторизация: ####
```json
{
 "Auth": "Logged",
 "Theme": "Simple",
 "Language": "EN"
}
```

#### Не верный логин или пароль: ####
```json
{
 "Auth": "Denied"
}
```

#### Слишком много попыток авторизации: ####
```json
{
 "Auth": "Banned",
 "Time": 300
}
```
_Клиент забанен на количество секунд, указанное в `Time`, так как выполнил слишком много попыток не успешной авторизации._

#### Требуется код двух уровневой авторизации: ####
```json
{
 "Auth": "HOTP required"
}
```
_В этом случае необходимо дополнить запрос на  авторизацию кодом, полученным из устройства к которому привязана двух уровневая авторизация:_

```json
{
 "Login": "root",
 "Password": "myVerySecretPassword",
 "Hotp":4523
}
```
### Ответы сервера на запрос о двухуроневой авторизации: ###

#### Не верный код двух уровневой авторизации: ####
```json
{
 "Auth": "HOTP wrong code"
}
```
_Код `Hotp` отправленный по запросу авторизации не совпадает с кодом, который ожидает получить сервер от устройства, к которому привязана двух уровневая авторизация._
