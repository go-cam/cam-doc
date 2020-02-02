# Install by github

## 1 Download cam-template

    git clone --depth=1 https://github.com/go-cam/cam-template.git -b [version]

## 2 Init framework

### 2.1 Rename folder

    mv cam-template my-project

### 2.2 Download dependency Library

    cd my-project
    go mod tidy

### 2.3 Compile command line tools

    go build cam.go

### 2.4 Execute command

    ./cam init

## 3 Run Server

    cd server
    go build main.go
    ./main
