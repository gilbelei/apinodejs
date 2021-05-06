# API em NodeJs
Esta API é um exemplo de construção de APIs utilizando NodeJS
## Endpoints
### POST /auth
Responsável por realizar a autenticação do usuário para acesso a outras APIs.
#### Parametros
* **email** - E-mail do usuário cadastrado no sistema;
* **password** - Senha do usuário.

Exemplo de Parâmetro
```
{"email": "gilhhb@gmail.com","password":"nodejs<3"}

```

#### Resposta
##### Ok! 200
Caso essa resposta ocorra é retornado o token para autenticação do usuário.

Exemplo de Resposta
```
{
    "token": "exemPloDeTokenValidonR5cCI6IkpXVCJ9.eyJpZCI6MSwiZW1haWwiOiJnaWxoZW5yaXF1ZWhiQGdtYWlsLmNvbSIsImlhdCI6MTYyMDMwOTMzNiwiZXhwIjoxNjIwNDgyMTM2fQ.m40qE3g8ICFPHk7RwbLDi-QJ35DAZpWScOpeAjoVNAY"
}

```

#### O E-mail enviado é inválido 400
Caso essa resposta ocorra significa que houve falha na formatação de passagem dos parâmetros.

Exemplo de Resposta
```
{
    "err": "O E-mail enviado é inválido"
}

```

#### Credenciais inválidas! 401
Caso essa resposta ocorra significa que houve falha na autenticação.

Exemplo de Resposta
```
{
    "err": "Credenciais inválidas!"
}

```

#### O E-mail enviado é inválido 404
Caso essa resposta ocorra significa que o e-mail enviado no parâmetro não existe da base de dados.

Exemplo de Resposta
```
{
    "err": "O E-mail enviado não existe na base de dados!"
}

```


### GET /games
Retorna uma lista de games advindo de uma base de dados fake a partir de um json.
#### Parametros
* **token** - Token válido do usuário advindo da API auth passado no header pelo método de autenticação Bearer.

#### Resposta
##### Ok! 200
Caso essa resposta ocorra é retornado a listagem de todos os games.

Exemplo de Resposta
```
[
    {
        "id": 23,
        "title": "Call of duty MW",
        "year": 2019,
        "price": 60
    },
    {
        "id": 65,
        "title": "Sea of thieves",
        "year": 2018,
        "price": 40
    },
    {
        "id": 2,
        "title": "Minecraft",
        "year": 2012,
        "price": 20
    }
]

```

#### Falha na autenticação! 401
Caso essa resposta ocorra significa que houve falha na autenticação. Motivos: token inválido, token expirado.

Exemplo de Resposta
```
{
    "err": "Token inválido!"
}

```

### GET /game/:id
Retorna os detalhes de um game específico advindo de uma base de dados fake a partir de um json.

#### Parametros
* **token** - Token válido do usuário advindo da API auth passado no header pelo método de autenticação Bearer;
* **id** - Token válido do usuário advindo da API auth passado via GET.

#### Resposta
##### Ok! 200
Caso essa resposta ocorra é retornado os detalhe do game.

Exemplo de Resposta
```
{
    "id": 65,
    "title": "Sea of thieves",
    "year": 2018,
    "price": 40
}

```

#### Bad Request 400
Caso essa resposta ocorra significa que houve falha na formatação de passagem dos parâmetros.

Exemplo de Resposta
```
Bad Request

```

#### Not Found 404
Caso essa resposta ocorra significa que o id informado não existe.

Exemplo de Resposta
```
Not Found

```

### POST /game
Salva um game na lista json temporariamente.

#### Parametros
* **token** - Token válido do usuário advindo da API auth passado no header pelo método de autenticação Bearer;
* **title** - Trata-se do título do game;
* **year** - Trata-se do ano de lançamento do game;
* **price** - Trata-sedo valor do game.

#### Resposta
##### Ok! 200
Caso essa resposta ocorra significa que o game foi salvo com sucesso.

### DELETE /game/:id
Deleta um game específico no banco de dados.
#### Parametros
* **token** - Token válido do usuário advindo da API auth passado no header pelo método de autenticação Bearer;
* **id** - Token válido do usuário advindo da API auth passado via GET.

#### Resposta
##### Ok! 200
Caso essa resposta ocorra significa que o game foi removido com sucesso.

#### Bad Request 400
Caso essa resposta ocorra significa que houve falha na formatação de passagem dos parâmetros.

Exemplo de Resposta
```
Bad Request

```

#### Not Found 404
Caso essa resposta ocorra significa que o id informado não existe.

Exemplo de Resposta
```
Not Found

```

### PUT /game/:id
Atualiza as informações do game.
#### Parametros
* **token** - Token válido do usuário advindo da API auth passado no header pelo método de autenticação Bearer;
* **id** - Token válido do usuário advindo da API auth passado via GET;
* **title** - Trata-se do título do game;
* **year** - Trata-se do ano de lançamento do game;
* **price** - Trata-sedo valor do game.

#### Resposta
##### Ok! 200
Caso essa resposta ocorra significa que o game foi atualizado com sucesso.

#### Bad Request 400
Caso essa resposta ocorra significa que houve falha na formatação de passagem dos parâmetros.

Exemplo de Resposta
```
Bad Request

```

#### Not Found 404
Caso essa resposta ocorra significa que o id informado não existe.

Exemplo de Resposta
```
Not Found

```

