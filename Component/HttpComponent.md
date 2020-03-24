# HttpComponent

Create HTTP service, only HTTP and HTTPS

### Use component

#### 1. Add component to application

server/config/app.go :
```go
// app config
func GetConfig() camBase.AppConfigInterface {
    config := cam.NewConfig()
    config.ComponentDict = map[string]camBase.ComponentConfigInterface{
        "http": httpConfig(),
    }
    return config
}

// http component config
func httpConfig() camBase.ComponentConfigInterface {
    config := cam.NewHttpConfig(8800)
    config.Register(&controllers.HelloController{})
    return config
}
```

### Config

#### Base

###### Props

| Key | Type | Note |
| ---- | ---- | ---- |
| Port | uint16 | http port |
| SessionName | string |  session name. use on generate/store session |
| SessionKey | string | session key |

###### Methods

AddRoute(route string, handler camBase.HttpRouteHandler)

| Param | Note |
| ---- | ---- |
| route | match route. Example: "user/get-list" |
| handler | handle route's function |
