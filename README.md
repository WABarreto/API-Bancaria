# API Bancária

API RESTful assíncrona desenvolvida com FastAPI para gerenciamento de operações bancárias, incluindo autenticação JWT, depósitos, saques e consulta de extrato.

---

# Tecnologias Utilizadas

* Python 3.12
* FastAPI
* SQLAlchemy
* Alembic
* PostgreSQL
* AsyncPG
* Pydantic
* JWT Authentication
* Uvicorn

---

# Estrutura do Projeto

```text
API-Bancaria/
├── alembic/
├── src/
│   ├── controllers/
│   │   ├── account.py
│   │   ├── auth.py
│   │   └── transactions.py
│   ├── models/
│   │   ├── account.py
│   │   └── transaction.py
│   ├── schemas/
│   │   ├── account.py
│   │   ├── auth.py
│   │   └── transaction.py
│   ├── services/
│   │   ├── account.py
│   │   └── transaction.py
│   ├── views/
│   │   ├── account.py
│   │   ├── auth.py
│   │   └── transaction.py
│   ├── config.py
│   ├── database.py
│   ├── exceptions.py
│   ├── main.py
│   └── security.py
├── alembic.ini
├── requirements.txt
└── README.md
```

---

# Funcionalidades

* Cadastro de contas bancárias
* Login com JWT
* Depósitos
* Saques
* Consulta de extrato
* Validação de saldo
* Documentação automática com Swagger
* Migrations com Alembic

---

# Regras de Negócio

* Não permite depósitos negativos
* Não permite saques negativos
* Não permite saques acima do saldo disponível
* Endpoints protegidos exigem autenticação JWT

---

# Configuração do Ambiente

## 1. Clone o repositório

```bash
git clone https://github.com/WABarreto/API-Bancaria
cd API-Bancaria
```

---

## 2. Crie o ambiente virtual

### Windows

```powershell
py -m venv venv
```

Ative o ambiente:

```powershell
venv\Scripts\activate
```

### Linux/macOS

```bash
python3 -m venv venv
source venv/bin/activate
```

---

## 3. Instale as dependências

```bash
pip install -r requirements.txt
```

---

# Banco de Dados

O projeto utiliza PostgreSQL.

Download:

[https://www.postgresql.org/download/](https://www.postgresql.org/download/)

---

# Criando o Banco

```sql
CREATE DATABASE api_bancaria;
```

---

# Configuração da Conexão

Configure a URL do banco em `config.py`.

Exemplo:

```python
DATABASE_URL = "postgresql+asyncpg://postgres:senha@localhost:5432/api_bancaria"
```

---

# Executando as Migrations

## Criar migration

```bash
alembic revision --autogenerate -m "init_db"
```

## Aplicar migrations

```bash
alembic upgrade head
```

---

# Executando a Aplicação

```bash
uvicorn src.main:app --reload
```

A API estará disponível em:

```text
http://127.0.0.1:8000
```

---

# Documentação da API

## Swagger

```text
http://127.0.0.1:8000/docs
```

## Redoc

```text
http://127.0.0.1:8000/redoc
```

---

# Endpoints Principais

## Autenticação

```http
POST /login
```

---

## Contas

```http
POST /accounts
GET /accounts/{id}
```

---

## Transações

```http
POST /transactions/deposit
POST /transactions/withdraw
GET /transactions/statement/{account_id}
```
