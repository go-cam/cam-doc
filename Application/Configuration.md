# Configuration

Application configuration. 

## 1. How to configure?

### 1.1 Single configuration
Example:
```go
package config

import (
    "github.com/go-cam/cam"
    "github.com/go-cam/cam/base/camBase"
)

// Add a configuration to the app
func appAddConfig() camBase.AppConfigInterface {
    config := cam.NewConfig()
    cam.App.AddConfig(config)
    return config
}
```

### 1.2 Multiple configurations
You can also add multiple configurations for the app. The later configuration will overwrite the previous one. 
[Configure override rules](#1.4 Configure override rules)

Example:

```go
package config

import (
    "github.com/go-cam/cam"
    "github.com/go-cam/cam/base/camBase"
)

// Add tow configurations to the app
func appAddConfig() camBase.AppConfigInterface {
    config1 := cam.NewConfig()
    config2 := cam.NewConfig()
    cam.App.AddConfig(config1)
    cam.App.AddConfig(config2)
    return config
}
```

### 1.3 Add component configuration

In the following example, add the DatabaseComponent

```go
package config

import (
    "github.com/go-cam/cam"
    "github.com/go-cam/cam/base/camBase"
)

// Add a configuration to the app
func appAddConfig() camBase.AppConfigInterface {
    config := cam.NewConfig()
    cam.App.AddConfig(config)
    config1.ComponentDict = map[string]camBase.ComponentConfigInterface{
        "db": databaseConfig(),
    }
    return config
}

// database component config
func databaseConfig() camBase.ComponentConfigInterface {
    config := cam.NewDatabaseConfig("mysql", "127.0.0.1", "3306", "go_cam", "root", "root1")
    return config
}
```

### 1.4 Configure override rules

In the following example, "DB" in config1 will be replaced by "DB" in config2. But "console" in config1 will remain

```go
package config

import (
    "github.com/go-cam/cam"
    "github.com/go-cam/cam/base/camBase"
)

// Add tow configurations to the app
func appAddConfig() camBase.AppConfigInterface {
    config1 := cam.NewConfig()
    config1.ComponentDict = map[string]camBase.ComponentConfigInterface{
        "db":      databaseConfig1(),
        "console": consoleConfig(),
    }

    config2 := cam.NewConfig()
    config1.ComponentDict = map[string]camBase.ComponentConfigInterface{
        "db":      databaseConfig2(),
    }

    cam.App.AddConfig(config1)
    cam.App.AddConfig(config2)
    return config
}

// database component config
func databaseConfig1() camBase.ComponentConfigInterface {
    config := cam.NewDatabaseConfig("mysql", "127.0.0.1", "3306", "go_cam", "root", "root1")
    return config
}
// database component config
func databaseConfig1() camBase.ComponentConfigInterface {
    config := cam.NewDatabaseConfig("mysql", "127.0.0.1", "3306", "go_cam", "root", "root2")
    return config
}

// console component config
func consoleConfig() camBase.ComponentConfigInterface {
    config := cam.NewConsoleConfig()
    config.DatabaseDir = "../common/database"
    config.XormTemplateDir = "../common/templates/xorm"
    return config
}
```
