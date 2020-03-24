# Cam v0.3.0

### Template directory: 
    The document is explained based on this directory
 
```text
.
|-- common                  // common module directory
  |-- config                
    |-- app.go              // common module config
  |-- templates
    |-- xorm                // xorm generate orm files's template
      |-- config
      |-- struct.go.tpl
|-- server                  // server module directory
  |-- config
    |-- app.go
    |-- bootstrap.go        // app bootstrap file
  |-- controllers           // controllers directory
    |-- HelloController.go
  |-- main.go               // entry of server module
|-- .gitignore
|-- cam.go                  // command line tools. you can build and execute it
|-- go.mod
|-- go.sum
|-- LICENSE
|-- README.md
``` 


### Content
- [Install](https://github.com/go-cam/cam-template)
- Document
  - [Application](Application/Index.md)
    - [Configuration](Application/Configuration.md)
    - [Env file](Application/EnvFile.md)
  - Component
    - [HttpComponent](Component/HttpComponent.md)
