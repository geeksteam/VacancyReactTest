# AngularJS Junior developer vacancy test#

![geeks](https://github.com/geeksteam/VacancyFrontendTest/raw/master/logo-git.png)

We are looking for a junior `AngularJS` developer (version 1 not TypeScript).

##There is a small challenge to test your HTML, CSS, AngularJS basic skills:##

Asume we have up and running backend server wich listen for `POST` requests in `JSON` format (default AngularJS post format), at `/login` URL and reply to our frontend in `JSON` format too.

We suggest to use `mockserver-grunt` for testing your app: https://www.npmjs.com/package/mockserver-grunt.

### Create Login form
Create Login form view using Bootstrap.
![alt tag](https://raw.githubusercontent.com/geeksteam/VcFrontendTest/master/sketch/LoginPage.png)

Our backend server have several reponses to your AngularJS frontend:
```
- /login
 |- 1. "Login Denied"
 |- 2. "Success"
```

### 1. Login Denied.
We post request to `/login` with incorrect (`foo,bar` in our case) `Username` and `Password` from our Login form.
Our backend server respond:
```
{"Auth":"Denied"}
```
So we are denied to enter the app. Make `red` Login field of the form.

![alt](https://raw.githubusercontent.com/geeksteam/VcFrontendTest/master/sketch/LoginFailed.png)


If you use mock server, there is mock for testing and developing:

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
We post request to `/login` with correct (User:Password in our case) `Username` and `Password` from our Login form.
Out backend server respond:
```
{
	"Auth":"Logged",
	"Language":"EN"
}
```

We are succesfull logged to your Application, and you must show this to the user:
![alt](https://raw.githubusercontent.com/geeksteam/VcFrontendTest/master/sketch/Success.png)

If you are using mock-server:
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
- [x] Use Angular 1.5 and use components and views,
- [x] Use `camelCase` names,
- [x] Name your controller as `someController`, and services `someService`,
- [x] For http.Post requests and results create `Service`, don't do async requests in controllers,
- [x] Comment your code,
- [x] Use `Grunt`.


If any questions about task, mailto _vacancy @ geeks.team_.
