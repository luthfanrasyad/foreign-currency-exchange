# Foreign Exchange Currency

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Run your tests
```
npm run test
```

### Lints and fixes files
```
npm run lint
```

## Run in Docker Container

### Build Docker image
```
docker build -t vuejs-cookbook/dockerize-vuejs-app .
```

### Run app in a Docker container
```
docker run -it -p 8080:8080 --rm --name dockerize-vuejs-app-1 vuejs-cookbook/dockerize-vuejs-app
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).

## Structure of Application

### Component Structure
                                 ----------------------- App -----------------------
                                 |                        |                         |
                                 |                        |                         |
                                 |                        |                         |  
                            BaseCurrency              Converted               AddCurrency
                                                          |
                                                          |
                                                          |
                                                    ConvertedValue

