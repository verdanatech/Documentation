
# Verdanadesk API

## SUMÁRIO

- Error Response
- CÓDIGO DE RESPOSTA DE ERRO PARA API
- Auth
- GET initSession
- Tickets
  - POST Criar um acompanhamento
  - POST Criar uma tarefa
  - POST Criar uma solução
  - GET Listar chamados


## Error Response

### CÓDIGO DE RESPOSTA DE ERRO PARA API

- 200 (OK)
- 201 (Created)
- 204 (No Content)
- 207 (Multi-Status)
- 400 (Bad Request) with a message indicating an error in input parameter.
- 401 (UNAUTHORIZED).
- 403 (Forbidden).

A URL para ser utilizada é `https://{{instancia}}.verdanadesk.com/plugins/applicationinterface`

## Auth

### GET initSession

`{{URL}}/auth`

Inicia a sessão para conexão 

**AUTHORIZATION**: Basic Auth

| Campo   | Valor          |
|---------|----------------|
| Username | `<username>`  |
| Password | `<password>`  |

Você deve passar estes 2 parâmetros na autenticação básica http. Consiste em uma string Base64 com login e senha separados por ":". Um cabeçalho de autorização válido é: `"Authorization: Basic base64({login}:{password})"`

**HEADERS**

| Campo       | Valor                       |
|-------------|-----------------------------|
| Authorization | Basic Z2xwaTonbHBp       |
| App-Token    | `<token>`                 |

## Tickets

### POST Criar um acompanhamento

`{{URL}}/tickets/{{ticket_id}}/followups`

**HEADERS**

| Campo       | Valor       |
|-------------|-------------|
| Bearer      | `<token>`   |
| App-Token   | `<token>`   |

**BODY** `x-www-form-urlencoded`

```json
{
 "content": "Acompanhamento adicionado via API"
}
```

| Atributo | Tipo | Descrição               |
|----------|------|-------------------------|
| Content  | text | Conteúdo do acompanhamento |

### POST Criar uma tarefa

`{{URL}}/tickets/{{ticket_id}}/tasks`

**HEADERS**

| Campo       | Valor       |
|-------------|-------------|
| Bearer      | `<token>`   |
| App-Token   | `<token>`   |

**BODY** `x-www-form-urlencoded`

```json
{
 "state": 1,
 "actiontime": 0,
 "content": "Corpo da tarefa"
}
```

| Atributo  | Tipo  | Descrição               |
|-----------|-------|-------------------------|
| Content   | text  | Conteúdo do tarefa       |
| Actiontime| int   | Tempo da tarefa          |
| States    | int   | Status da Tarefa: 1- A fazer, 2- Feito, 0 - Informação |

### POST Criar uma solução

`{{URL}}/tickets/{{ticket_id}}/solutions`

**HEADERS**

| Campo       | Valor       |
|-------------|-------------|
| Bearer      | `<token>`   |
| App-Token   | `<token>`   |

**BODY** `x-www-form-urlencoded`

```json
{
 "content": "Solução de chamado via API"
}
```

| Atributo | Tipo | Descrição               |
|----------|------|-------------------------|
| Content  | text | Conteúdo do solução      |

