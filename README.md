```markdown
# 📇 TF12WEB – Sistema de Gerenciamento de Pessoas

Este projeto é uma **API RESTful** desenvolvida com **Node.js**, **Express**, **Sequelize** e **PostgreSQL**, containerizada com **Docker**. O sistema permite gerenciar pessoas e seus respectivos telefones, com suporte a paginação, ordenação e relacionamento 1:N.

---

## 🚀 Tecnologias Utilizadas

- Node.js 22+
- Express.js
- Sequelize ORM
- PostgreSQL
- Docker & Docker Compose
- Nginx (Proxy reverso)

---

## 📁 Estrutura do Projeto

```bash
TF12WEB/
├── app/
│   ├── Controllers/        # Controladores (lógica de negócio)
│   └── Models/             # Models definidos no Sequelize
├── config/                 # Configurações do Sequelize e relacionamentos
├── docker/
│   └── postgres/init/      # Scripts de criação e popularização do banco
├── public/                 # Arquivos públicos e estáticos
├── routes/                 # Rotas da aplicação
├── .env                    # Variáveis de ambiente
└── docker-compose.yml      # Orquestração dos containers
```

---

## ⚙️ Como Executar o Projeto

### 1. Clone o repositório

```bash
git clone https://github.com/Felipwz/TF12WEB.git
cd TF12WEB
```

### 2. Configure o ambiente

O arquivo `.env` já está configurado com as seguintes variáveis:

```env
PORT=8080
POSTGRES_HOST=postgres-tf12-container
POSTGRES_PORT=5432
POSTGRES_USER=postgres
POSTGRES_PASSWORD=postgres
POSTGRES_DB=postgres
```

### 3. Suba os containers

```bash
docker-compose up --build -d
```

Esse comando irá:

- Construir as imagens do Node.js e Nginx
- Iniciar os containers do PostgreSQL, Node.js e Nginx
- Executar os scripts de inicialização do banco
- Configurar o proxy reverso com Nginx

### 4. Verifique se está tudo funcionando

```bash
docker ps
```

Você deverá ver **três containers em execução**:

- `tf12web-node-web-tf12-container`
- `tf12web-nginx-tf12-container`
- `tf12web-postgres-tf12-container`

---

## 🧪 Testando a API

A aplicação estará disponível em:  
🔗 `http://localhost:8080`

### 🔎 Endpoint: Listar Pessoas

```http
GET /api/pessoas
```

#### Parâmetros de consulta (query):

- `limit`: Quantidade de registros por página (padrão: 10)
- `offset`: Quantidade de registros a pular (padrão: 0)
- `orderBy`: Campo e ordem da ordenação (ex: `created_at,desc`)

A resposta será um JSON com os dados das pessoas e seus telefones associados.

---

## 🗃️ Estrutura do Banco de Dados

### 📌 Tabela `pessoas`

| Campo      | Tipo        |
|------------|-------------|
| id         | SERIAL (PK) |
| nome       | TEXT        |
| created_at | TIMESTAMP   |
| updated_at | TIMESTAMP   |

### 📌 Tabela `telefones`

| Campo      | Tipo         |
|------------|--------------|
| id         | SERIAL (PK)  |
| numero     | TEXT         |
| id_pessoa  | INTEGER (FK) |
| created_at | TIMESTAMP    |
| updated_at | TIMESTAMP    |

Scripts de criação e popularização estão em:  
📁 `docker/postgres/init/`

---

## 🛠️ Dicas e Solução de Problemas

### 🔄 Reiniciar containers

```bash
docker-compose down
docker-compose up -d
```

### 🔍 Ver logs dos containers

```bash
docker logs tf12web-node-web-tf12-container-1
docker logs tf12web-postgres-tf12-container-1
docker logs tf12web-nginx-tf12-container-1
```

### ❌ Porta 8080 em uso?

```powershell
netstat -ano | findstr :8080
taskkill /F /PID [PID]
```

---

## 📬 Contato

Para dúvidas ou sugestões, entre em contato com o mantenedor do projeto:  
🔗 GitHub: [@Felipwz](https://github.com/Felipwz)
```
