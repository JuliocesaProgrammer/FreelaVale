# Freela Vale

## 🚩 Sobre o Projeto

Freela Vale é uma plataforma de freelancer projetada para conectar talentos locais (freelancers) com oportunidades de trabalho (clientes) especificamente na região do Vale do São Francisco, Brasil. O objetivo é fortalecer a economia local, facilitando a contratação de profissionais da própria comunidade para diversas necessidades de serviços.

## ✨ Funcionalidades Principais (Planejadas e em Desenvolvimento)

* **Cadastro de Usuários:** Diferenciação entre perfis de "Cliente" e "Freelancer".
* **Autenticação Segura:** Login com e-mail e senha, com hashing de senhas (usando bcrypt.js).
* **Gerenciamento de Sessão:** Uso de JSON Web Tokens (JWT) para autenticação baseada em token.
* **Perfis de Freelancer:** Criação e gerenciamento de perfis detalhados, incluindo habilidades, portfólio, experiência e avaliações.
* **Publicação de Projetos:** Clientes podem postar detalhes dos projetos que necessitam.
* **Busca e Filtros:** Mecanismos para clientes encontrarem freelancers e para freelancers encontrarem projetos, com filtros por categoria, habilidade, etc.
* **Sistema de Propostas:** Freelancers podem enviar propostas para os projetos.
* **Mensagens Diretas:** Comunicação entre clientes e freelancers dentro da plataforma.
* **Sistema de Avaliação:** Clientes e freelancers podem se avaliar mutuamente após a conclusão de um projeto.

## 🛠️ Tecnologias Utilizadas

* **Frontend:**
    * HTML5
    * CSS3
    * JavaScript (Vanilla)
* **Backend:**
    * Node.js
    * Express.js
    * MySQL (com o driver `mysql2`)
    * `bcryptjs` para hashing de senhas
    * `jsonwebtoken` para autenticação baseada em tokens
    * `dotenv` para gerenciamento de variáveis de ambiente
    * `cors` para habilitar Cross-Origin Resource Sharing
* **Banco de Dados:**
    * MySQL

## 🚀 Configuração e Instalação

Siga os passos abaixo para configurar e rodar o projeto localmente.

### Pré-requisitos

* [Node.js](https://nodejs.org/) (versão LTS recomendada)
* npm (geralmente vem com o Node.js) ou Yarn
* [MySQL Server](https://dev.mysql.com/downloads/mysql/) instalado e rodando

### Backend

1.  **Clone o repositório (se ainda não o fez):**
    ```bash
    git clone [https://github.com/seu-usuario/freelavale.git](https://github.com/seu-usuario/freelavale.git)
    cd freelavale/freelavale-backend
    ```

2.  **Instale as dependências:**
    ```bash
    npm install
    ```

3.  **Configure as Variáveis de Ambiente:**
    * Crie um arquivo `.env` na raiz da pasta `freelavale-backend/`.
    * Copie o conteúdo do arquivo `.env.example` (se existir) ou adicione as seguintes variáveis:
        ```env
        DB_HOST=localhost
        DB_USER=seu_usuario_mysql
        DB_PASSWORD=sua_senha_mysql
        DB_NAME=freelavale_db
        PORT=3001
        JWT_SECRET=seu_segredo_super_secreto_para_jwt
        ```
    * Substitua pelos seus dados reais do MySQL e defina um `JWT_SECRET` forte.

4.  **Configure o Banco de Dados MySQL:**
    * Certifique-se de que seu servidor MySQL está rodando.
    * Crie o banco de dados `freelavale_db` (se ainda não existir).
    * Execute o script SQL abaixo para criar a tabela `usuarios` (você pode adicionar este script em um arquivo `schema.sql` no projeto):
        ```sql
        CREATE DATABASE IF NOT EXISTS freelavale_db;
        USE freelavale_db;

        CREATE TABLE IF NOT EXISTS usuarios (
            id INT AUTO_INCREMENT PRIMARY KEY,
            nome_completo VARCHAR(255) NOT NULL,
            email VARCHAR(255) NOT NULL UNIQUE,
            senha VARCHAR(255) NOT NULL,
            tipo_conta ENUM('cliente', 'freelancer') NOT NULL,
            data_cadastro TIMESTAMP DEFAULT CURRENT_TIMESTAMP
        );
        -- Adicione outras tabelas aqui (perfis, projetos, propostas, etc.) conforme são desenvolvidas.
        ```

5.  **Inicie o servidor backend:**
    ```bash
    npm start
    ```
    Ou, se configurou o nodemon para desenvolvimento:
    ```bash
    npm run dev
    ```
    O servidor backend estará rodando em `http://localhost:3001` (ou a porta definida no seu `.env`).

### Frontend

1.  Navegue até a pasta do frontend (se estiver separada, ex: `freelavale/freelavale-frontend` ou na raiz do projeto se os arquivos HTML estiverem lá).
    ```bash
    cd ../ # ou o caminho para a pasta do frontend
    ```
2.  Abra os arquivos `.html` (como `index.html`, `signup.html`, `login.html`) diretamente no seu navegador.
    * Para uma melhor experiência de desenvolvimento frontend, você pode usar extensões como "Live Server" no VS Code.

## 🌐 Endpoints da API (Exemplos Iniciais)

* `POST /api/auth/registrar`: Registra um novo usuário.
    * Corpo da requisição (JSON): `{ "nome_completo", "email", "senha", "tipo_conta" }`
* `POST /api/auth/login`: Autentica um usuário existente.
    * Corpo da requisição (JSON): `{ "email", "senha" }`

*(Mais endpoints serão adicionados conforme o desenvolvimento)*

## 📁 Estrutura do Projeto (Backend - Sugestão)
