`npm init -y`

`npm install --save-dev --save-exact prettier`

`npm init stylelint`

Add necessary rules in **_.stylelintrc.json_** from [here](https://stylelint.io/user-guide/rules)

***

Below step is only needed if using **_scss_**

`npm install --save-dev stylelint stylelint-config-standard-scss`

Replace the default value of **_extends_** key in **_.stylelintrc.json_** with below code:

`{
  "extends": ["stylelint-config-standard-scss"]
}`

***

`npx husky-init -and npm install`

`npm install --save-dev lint-staged`


***


**Inside _package.json_, insert after _devDependencies_**

``` json
 "lint-staged": {
    "*.{css,scss}" : ["stylelint", "prettier --write"],
    "*.html": "prettier --write"
  }
```


**Folder example**

``` json
"lint-staged": {
  "src/scss/**/*.scss" : ["stylelint", "prettier --write"],
  "src/app/**/*.html" : "prettier --write"
}
```

_will match all scss files inside the src/scss directory_

_will match all html files inside the src/app directory_

**also**

``` json
"src/**/*.{html,scss}" : "prettier --write"
```

***

Replace the default value inside **_.husky/pre-commit_**, with the below code:

`npx lint-staged`

***

**Notes:**

1. Linting for certain files can be excluded using **_.prettierignore.json_**

2. **_Its better to include .vscode folder, stylelintrc.json, .prettierrc.json from this repo while using for other projects._**
