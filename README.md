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
cd T
