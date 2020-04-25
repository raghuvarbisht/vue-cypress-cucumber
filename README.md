# vue-cypress-cucumber


## Getting started

To get the frontend running locally:

- Clone this repo
- `yarn install` to install all req'd dependencies
- `yarn serve` to start the local server



To integrate cypress-cucumber-preprocessor in @vue/cli project need to follow below mention steps.


## Add the below lines in cypress.json 
```
"testFiles":"**/*.feature",
"integrationFolder": "tests/e2e/specs"

```

## Update the file at below location "test/e2e/plugin/index.js"
```

const cucumber = require( 'cypress-cucumber-preprocessor' ).default;

module.exports = (on, config) => {
  
  on( 'file:preprocessor', cucumber());
  
  return Object.assign({}, config, {
    fixturesFolder: 'tests/e2e/fixtures',
    integrationFolder: 'tests/e2e/specs',
    screenshotsFolder: 'tests/e2e/screenshots',
    videosFolder: 'tests/e2e/videos',
    supportFile: 'tests/e2e/support/index.js'
  })
}


```


## Add the bleow code in package.json
```
"cypress-cucumber-preprocessor": {
    "nonGlobalStepDefinitions": false,
    "stepDefinitions": "tests/e2e/specs"
}
```


### To run e2e test
```
yarn test:e2e
```

### Compiles and minifies for production
```
yarn build
```



### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).
