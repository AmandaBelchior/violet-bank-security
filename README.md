# 🔐 Violet Bank Security — Plataforma de Gestão de Incidentes

> Sistema interno de monitoramento e gestão de incidentes de segurança para analistas do SOC (Security Operations Center) do Violet Bank.

---

## 📌 Sobre o Projeto

O **Violet Bank Security** é uma aplicação web construída no **Bubble.io** que centraliza o ciclo de vida dos incidentes de segurança — desde o reporte até a resolução — permitindo que analistas acompanhem, classifiquem e respondam a ameaças de forma organizada e eficiente.

---

## 🖼️ Screenshots

> As capturas de tela da aplicação estão na pasta [Screenshots Projeto Violet Bank Security](https://github.com/AmandaBelchior/violet-bank-security/tree/main/Screenshots%20Projeto).

| Tela | Descrição |
|---|---|
| `screenshots/login.png` | Tela de login |
| `screenshots/signup.png` | Tela de cadastro |
| `screenshots/dashboard.png` | Dashboard SOC |
| `screenshots/meus-incidentes.png` | Lista de incidentes |
| `screenshots/reportar-incidente.png` | Formulário de novo incidente |
| `screenshots/relatorios.png` | Página de relatórios |

---

## ✨ Funcionalidades

### Autenticação
- **Login** com email e senha (workflow nativo do Bubble)
- **Cadastro** de novo analista via formulário HTML + JavascripttoBubble
- Redirecionamento automático para o dashboard após autenticação
- **Proteção de rotas**: todas as páginas internas redirecionam para o login caso o usuário não esteja autenticado

### Dashboard SOC
- Visão geral dos incidentes ativos
- Métricas em tempo real: Críticos, Alto Risco, Em Investigação, Resolvidos
- Acesso rápido às principais seções

### Meus Incidentes
- Lista de incidentes atribuídos ao analista logado
- Filtros por status: Todos, Ativos, Críticos, Resolvidos
- Informações de tipo e tempo de cada incidente

### Reportar Incidente
- Formulário para criação de novo incidente de segurança
- Registro automático na base de dados (`SecurityIncident`)
- Redirecionamento para o dashboard após o envio

### Relatórios
- Tabela completa com colunas: Incidente, Tipo, Severidade, Status, Ações
- Severidade visual com badges: `CRITICAL`, `HIGH RISK`, `MEDIUM`
- Status com indicadores coloridos: Triage, Investigando, Resolvido
- Botões de ação: **Ver Detalhes** e **Ver Arquivo**

---

## 🗂️ Estrutura de Páginas

| Página | Rota | Descrição |
|---|---|---|
| Login | `/index` | Tela de autenticação |
| Cadastro | `/signup` | Criação de conta |
| Dashboard | `/dashboard_soc` | Painel principal do SOC |
| Meus Incidentes | `/meus_incidentes` | Incidentes do analista |
| Reportar Incidente | `/reportar_incidente` | Formulário de novo incidente |
| Relatórios | `/relatorios` | Visão consolidada de todos os incidentes |
| Detalhe do Incidente | `/incidente_detalhe` | Informações detalhadas |
| Perfil | `/perfil` | Dados do analista |
| Notificações | `/notificacoes` | Alertas e atualizações |
| Tarefas | `/tarefas` | Tarefas atribuídas |
| Nova Tarefa | `/nova_tarefa` | Criação de tarefa |
| Reset de Senha | `/reset_pw` | Recuperação de acesso |

---

## 🧡 Tecnologias Utilizadas

| Tecnologia | Uso |
|---|---|
| [Bubble.io](https://bubble.io) | Plataforma no-code principal |
| HTML/CSS customizado | Interfaces e componentes visuais |
| JavascripttoBubble (plugin) | Integração entre JS e workflows do Bubble |
| Bubble Database | Armazenamento de usuários e incidentes |

---

## 🔄 Arquitetura de Workflows

```
[HTML Form]
    → bubble_fn_signup(nome, email, senha)
    → JavascripttoBubble A event
    → Sign the user up
    → Go to page dashboard_soc

[Botão Login]
    → Log the user in
    → Go to page dashboard_soc

[Formulário de Incidente]
    → bubble_fn_submit(dados)
    → JavascripttoBubble A event
    → Create a new SecurityIncident
    → Go to page dashboard_soc

[Page is loaded — qualquer página interna]
    → Only when: Current User is logged out
    → Go to page index
```

---

## 🛡️ Segurança

- Todas as rotas internas possuem proteção via workflow `Page is loaded`
- Condição: `Current User is logged out → redirect to /index`
- Senhas gerenciadas pelo sistema nativo de autenticação do Bubble

---

## 🗃️ Data Types (Banco de Dados)

| Tipo | Campos principais |
|---|---|
| `User` | nome, email, senha (nativo Bubble) |
| `SecurityIncident` | título, tipo, severidade, status, criado_por, data |

---

## 🚀 Como Acessar

1. Acesse o editor: [bubble.io](https://bubble.io) → app `amandacbvallis-98604`
2. Clique em **Preview** para testar a aplicação
3. Crie uma conta pelo `/signup` ou use uma conta existente

---

## 📋 Status do MVP

| Item | Status |
|---|---|
| Workflow de login | ✅ Concluído |
| Workflow de signup | ✅ Concluído |
| Proteção de páginas internas | ✅ Concluído |
| Workflow de criar incidente | ✅ Concluído |
| Página de Relatórios | ✅ Concluído |

---

## 👩‍💻 Desenvolvido por

Amanda Belchior  
Projeto prático 
