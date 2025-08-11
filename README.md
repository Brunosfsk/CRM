# 🚀 MinhaMaquina – Full-Stack Application

Este repositório é uma visão consolidada do projeto **MinhaMaquina**, uma aplicação full-stack desenvolvida durante minha atuação profissional. Ele combina um backend robusto com um frontend moderno, integrando diversas tecnologias e práticas de engenharia de software para entregar uma solução escalável, modular e altamente performática.

Como os repositórios originais são privados (por conterem código interno da empresa), este documento serve como **portfólio técnico**, descrevendo a arquitetura, tecnologias utilizadas, responsabilidades desempenhadas e as principais decisões de projeto.

---

## 🏗️ Arquitetura do Projeto

O sistema é composto por dois módulos principais:

| Módulo | Tecnologia | Tipo |
|-------|------------|------|
| **Backend** | NestJS (Node.js) + PostgreSQL + Prisma | API REST e WebSockets |
| **Frontend** | React + Vite + TypeScript | SPA (Single Page Application) |

Ambos os serviços são containerizados com **Docker**, orquestrados via **Docker Compose** e deployados no **Google Cloud Run** com integração contínua via **GitLab CI/CD**.

---

## 🔧 Tecnologias Utilizadas

### Backend
- **NestJS** – Framework Node.js modular, baseado em TypeScript, com suporte a injeção de dependência, decorators e arquitetura em camadas.
- **Prisma ORM** – Para modelagem e acesso ao banco de dados PostgreSQL.
- **PostgreSQL** – Banco de dados relacional usado para persistência de dados.
- **Google Cloud Storage** – Armazenamento de arquivos (imagens, documentos, etc.).
- **WebSockets** – Comunicação em tempo real entre cliente e servidor.
- **Swagger/OpenAPI** – Documentação automática da API.
- **Docker & Docker Compose** – Containerização e orquestração local.
- **GitLab CI/CD** – Automação de build e deploy no Google Cloud Run.

### Frontend
- **React** – Biblioteca para construção de interfaces dinâmicas e componentizadas.
- **Vite** – Ferramenta de build moderna, rápida e otimizada.
- **TypeScript** – Tipagem estática para maior segurança e manutenibilidade.
- **React Context API** – Gerenciamento de estado global (autenticação, permissões, etc).
- **Custom Hooks** – Reutilização lógica de chamadas à API.
- **i18n** – Suporte a internacionalização (múltiplos idiomas).
- **Axios com interceptors** – Camada de comunicação com a API, com tratamento de erros e autenticação.
- **Docker & CI/CD** – Mesma stack de deploy do backend.

---

## 📂 Estrutura e Modularização

### Backend (NestJS)
O backend foi estruturado em módulos bem definidos, garantindo escalabilidade e separação de responsabilidades:

- `auth` – Autenticação JWT e controle de sessão.
- `user` e `client` – Gestão de usuários e clientes (multi-tenant).
- `crm` – Módulo completo de CRM com:
  - Leads, cards, pipelines, colunas
  - Atividades, motivos de perda, relatórios
  - Fontes de origem (sources)
- `bucket` – Upload e gerenciamento de arquivos no Google Cloud Storage.
- `prisma` – Camada de persistência com migrações versionadas.
- `cors` – Configuração dinâmica de CORS com suporte a regex (para subdomínios).

> 🛠️ **Destaque técnico**: Implementação de WebSockets para notificações em tempo real e integração com sistema externo (Make.com) via webhooks.

---

### Frontend (React)
O frontend foi organizado com foco em reutilização, manutenção e segurança:

- `components/` – Componentes UI reutilizáveis (botões, cards, modais).
- `pages/` – Telas da aplicação (dashboard, CRM, perfis).
- `services/` – Configuração do Axios, interceptadores e utils.
- `hooks/` – Custom hooks para chamadas à API (ex: `useLeads`, `useAuth`).
- `context/` – Contextos para autenticação, permissões e configurações.
- `routes/` – Rotas protegidas por roles e permissões.
- `privatePermissions/` – Componentes que só exibem conteúdo com base em permissão.
- `i18n/` – Sistema de tradução com suporte a múltiplos idiomas.

> 🎯 **Destaque técnico**: Sistema de rotas privadas com controle de acesso baseado em perfil, integrado ao contexto de autenticação.

---

## ⚙️ Infraestrutura e CI/CD

Ambos os projetos utilizam uma pipeline robusta no **GitLab CI/CD**:

1. **Build** – Imagem Docker é construída e enviada ao **Google Artifact Registry**.
2. **Deploy** – Aplicação é deployada no **Google Cloud Run** (servless, escalável).
3. **Ambientes** – Configurações distintas para dev, staging e produção.

Também foi implementado suporte a **DevContainers no VS Code**, permitindo setup rápido de ambiente de desenvolvimento com Docker.

---

## 🔐 Variáveis de Ambiente (Exemplos)

Configurações sensíveis são gerenciadas via `.env`, com suporte a múltiplos ambientes:

**Backend**
- `DATABASE_URL` – Conexão com PostgreSQL.
- `BUCKET_NAME` – Nome do bucket no GCS.
- `KEY_GOOGLE_CLOUD_STORAGE` – Chave de acesso criptografada.
- `CORS_ALLOWED_ORIGINS_REGEX` – Permite subdomínios dinâmicos.
- `API_TOKEN_INTERN` – Token para integrações internas.

**Frontend**
- `VITE_API_HOST` – URL da API backend.
- `VITE_DOMAIN` / `VITE_SUBDOMAIN` – Configuração de domínio para ambientes locais.

---

## 🌐 Escopo e Funcionalidades

O sistema **MinhaMaquina** é uma plataforma de gestão de leads e relacionamento com clientes (CRM), com foco em:

- Gestão de pipelines e etapas de vendas.
- Automação de atividades e notificações.
- Upload e armazenamento de documentos.
- Relatórios personalizados.
- Multi-tenant (vários clientes com dados isolados).
- Acesso seguro com autenticação JWT e controle de permissões.

---

## 🤝 Considerações Finais

Este projeto representa uma aplicação real que construi junto a mais um desenvolvedor, usada no momento pela própria empresa, com requisitos de escalabilidade, segurança e usabilidade. A combinação de **NestJS no backend** e **React no frontend** provou-se extremamente eficaz para manter um código limpo, testável e evolutivo.

Embora o código-fonte não possa ser compartilhado publicamente, este documento reflete com fidelidade a experiência prática com tecnologias modernas no desenvolvimento full-stack.
