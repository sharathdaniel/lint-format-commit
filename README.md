First install [Stylelint](https://marketplace.visualstudio.com/items?itemName=stylelint.vscode-stylelint), [Prettier](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode) extensions in VS Code.

Enter the following commands in terminal:

`npm init -y`

`npm install --save-dev --save-exact prettier`

`npm init stylelint`

Include **_.vscode folder, .stylelintrc.json, .prettierrc.json_** from this repo to your project.

Rules specified in **_.stylelintrc.json_** are from [here](https://stylelint.io/user-guide/rules).

***

Below step is only needed if using **_scss_**

`npm install --save-dev stylelint stylelint-config-standard-scss`

Replace the default value of **extends** key in **_.stylelintrc.json_** with below code:

`{
  "extends": ["stylelint-config-standard-scss"]
}`

***

`npm install --save-dev lint-staged`

Inside **_package.json_**, add the below code after **devDependencies**

``` json
"lint-staged": {
  "*.{css,scss}" : ["stylelint", "prettier --write"],
  "*.html": "prettier --write"
}
```


_Folder example

``` json
"lint-staged": {
  "src/scss/**/*.scss" : ["stylelint", "prettier --write"],
  "src/app/**/*.html" : "prettier --write"
}
```

Matches all **_scss_** files inside the src/scss directory.

Matches all **_html_** files inside the src/app directory.

_Another example_

``` json
"src/**/*.{html,scss}" : "prettier --write"
```

***

`npx husky-init -and npm install`

Replace the default value inside **_.husky/pre-commit_**, with the below code:

`npx lint-staged`

***

Finally restart VS Code. Now type some invalid css code, see if the warnings are showing up in **Problems** panel. Try to commit this file, the process will not complete as it contains invalid code.

***

**Notes:**

1. Linting for certain files can be excluded using **_.prettierignore.json_**
2. Installing **SonarLint** extension will give additional linting rules.
