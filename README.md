# API simples com Laravel

## Requisitos
- PHP 8.4.3
- Laravel 12 (com Laravel Installer 5.13.0)
- Composer - Version 2.8.6
- node - 22.14.0 (com npm 10.9.2)
- Git - 2.45.0
- SQLite -  3.49.1

## Instalação

Instale todos os programas listados acima (isto inclui adicionar os seus respectivos diretórios na variável de sistema PATH para usuários de Windows10/11).

Clone o repositório utilizando:
`git clone https://github.com/felipeguimaraens/Laravel-RestAPI`

Accesse o diretório utilizando CMD e execute os seguintes comandos:
```
cd Laravel-RestAPI
composer install
npm install
```
Criar o arquivo .env utilizando o comando `cp .env.example .env`

Para rodar o servidor utilize o comando: `php artisan serve`

## Como utilizar

Com o servidor rodando conforme passo anterior já será possível fazer requisições utilizando um client HTTP. Recomendo utilizar o aplicativo [HTTPie](https://httpie.io/), porém este passo a passo funciona com outros aplicativos.

## Definição das APIs
### Registar o usuário

#### URL
**POST** `http://127.0.0.1:8000/api/register`

#### Headers
```
Accept : application/json
Content-Type : application/json
```
#### Body
```
{
"name": "INSIRA NOME",
"email": "INSIRA E-MAIL",
"password": "INSIRA SENHA",
"password_confirmation": "INSIRA SENHA",
"cpf": "INSIRA CPF",
"telefone": "INSIRA TELEFONE"
}
```
#### Exemplo de resposta
```
{
  "user": {
    "name": "Novo usuário",
    "email": "NovoUsuario256@emaila.ml2",
    "telefone": "1234567890",
    "cpf": "12345123456",
    "updated_at": "2025-03-06T23:08:52.000000Z",
    "created_at": "2025-03-06T23:08:52.000000Z",
    "id": 4
  },
  "token": "4|DFau0VTDWsAjR7nxFiyEbH3O6fBs8SKzmCrbprV3e1cefb4c"
}
```

OBS¹: Se o usuário foi criado(registrado) corretamente o sistema retornara **201 Created** e um **token** que deverá ser utilizado na autenticação nas demais requisições.

OBS²: O id retornado deverá ser utilizado na solicitação para editar o usuário.

### Login


#### URL
**POST** `http://localhost:8000/api/login`

#### Headers
```
Accept : application/json
Content-Type : application/json
```
#### Body
```
{
"email": "EMAIL",
"password": "SENHA"
}
```
#### Exemplo de resposta
Code **200 OK**
```
{
  "token": "4|DFau0VTDWsAjR7nxFiyEbH3O6fBs8SKzmCrbprV3e1cefb4c"
}
```

### Informação do usuário

#### URL
**GET** `http://localhost:8000/api/user`

#### Headers
```
Accept : application/json
Content-Type : application/json
Authorization : Bearer {token}
```
#### Body
```

```
#### Exemplo de resposta
```
{
  "id": 2,
  "name": "admin",
  "email": "myemail@emaila.ml2",
  "email_verified_at": null,
  "created_at": "2025-03-06T14:33:22.000000Z",
  "updated_at": "2025-03-06T22:36:00.000000Z",
  "telefone": "1234567890",
  "cpf": "12345123456"
}
```

### Editar usuário

#### URL
**GET** `http://localhost:8000/api/users/{id}`

#### Headers
```
Accept : application/json
Content-Type : application/json
Authorization : Bearer {token}
```
#### Body
```
{
"name": "INSIRA NOME",
"email": "INSIRA E-MAIL",
"password": "INSIRA SENHA",
"cpf": "INSIRA CPF",
"telefone": "INSIRA TELEFONE"
}
```
#### Exemplo de resposta
```
{
  "message": "Logout realizado com sucesso."
}
```

### Logout

#### URL
**POST** `http://localhost:8000/api/logout`

#### Headers
```
Accept : application/json
Content-Type : application/json
Authorization : Bearer {token}
```
#### Body
```

```
#### Exemplo de resposta
```
{
  "message": "Logout realizado com sucesso."
}
```

## Status do projeto

🟢 Implementado

🟡 Em Progresso

🔴 Não implementado


- Requisitos
  - ~~Autenticação (JWT)~~ 🟢 Utilizado Sanctum como padrão do boilerplate utilizado.
  - Criar Usuário 🟢
  - Editar Usuário 🟢
  - Deletar usuário (Logicamente) 🔴
  - Exibir dados do usuário 🟢
  - Atribuição de Permissão 🔴
  - Armazenar registros de endereço 🟡

- Dados do Usuário 🟢
  - Nome 🟢
  - E-mail 🟢
  - Telefone 🟢
  - CPF 🟢

- Dados de Endereço 🟡
  - Logradouro 🟡
  - Número 🟡
  - Bairro 🟡
  - Complemento 🟡
  - CEP 🟡