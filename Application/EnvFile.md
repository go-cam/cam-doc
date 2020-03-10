# EnvFile

Write different variables in .evn file in different environments

## Create and use .env file in code

.env file must be in the same directory as the executable file.

.env
```text
DB_USERNAME = root
DB_PASSWORD = 123456
```

use in code:
```text
    username := cam.App.GetEnv("DB_USERNAME") // username = "root"
    password := cam.App.GetEnv("DB_PASSWORD") // password = "123456"
    fmt.println(username + " " + password) // output: "root 123456"
```
