`yarn add react react-dom`

# Babel
Converte (transpilar) código do React para um código que browser entenda
# Webpack
Para cada tipo de arquivo (.js, .css, .png) eu vou converter o código de uma maneira diferente
## Loaders
babel-loader, css-loader, image-loader

---

`yarn add @babel/core @babel/preset-env @babel/preset-react webpack webpack-cli`
### @babel/preset-env
Converte um código de JS moderno para um mais antigo. Ele entende o ambiente em que a aplicação vai ser executada e faz essa adaptação.
### @babel/preset-react
Conversão do React para o JS

`yarn add @babel/cli` -> Interface de linha de comando
`yarn babel src/index.js --out-file public/bundle.js` -> Faz com que o arquivo transpilado seja 'jogado' para o public/bundle.js, o qual é a função da flag --out-file