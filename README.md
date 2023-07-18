`npm init -y`

`npm install --save-dev --save-exact prettier`

`npm init stylelint`

Add necessary rules in **_.stylelintrc.json_** from [here](https://stylelint.io/user-guide/rules)

***

Below step is only needed if using **_scss_**

`npm install --save-dev stylelint stylelint-config-standard-scss`

Replace the default value of **extends** key in **_.stylelintrc.json_** with below code:

`{
  "extends": ["stylelint-config-standard-scss"]
}`

***

`npx husky-init -and npm install`

`npm install --save-dev lint-staged`


***


Inside **_package.json_**, add the below code after **devDependencies**

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

will match all **_scss_** files inside the src/scss directory

will match all **_html_** files inside the src/app directory

**Another example**

``` json
"src/**/*.{html,scss}" : "prettier --write"
```

***

Replace the default value inside **_.husky/pre-commit_**, with the below code:

`npx lint-staged`

***

Run Stylelint on all the **_scss_** files in your project with the below code:

`npx stylelint "**/*.scss"`

Problems in **_css_** files will be shown automatically in **Problems** tab in **VS Code**

***

**Notes:**

1. Linting for certain files can be excluded using **_.prettierignore.json_**

2. Its better to include **_.vscode folder, .stylelintrc.json, .prettierrc.json_** from this repo while using for other projects.
3. Installing **SonarLint** extension will give additional linting rules.
