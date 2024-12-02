
# **Documento de Requisitos Funcionais**

Este documento serve para gerenciar o que e como deverá ser realizado a criação da API.

- Projeto: Gerenciamento de Biblioteca
- Objetivo: Criar uma API para gerenciar livros e usuários de uma biblioteca, permitindo o cadastro, consulta, edição e remoção de informações.

## **1. Requisitos Funcionais**
### **1.1. Usuários**
- **RF-01**: A API deve permitir o cadastro de usuários com os seguintes campos obrigatório
    - Nome
    - Email(único)
    - Senha
- **RF-02**: A API deve permitir a autenticação de usuários utilizando JWT (JSON Web Token).
- **RF-03**: A API deve permitir que um usuário veja os seus próprios dados, exceto a senha.
- **RF-04**: A API deve permitir que um administrador liste todos os usuários cadastrados.
___
### **1.2. Livros**
- **RF-05**: A API deve permitir o cadastro de livros com os seguintes campos:
    - Título
    - Autor
    - ISBN (único)
    - Quantidade disponível
- **RF-06**: A API deve permitir a consulta de livros por diferentes critérios:
    - Por Título
    - Por Autor
    - Por ISBN
- **RF-07**: A API deve permitir a atualização dos dados de um livro.
- **RF-08**: A API deve permitir a exclusão de um livro do sistema.
### 1.3. Empréstimos
- **RF-09**: A API deve permitir que um usuário faça o empréstimo de um livro.
    - Só pode emprestar se houver exemplares disponíveis.
- **RF-10**: A API deve permitir que um usuário devolva um livro.
- **RF-11**: A API deve registrar o histórico de empréstimos, incluindo:
    - Usuário que fez o empréstimo
    - Livro emprestado
    - Data do empréstimo
    - Data de devolução
___
## **2. Regras de Negócio**
- **RN-01**: Um livro só pode ser excluído se não estiver emprestado.
- **RN-02**: Um usuário não pode pegar mais de 3 livros emprestados simultaneamente.
- **RN-03**: A senha do usuário deve ser armazenada de forma segura (hashing).
___
## **3. Endpoints**
Aqui estão alguns endpoints que atendem aos requisitos funcionais:
### **Usuários**
```http
POST /users: Cadastro de usuário
POST /auth/login: Login e geração de token JWT
GET /users/me: Consultar informações do próprio usuário
GET /users: Listar todos os usuários (apenas para admins)
```
### **Livros**
```http
POST /books: Cadastro de livros
GET /books: Listar e filtrar livros por título, autor ou ISBN
PUT /books/:id: Atualizar dados de um livro
DELETE /books/:id: Remover um livro
```
### Empréstimos
```http
POST /loans: Registrar empréstimo de livro
POST /loans/:id/return: Registrar devolução de livro
GET /loans: Listar histórico de empréstimos
```
___
