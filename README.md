# 📋 TarefasDB-API

## 📌 Sobre o Projeto

**TarefasDB-API** é um backend REST desenvolvido em **Node.js** que funciona como a camada de servidor de uma aplicação web completa de gerenciamento de tarefas. Este projeto se integra com um frontend para criar um sistema completo de **To-Do List**.

O backend é responsável por gerenciar todas as operações de dados, autenticação, validações e conexão com o banco de dados, enquanto o frontend consome as APIs fornecidas para exibir e interagir com as tarefas de forma amigável ao usuário.

---

## 🛠️ Tecnologias Utilizadas

| Tecnologia | Versão | Função |
|-----------|--------|--------|
| **Node.js** | - | Runtime JavaScript |
| **Express.js** | ^5.2.1 | Framework web para criar APIs REST |
| **MongoDB** | - | Banco de dados NoSQL |
| **Mongoose** | ^9.5.0 | ODM (Object Document Mapper) para MongoDB |

---

## 📂 Estrutura do Projeto

```
API/
├── index.js              # Arquivo principal - servidor Express
├── package.json          # Dependências do projeto
├── README.md            # Este arquivo
├── LICENSE              # Licença do projeto
├── models/
│   └── tarefa.js        # Schema MongoDB para tarefas
└── routes/
    └── routes.js        # Definição das rotas da API
```

---

## 🚀 Funcionalidades Principais

### ✅ Operações CRUD Completas

A API oferece os seguintes endpoints para gerenciar tarefas:

#### 📤 **POST** - Criar uma nova tarefa
```
POST /api/post
```
**Request Body:**
```json
{
  "descricao": "Minha tarefa",
  "statusRealizada": false
}
```
**Response:** Tarefa criada com ID gerado automaticamente

#### 📥 **GET** - Obter todas as tarefas
```
GET /api/getAll
```
**Response:** Array com todas as tarefas registradas

#### 🗑️ **DELETE** - Deletar uma tarefa
```
DELETE /api/delete/:id
```
**Parâmetro:** `id` - ID da tarefa a ser deletada

#### ✏️ **PATCH** - Atualizar uma tarefa
```
PATCH /api/update/:id
```
**Parâmetro:** `id` - ID da tarefa  
**Request Body:**
```json
{
  "descricao": "Tarefa atualizada",
  "statusRealizada": true
}
```

---

## 📊 Modelo de Dados

### Tarefa
```javascript
{
  _id: ObjectId,           // ID único gerado automaticamente
  descricao: String,       // Descrição da tarefa (obrigatório)
  statusRealizada: Boolean // Status de conclusão (obrigatório)
}
```

---

## 💻 Como Configurar e Executar

### 📋 Pré-requisitos
- Node.js instalado
- MongoDB em execução (local ou remoto)
- npm ou yarn

### 🔧 Instalação

1. **Clone ou baixe o projeto:**
```bash
cd API
```

2. **Instale as dependências:**
```bash
npm install
```

3. **Configure as variáveis de ambiente:**

Crie um arquivo `.env` na raiz do projeto (opcional):
```
PORT=3000
MONGO_URL=mongodb://localhost:27017/tarefas
```

Se não configurar, usa valores padrão:
- `PORT`: 3000
- `MONGO_URL`: Variável de ambiente ou URI do MongoDB Atlas

### ▶️ Executar o Servidor

```bash
npm start
```

O servidor iniciará na porta **3000** (ou conforme configurado):
```
Server Started at 3000
Database Connected
```

---

## 🔌 CORS (Compartilhamento de Recursos)

A API está configurada para aceitar requisições de **qualquer origem** (CORS habilitado):

**Métodos permitidos:** HEAD, GET, POST, PATCH, DELETE  
**Headers permitidos:** Origin, X-Requested-With, Content-Type, Accept

---

## 🔗 Integração com Frontend

O frontend deve consumir os endpoints da seguinte forma:

**Base URL:** `http://localhost:3000/api`

### Exemplo com Fetch API (JavaScript):

```javascript
// Criar tarefa
fetch('http://localhost:3000/api/post', {
  method: 'POST',
  headers: { 'Content-Type': 'application/json' },
  body: JSON.stringify({ 
    descricao: 'Nova tarefa',
    statusRealizada: false 
  })
})

// Obter todas
fetch('http://localhost:3000/api/getAll')

// Atualizar
fetch('http://localhost:3000/api/update/ID_AQUI', {
  method: 'PATCH',
  headers: { 'Content-Type': 'application/json' },
  body: JSON.stringify({ 
    statusRealizada: true 
  })
})

// Deletar
fetch('http://localhost:3000/api/delete/ID_AQUI', {
  method: 'DELETE'
})
```

---

## 🐛 Tratamento de Erros

Todos os endpoints possuem tratamento de erros:

| Código | Significado |
|--------|------------|
| **200** | Sucesso |
| **400** | Erro na requisição (dados inválidos) |
| **500** | Erro interno do servidor |

---

## 📝 Licença

Este projeto está licenciado sob ISC License.

---

## 👤 Autor

Desenvolvido como parte de um projeto de gerenciamento de tarefas com arquitetura full-stack.

---

## 📞 Suporte

Para dúvidas ou problemas, verifique:
- Conexão com MongoDB
- Porta 3000 disponível
- Variáveis de ambiente configuradas corretamente