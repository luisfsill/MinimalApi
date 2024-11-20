# Minimal API com Autenticação JWT e CRUD de Veículos e Administradores

Este projeto implementa uma API mínima utilizando .NET Core, com autenticação via JWT (JSON Web Tokens) e funcionalidades CRUD (Create, Read, Update, Delete) para o gerenciamento de veículos e administradores. Ele utiliza Swagger para documentação e permite o uso de autenticação baseada em tokens JWT para acessar as rotas protegidas.

## Tecnologias Utilizadas

- **.NET 6/7**: Framework para construção da API
- **JWT (JSON Web Token)**: Utilizado para autenticação
- **MySQL**: Banco de dados relacional
- **Swagger**: Documentação da API
- **CORS**: Configuração para permitir requisições de diferentes origens
- **Entity Framework Core**: ORM para interação com o banco de dados
- **ASP.NET Core Authentication & Authorization**: Controle de acesso à API

## Funcionalidades

### 1. **Autenticação e Autorização**
   - Endpoint `/administradores/login` para autenticar administradores utilizando credenciais (email e senha) e gerar um token JWT.
   - O token gerado deve ser incluído no cabeçalho da requisição como **Authorization: Bearer {token}**.
   - A autorização é baseada em papéis (roles) configurados, sendo que apenas administradores (perfil "Adm") podem acessar algumas rotas.

### 2. **CRUD de Administradores**
   - **Listar Administradores**: `/administradores` – Lista todos os administradores, com paginação.
   - **Buscar Administrador por ID**: `/administradores/{id}` – Retorna detalhes de um administrador.
   - **Criar Administrador**: `/administradores` – Cria um novo administrador, com validação dos dados de entrada.
   - **Atualizar Administrador**: `/administradores/{id}` – Permite a atualização de um administrador existente.
   - **Deletar Administrador**: `/administradores/{id}` – Deleta um administrador do banco de dados.

### 3. **CRUD de Veículos**
   - **Listar Veículos**: `/veiculos` – Lista todos os veículos, com paginação.
   - **Buscar Veículo por ID**: `/veiculos/{id}` – Retorna detalhes de um veículo.
   - **Criar Veículo**: `/veiculos` – Cria um novo veículo com validação dos dados de entrada.
   - **Atualizar Veículo**: `/veiculos/{id}` – Permite a atualização dos dados de um veículo.
   - **Deletar Veículo**: `/veiculos/{id}` – Deleta um veículo do banco de dados.

## Endpoints

### Administradores
- **POST** `/administradores/login`: Efetua login e retorna o token JWT.
- **GET** `/administradores`: Lista os administradores (requer autenticação).
- **GET** `/administradores/{id}`: Retorna detalhes do administrador especificado.
- **POST** `/administradores`: Cria um novo administrador (requer autenticação).
- **PUT** `/administradores/{id}`: Atualiza um administrador (requer autenticação).
- **DELETE** `/administradores/{id}`: Deleta um administrador (requer autenticação).

### Veículos
- **POST** `/veiculos`: Cria um novo veículo (requer autenticação e permissões de "Adm" ou "Editor").
- **GET** `/veiculos`: Lista todos os veículos.
- **GET** `/veiculos/{id}`: Retorna detalhes de um veículo especificado.
- **PUT** `/veiculos/{id}`: Atualiza os dados de um veículo (requer autenticação e permissões de "Adm").
- **DELETE** `/veiculos/{id}`: Deleta um veículo (requer autenticação e permissões de "Adm").
