`npm init -y`

`npm install --save-dev --save-exact prettier`

`npm init stylelint`

`npx husky-init -and npm install`

`npm install --save-dev lint-staged`


***


**Inside _package.json_, insert after _devDependencies_**

> "lint-staged": {
  "\*.{css,scss}" : [
     "stylelint",
     "prettier --write"
  ],
  "\*.html": "prettier --write"
}


**Folder example**

> "lint-staged": {
  "src/scss/\*\*/\*.scss" : [
     "stylelint",
     "prettier --write"
  ],
  "src/app/\*\*/\*.html" : "prettier --write"
}

_will match all scss files inside the src/scss directory_

_will match all html files inside the src/app directory_

**OR**

> "src/**/*.{html,scss}" : "prettier --write"

_**.prettierignore**_ file is considered when running lint staged

***

**Inside _.husky/pre-commit_, add the below line**

`npx lint-staged`
