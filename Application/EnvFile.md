# EnvFile

Write different variables in .evn file in different environments

## Create and use .env file in code

.env file must be in the same directory as the executable file.

It is recommended to create .env file in this directory: `./server/.env`

./server/.env:
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
