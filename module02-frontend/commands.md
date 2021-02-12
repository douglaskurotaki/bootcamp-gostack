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
`yarn add babel-loader`

```js
// webpack.config.js
rules: [
      {
        teste: /\.js$/,
        exclude: /node_modules/,
        use: {
          loader: 'babel-loader'
        }
      }
    ]
```
A definição desse código, toda vez que eu tiver um arquivo com extensão js e não estiver dentro da pasta node_modeules, ele será convertido
`yarn webpack --mode development` -> Executa o webpack em modo desenvolvimento
`yarn add webpack-dev-server -D`
`yarn webpack serve --mode development` -> Executa o servidor do webpack

---

# JSX
HTML dentro do JS (JS XML)
componente sempre com inicial com letra maiúscula

*Para melhorar a produtividade, usamos o emmet do vscode, o qual faz o autocomplete das sintaxes*

```json
// setting.json
"emmet.syntaxProfiles": { "javascript": "jsx" },
"emmet.includeLanguages": { "javascript": "javascriptreact" }
``'

## Fragment
É quando queremos incluir mais de uma tag dentro de um componente, sem que precisemos colocar uma div

```
<>
  <Header />
  <Header />
</>
```

# Principais tópicos do react
- Componentes
- Propriedades
- Estados & Imutabilidade

## children

```js
// App.js
<Header title="Homepage">
  <ul>
    <li>Homepage</li>
    <li>Projects</li>
  </ul>
</Header>

// Header.js
export default function Header({ title, children }) {
  return (
    <header>
      <h1>{title}</h1>
      {children}
    </header>
  )
}
```

Com essa opção de children conseguimos passar para o componente pai, os filhos que no caso são as listas passadas dentro da tag `Header`

## html com array
Podemos fazer criações de tags html dessa forma:
```js
const projects = ['Desenvolvimento de app', 'Front-end web'];
<ul>
  {projects.map(project => <li key={project}>{project}</li>)}
</ul>
```

Devemos passar na tag pai no caso o `li` a propriedade `key`, que é o valor único que não se repetirá entre os dados. O mais ideal é que seja um id único

useState retorna array com 2 posições
1 - Variável com seu valor inicial
2 - Função para atualizarmos o valor

A **imutabilidade** é um conceito de que nunca podemos mudar/alterar uma informação, mas sim, sempre recriar.
Nesse caso, usarmos um push, estamos mudando a informação, e isso não é um boa prática
Toda vez que usamos a opção 2 do useState, ele faz com que a tela de renderize novamente