`yarn init -y`
`yarn express`
`yarn add nodemon -D` -> Atualiza o serviço ao salvar os arquivos

## Tipo de parâmetros
**queryparams** -> Filtros e paginação
```
http://localhost:3333/projects?title=React&owner=Douglas&title=React&owner=Douglas
```
**routeparams** -> Identificar recursos (Atualizar/Deletar)
```
http://localhost:3333/projects/:id
```
**requestbody** -> Conteúdo na hora de criar ou editar um recurso (JSON)
```
{
	"title": "Aplicativo React Native",
	"owner": "Douglas Kurotaki"
}
```

**express funciona de forma linear**
`app.use(express.json());` -> Esse comando serve para que o express funcione com JSON

----

`yarn add uuidv4` -> Para criação de id's

----

## Middleware
**Interceptador de requisições que interrompe totalmente a requisição ou alterar dados da requisição**
As middleware são declaradas da seguinte forma: `function exampleMiddleware(request, response, next)`
Elas possuem os parãmetros como temos nas requisições (essas são middlewares também) e também o **next**
O **next** serve para que o procedimento seja prosseguido. Caso não haja ele dentro da função, o processo não vai continuar
No express usamos no ínico o `app.use(exampleMiddleware);` antes de chamarmos as requisição para que não precisemos inserir elas no callback das requisições como no seguinte caso:

```js
app.get('/projects', exampleMiddleware, (request, response) => {
  const { title } = request.query;
  const results = title ? projects.filter(project => project.title.includes(title)) : projects;
  return response.json(results);
})
```

Podemos também fazer validações com os middlewares. Como sabemos que toda requisição, caso tivermos esse middleware antes das chamadas da requisição, ela intercepta o procedimento, fazendo com que possamos modificar ou validar os dados. Dessa forma, ante de chamar o `next();`, podemos criar uma condição:

```js
function valideProjectId(request, response, next) {
  const { id } = request.params;
  if (!isUuid(id)) {
    return response.status(400).json({ error: 'Invalid project id' });
  }
  return next();
}
```

Da mesma forma que criamos uma chamada da função do middleware para executar em todas as requisições, podemos fazer uma validação para executar somente em rotas que tenham um parâmetro:

```js
app.use('/projects/:id', valideProjectId);
```
---

`yarn add cors`

```js
app.use(cors());
```
Isso faz com que possamos permitir que qualquer sistema consiga fazer requisição para essa aplicação