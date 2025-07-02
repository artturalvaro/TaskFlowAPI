
# TaskFlow API - Backend (GoLang)

Este é o backend da aplicação **TaskFlow**, implementado com **GoLang**, **PostgreSQL**, **JWT** e **bcrypt** para gerenciamento de autenticação de usuário, registro e segurança de senhas.

## Funcionalidades

- **Registro de usuário** com validação de senha e confirmação de senha.
- **Armazenamento seguro** de senhas com **bcrypt**.
- **Geração de tokens JWT** para autenticação de usuário.
- **Conexão com PostgreSQL** para armazenar dados de usuário.
- Rota para o **registro de usuário**.

## Tecnologias Utilizadas

- **GoLang**: Linguagem de programação para o backend.
- **Gin**: Framework web para GoLang.
- **PostgreSQL**: Banco de dados relacional para armazenar os dados de usuários.
- **JWT (JSON Web Token)**: Para autenticação de usuários.
- **bcrypt**: Para criptografia de senhas.

## Como Configurar o Backend

### 1. Instalar o Go
Certifique-se de que o **GoLang** esteja instalado na sua máquina. Se não, baixe a versão mais recente do [GoLang](https://golang.org/dl/).

### 2. Configurar o Banco de Dados PostgreSQL

1. Instale o **PostgreSQL** no seu sistema.
2. Crie um banco de dados para a aplicação:

   ```sql
   CREATE DATABASE taskflow;
   ```

3. Crie a tabela `users` com o seguinte comando SQL:

   ```sql
   CREATE TABLE users (
    id SERIAL PRIMARY KEY,
    email VARCHAR(255) UNIQUE NOT NULL,
    username VARCHAR(255) UNIQUE NOT NULL,
    password VARCHAR(255) NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
   );
   ```

### 3. Instalar as Dependências do Go

Execute o seguinte comando para instalar as dependências necessárias no seu backend (Go):

```bash
go get github.com/lib/pq
go get github.com/dgrijalva/jwt-go
go get github.com/gin-gonic/gin
go get golang.org/x/crypto/bcrypt
```

### 4. Configuração do Banco de Dados

No arquivo `main.go`, configure a conexão com o PostgreSQL ajustando as credenciais conforme seu ambiente. O código de conexão pode ser alterado da seguinte forma:

```go
db, err := sql.Open("postgres", "user=seu_usuario password=sua_senha dbname=taskflow sslmode=disable")
```

### 5. Rodar o Servidor

Para rodar o backend, use o comando:

```bash
go run main.go
```

O servidor vai rodar na porta **8000** por padrão. O backend estará disponível em `http://localhost:8000`.

### 6. Estrutura do Projeto

A estrutura do backend segue o formato abaixo:

```
/TaskFlowAPI
├── main.go         # Arquivo principal com a configuração do servidor e rotas
├── /models         # Modelos e estruturas de dados (por exemplo, User)
├── /handlers       # Funções que lidam com as rotas (registro, login, etc.)
├── /middleware     # Middleware para autenticação e verificação de JWT
├── /utils          # Funções auxiliares, como geração de JWT, criptografia de senha
└── /config         # Configurações gerais, como banco de dados e variáveis de ambiente
```

---

## Licença

Distribuído sob a licença MIT. Veja o arquivo [LICENSE](LICENSE) para mais informações.
