# 📚 Biblioteca API
API desenvolvida com **NestJS** para gerenciar livros, usuários e empréstimos em uma biblioteca.

## **Índice**
- [Sobre o Projeto](#sobre-o-projeto)
- [Tecnologias Utilizadas](#tecnologias-utilizadas)
- [Como Executar o Projeto](#como-executar-o-projeto)
- [Endpoints](#endpoints)
- [Funcionalidades](#funcionalidades)
- [Melhorias Futuras](#melhorias-futuras-previstas)

---

## **Sobre o Projeto**
Esta API tem como objetivo gerenciar as operações básicas de uma biblioteca, permitindo:
- Cadastro e autenticação de usuários.
- Gerenciamento de livros (criação, consulta, edição e exclusão).
- Controle de empréstimos e devoluções de livros.
- Registro de histórico de empréstimos.

A aplicação foi projetada para ser prática e escalável, usando boas práticas de desenvolvimento com o **NestJS**.

---

## **Tecnologias Utilizadas**
- **Backend**: NestJS
- **Banco de Dados**: PostgreSQL ou MySQL
- **Autenticação**: JWT
- **Validação de Dados**: Class-validator
- **Gerenciamento de Dependências**: NPM/Yarn
- **Testes** (opcional): Jest e Supertest

---

## **Como Executar o Projeto**

### **1. Pré-requisitos**
Certifique-se de ter instalado:
- [Node.js](https://nodejs.org/) (versão LTS recomendada)
- [Yarn](https://yarnpkg.com/) ou NPM
- Banco de dados (PostgreSQL ou MySQL)
- [Postman](https://www.postman.com/) ou outra ferramenta para testar a API

### **2. Clonar o Repositório**
```bash
git clone https://github.com/seu-usuario/biblioteca-api.git
cd biblioteca-api
```

### **3. Instalar Dependências**
```bash
yarn install
# ou
npm install
```
### **4. Configurar Variáveis de Ambiente**
Crie um arquivo .env na raiz do projeto com as seguintes variáveis:
```dotenv
DATABASE_HOST=localhost
DATABASE_PORT=3306
DATABASE_USER=root
DATABASE_PASSWORD=senha
DATABASE_NAME=biblioteca
JWT_SECRET=sua_chave_secreta
PORT=3000
```
### **5. Executar as Migrações**
```bash
npx typeorm migration:run
```
### **6. Iniciar o Servidor**
```bash
yarn start:dev
# ou
npm run start:dev
```
A API estará disponível em http://localhost:3000.
___
## **Endpoints**
Abaixo estão os principais endpoints da API:

### **Usuários**
```http
POST /users: Cadastrar usuário.
POST /auth/login: Autenticar e gerar token JWT.
GET /users/me: Ver dados do próprio usuário (autenticado).
GET /users: Listar todos os usuários (somente admins).
```

### **Livros**
```http
POST /books: Cadastrar livro.
GET /books: Listar e filtrar livros.
PUT /books/:id: Atualizar dados de um livro.
DELETE /books/:id: Excluir um livro.
```

### **Empréstimos**
```http
POST /loans: Registrar empréstimo de livro.
POST /loans/:id/return: Registrar devolução de livro.
GET /loans: Listar histórico de empréstimos.
```
___
## **Funcionalidades**
### ✅ **Usuários**
- Cadastro, autenticação com JWT e gerenciamento de permissões (admin e usuário comum).
### ✅ **Livros**
- CRUD completo de livros com validação e filtros dinâmicos.
### ✅ **Empréstimos**
- Controle de empréstimos, devoluções e histórico.
___
## **Melhorias Futuras ***Previstas*****
- [ ] Implementar paginação nos endpoints de listagem
- [ ] Adicionar testes unitários e de integração.
- [ ] Criar notificações para devoluções atrasadas.
- [ ] Desenvolver uma interface frontend para interação com a API.
