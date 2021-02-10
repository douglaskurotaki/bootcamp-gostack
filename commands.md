yarn init -y
yarn express
yarn add nodemon -D -> Atualiza o serviço ao salvar os arquivos

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