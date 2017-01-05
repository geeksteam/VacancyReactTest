# ReactJS Junior developer Vacancy test#


![geeks](https://github.com/geeksteam/VacancyFrontendTest/raw/master/logo-git.png)
<img src="https://upload.wikimedia.org/wikipedia/commons/4/42/Love_Heart_SVG.svg" width="80">
<img src="https://react-mdl.github.io/react-mdl/react.svg" width="250">


[![Join the community chat at https://gitter.im/geeksteam/Vacancies]
(https://badges.gitter.im/Join%20Chat.svg)]
(https://gitter.im/geeksteam/Vacancies)

We are looking for a junior `React+Redux` reactive :rocket: developer.

##There is a small challenge to test your HTML, CSS, React basic skills:##

Asume we have up and running backend server wich listen for `POST` requests in `JSON` format (default React post format), at `/login` URL and reply to our frontend in `JSON` format too.

We suggest to use `mockserver-grunt` or ther mock server for testing your app: https://www.npmjs.com/package/mockserver-grunt. But you can test as you wish.

### Create Login form
Create Login form view using Bootstrap:

![alt tag](https://raw.githubusercontent.com/geeksteam/VacancyFrontendTest/master/sketch/LoginPage.png)

Our backend server have several reponses to your React frontend:
```
- /login
 |- 1. "Login Denied"
 |- 2. "Success"
```

### 1. Login Denied.
We `POST` request to `/login` with incorrect (`foo,bar` in our case) `Username` and `Password` from our Login form.
Our backend server respond:
```
{"Auth":"Denied"}
```
So we are denied to enter the app. Make `red` Login field of the form:

![alt](https://raw.githubusercontent.com/geeksteam/VcFrontendTest/master/sketch/LoginFailed.png)


If you use mock server to emulate backend, there is mock for testing and developing:

```
mockServerClient("localhost", 8080).mockAnyResponse({
    "httpRequest": {
        "method": "POST",
        "path": "/login",
        "body": {
            "type": "JSON",
            "value": JSON.stringify({ Username: "foo", Password: "bar" }),
            "matchType": "STRICT"
        }
    },
    "httpResponse": {
        "statusCode": 200,
        "headers": [
            {
                "name": "Content-Type",
                "values": ["application/json; charset=utf-8"]
            },
            {
                "name": "Cache-Control",
                "values": ["public, max-age=86400"]
            }
        ],
        "body": JSON.stringify({ Auth: "Denied" }),
        "delay": {
            "timeUnit": "SECONDS",
            "value": 1
        }
    }
});
```

### 2. Auth succcess
We `POST` request to `/login` with correct (User:Password in our case) `Username` and `Password` from our Login form.
Out backend server respond:
```
{
	"Auth":"Logged",
	"Language":"EN"
}
```

We are succesfull logged to your Application, and you must show this to the user:

![alt](https://raw.githubusercontent.com/geeksteam/VcFrontendTest/master/sketch/Success.png)

If you use mock server to emulate backend, there is mock for testing and developing:
```
mockServerClient("localhost", 8080).mockAnyResponse({
    "httpRequest": {
        "method": "POST",
        "path": "/login",
        "body": {
            "type": "JSON",
            "value": JSON.stringify({ Username: "User", Password: "Password" }),
            "matchType": "STRICT"
        }
    },
    "httpResponse": {
        "statusCode": 200,
        "headers": [
            {
                "name": "Content-Type",
                "values": ["application/json; charset=utf-8"]
            },
            {
                "name": "Cache-Control",
                "values": ["public, max-age=86400"]
            }
        ],
        "body": JSON.stringify({ Auth: "Logged", Language: "EN" }),
        "delay": {
            "timeUnit": "SECONDS",
            "value": 1
        }
    }
});
```

### Project manifest (optional but can make your life easy):
- [x] Our best practices and code rules: https://github.com/geeksteam/CodeRules,
- [x] Bootstrap React from: https://github.com/facebookincubator/create-react-app,
- [x] Use `CamelCase` names,
- [x] Using Redux would be + in your karma,
- [x] Use feauture-based directory structure.


If any questions about task, join the chat at our Gitter [![https://gitter.im/geeksteam/Vacancies](https://badges.gitter.im/Join%20Chat.svg)](https://gitter.im/geeksteam/Vacancies) or mailto _vacancy @ geeks.team_.
