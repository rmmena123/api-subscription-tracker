# 📦 Subscription Tracker API

Uma API segura, escalável e moderna para gerenciar assinaturas, com autenticação de usuário integrada, proteção Arcjet e autorização baseada em funções. Foi desenvolvida durante o [curso de back-end do canal Javascript Mastery](https://www.youtube.com/watch?v=rOpEN1JDaD0).

---

## 🚀 Features

- 🔐 **Autenticação Completa de Usuário**: Rotas para registro e login com JWT.
- 🧾 **Gerenciamento de Assinaturas**: Operações CRUD completas (criar, ler, atualizar, deletar) para assinaturas.
- 🧠 **Fluxo de Lembretes**: Envio automatizado de lembretes por e-mail antes das datas de renovação, utilizando Upstash Workflows.
- 🛡️ **Proteção com Arcjet**: Integração para defesa contra ataques DDoS, bots e limitação de taxa (rate limiting).
- 🧪 **Autorização Baseada em Funções**: Middleware para restringir o acesso a rotas específicas com base na função do usuário.
- 🌐 **Design RESTful**: API projetada seguindo os princípios REST para uma comunicação clara e padronizada.
- 🗃️ **Integração com MongoDB**: Utiliza Mongoose para uma modelagem de dados robusta e interação com o banco de dados.
- ⚙️ **Ambiente Configurável**: Suporte a variáveis de ambiente (`.env`) para fácil configuração.

---

## 📁 Estrutura de Pastas

A estrutura do projeto foi organizada para promover a separação de responsabilidades e facilitar a manutenção.

```
subscription-tracker-api/
├── config/              #  Configurações de ambiente, banco de dados e Arcjet
├── controllers/         # Lógica de negócio e funções que manipulam as requisições
├── database/            # Lógica de conexão com o MongoDB
├── middleware/          # Middlewares para erros, autenticação e proteção
├── models/              # Schemas do Mongoose para os modelos de dados
├── routes/              # Definição das rotas da API
├── app.js               # Arquivo principal de configuração do Express
└── .env                 # Variáveis de ambiente (não versionadas)
```

[Documentação técnica completa](https://rmmena123.notion.site/Subscription-Tracker-API-2365a575c33f804991c8dffb379a8c16)

---

## ⚙️ Instalação e Configuração

```bash
# Clone o repositório
git clone https://github.com/rmmena123/api-subscription-tracker.git

# Navegue até o diretório do repositório
cd api-subscription-tracker

# Instale as dependências (Versão 22 do Node.js)
npm install

# Configure as variáveis de ambiente em um arquivo .env.development.local
- `MONGO_URI`: URI de conexão do MongoDB.
- `JWT_SECRET`: Chave para assinar os tokens JWT.
- `JWT_EXPIRES_IN`: Tempo de expiração para os tokens (ex: `90d`).
- `ARCJET_KEY`: Chave de API do Arcjet para proteção.
- `UPSTASH_WORKFLOW_URL`: URL do seu workflow no Upstash.
- `UPSTASH_TOKEN`: Token de autorização do Upstash

# Inicie o servidor de desenvolvimento
npm run dev
```

---

## 🔐 Autenticação e Autorização

- A autenticação é baseada em **JSON Web Tokens (JWT)**. Após o login, um token é gerado e armazenado em um cookie seguro (`httpOnly`).
- Rotas protegidas utilizam o middleware `authorize` para garantir que apenas usuários autenticados possam acessá-las.

---

## 🛡️ Arcjet Middleware

O middleware do Arcjet é aplicado globalmente no `app.js` para analisar o tráfego de entrada antes que ele chegue às rotas da sua aplicação. Isso oferece uma camada de defesa proativa contra:

- ❌ Ataques DDoS
- 🤖 Tráfego de bots maliciosos
- 📈 Limitação de taxa (Rate Limiting) para prevenir abusos

---

## 📬 Reminder Workflow

Um fluxo de trabalho automatizado, gerenciado pelo **Upstash Workflow**, é responsável por enviar lembretes aos usuários.

- Os lembretes são agendados para **7, 5, 2 e 1 dia(s)** antes da data de renovação de uma assinatura.
- A lógica de cálculo de datas é gerenciada pela biblioteca **Day.js**.

---

## 🧰 Tecnologias Utilizadas

- **Node.js** + **Express**
- **MongoDB** + **Mongoose**
- **JSON Web Token (JWT)**
- **Arcjet** (Middleware de segurança)
- **Upstash Workflow** (Lógica de agendamento)
- **Day.js** (Manipulação de datas e horas)
- **Nodemailer** (Envio de e-mails)

---

## 👨‍💻 Autor

Desenvolvido por [Rodrigo Mena](https://github.com/rmmena123)

---

## 📝 Licença

Este projeto está licenciado sob a Licença MIT. Veja o arquivo `LICENSE` para mais detalhes.
