# Foreign Exchange Currency
### Built using Vue.js
Try the application https://ovo-test.herokuapp.com/
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

### List of Components
- **App**: The root component of the application. Fetches API and houses the rest of the components.
- **BaseCurrency**: Where the base currency (USD) lies. It contains an input which can be modified, which will propagate to the rest of the application.
- **Converted**: The container for all of the individual rates being displayed. Is the parent to the ConvertedValue component.
- **ConvertedValue**: This is where all the information for a single currency is shown, as well as where the conversion is done. Deletion of a currency is also done from here.
- **AddCurrency**: This component contains a button where it will add a new currency to the shown list of currencies.

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
