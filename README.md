### A guide to setup css/scss linting, html/css/scss formatting in your project using VS Code.
#### This setup also prevents invalid, poorly formatted code getting committed to repo.

***

First install [Stylelint](https://marketplace.visualstudio.com/items?itemName=stylelint.vscode-stylelint), [Prettier](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode) extensions in VS Code.

Initialize **npm** in your project if not already done by using the below command:

`npm init -y`

Enter the following commands in terminal:

`npm install --save-dev --save-exact prettier`

`npm init stylelint`

Include **_.vscode_** folder, **_.stylelintrc.json_**, **_.prettierrc.json_** from this repo to your project.

Read more up on **_.vscode_** folder [here](https://bobbyhadz.com/blog/what-is-vscode-folder).

Rules specified in **_.stylelintrc.json_** are from [here](https://stylelint.io/user-guide/rules).

Configuration specified in **_.prettierrc.json_** are from [here](https://prettier.io/docs/en/options.html).

***

Below step is only needed if using **_scss_**

`npm install --save-dev stylelint stylelint-config-standard-scss`

Replace the default value of **extends** key in **_.stylelintrc.json_** with the below code:

``` json
{
  "extends": ["stylelint-config-standard-scss"]
}
```

***

`npm install --save-dev lint-staged`

Inside **_package.json_**, add the below code after **devDependencies**.

``` json
"lint-staged": {
  "*.{css,scss}" : ["stylelint", "prettier --write"],
  "*.html": "prettier --write"
}
```


_Folder example_

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

```
npx lint-staged
```

***

Finally restart VS Code. Open your project and type some invalid code in the css/scss file, see if the warnings are showing up in the **Problems** panel. 

Try to commit this file, the process will not complete as it contains invalid code.

***

#### Notes:

1. Formatting for certain files can be excluded using **_.prettierignore_**
2. Linting for certain files can be excluded using **_.stylelintignore_**
3. Installing **SonarLint** extension will give additional linting rules.
