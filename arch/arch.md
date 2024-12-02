# **Passo a passo da aplicação**
Este documento vai auxiliar a criação da API com a indicação do passo a passo.  
<br>
***Recomenda-se utilizar o método TDD para a criação do projeto***  

## **1. Repositório**
- [ ] Criar um repositório no Github para armazenar o projeto.
- [ ] Criar uma pasta local para o projeto.
- [ ] Realizar o clone do repositório na pasta criada.

## **2. Projeto**
- [ ] Escolher qual tecnologia será utilizada (ex.: Node.js, Python, Java, etc.).
- [ ] Criar os arquivos base de uma API REST.

---

### **2.1 Definindo os arquivos**
Organize os diretórios e crie os arquivos conforme a estrutura base para a API:
- [ ] Diretório principal para os arquivos do projeto.
  - [ ] `modules/` ou `features/` - Divida os módulos principais, como `users`, `books`, e `loans`.
  - [ ] `shared/` - Para helpers, middlewares ou componentes reutilizáveis.
  - [ ] `tests/` - Para testes unitários e de integração.
- [ ] Crie o arquivo de configuração principal para inicializar o servidor (ex.: `server.js` ou `app.js`).

---

### **2.2 Configurando o Banco de Dados**
- [ ] Escolher o banco de dados (ex.: PostgreSQL, MySQL, MongoDB).
- [ ] Configurar a conexão com o banco de dados:
  - [ ] Instalar as dependências necessárias para a comunicação com o banco.
  - [ ] Criar um arquivo de configuração ou utilizar variáveis de ambiente para armazenar as credenciais de conexão.

---

## **3. Testes Unitários**
A abordagem TDD recomenda começar pelos testes antes de implementar o código funcional.

### **3.1 Serviço de Usuário**
- [ ] Criar o teste unitário para o serviço de usuário:
  - [ ] Testar a criação de um novo usuário.
  - [ ] Validar a autenticação (se aplicável).
  - [ ] Garantir que usuários duplicados não sejam permitidos.
- Exemplo de teste inicial:
  ```javascript
  describe('UserService', () => {
    let userService;

    beforeEach(() => {
      userService = new UserService();
    });

    it('deve criar um novo usuário', async () => {
      const user = await userService.create({
        name: 'João Silva',
        email: 'joao@example.com',
        password: 'senha123',
      });
      expect(user).toHaveProperty('id');
      expect(user.email).toBe('joao@example.com');
    });
  });
  ```
___
### **3.2 Serviço de Recursos (Ex.: Livros)**
- [ ] Testar as operações CRUD:
    - [ ] Criação de um recurso.
    - [ ] Atualização de informações.
    - [ ] Exclusão.
    - [ ] Listagem com filtros dinâmicos.
___
### **3.3 Serviço de Relacionamentos (Ex.: Empréstimos)**
- [ ] Criar testes para o fluxo que envolve múltiplas entidades:
    - [ ] Registrar a associação entre recursos (ex.: empréstimo de livros).
    - [ ] Garantir integridade no processo (ex.: impedir que o mesmo recurso seja utilizado simultaneamente).
    - [ ] Registrar finalizações ou atualizações do estado do relacionamento.
___
## **4. Implementação**
Com base nos testes escritos, implemente as funcionalidades no código seguindo os passos abaixo:
### **4.1 Módulo de Usuários**
- [ ] Criar a entidade User no modelo escolhido (ex.: classe, schema ou tabela).
- [ ] Criar um serviço para gerenciar a lógica de negócios:
    - [ ] create()
    - [ ] findOne()
    - [ ] update()
- [ ] Implementar um controlador ou rota para expor as funcionalidades da API:
    - [ ] Cadastro de usuários.
    - [ ] Consulta de usuários.
    - [ ] Atualização de informações.
___
## **4.2 Módulo de Recursos (Ex.: Livros)**
- [ ] Criar a entidade Book no modelo escolhido.
- [ ] Implementar os métodos do serviço:
    - [ ] createBook()
    - [ ] listBooks()
    - [ ] updateBook()
    - [ ] deleteBook()
- [ ] Expor as rotas no controlador ou middleware.
___
## **5. Documentação**
- [ ] Criar uma documentação para a API (ex.: usando Swagger, Postman ou Markdown).
- [ ] Incluir exemplos de requisições para cada rota.
- [ ] Descrever os parâmetros necessários e as respostas esperadas.
___
## **6. Testes de Integração**
- [ ] Testar toda a API em conjunto, verificando se os serviços funcionam de forma integrada.
- [ ] Validar os fluxos principais, como:
    - [ ] Cadastro e consulta de usuários.
    - [ ] Relacionamento entre entidades (ex.: empréstimo e devolução).
___
## **7. Finalização**
- [ ] Validar a cobertura dos testes.
- [ ] Subir o código para o repositório.
- [ ] Realizar o deploy da aplicação em um ambiente de produção ou sandbox