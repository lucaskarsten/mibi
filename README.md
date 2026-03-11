<div align="center">

<img src="https://raw.githubusercontent.com/lucaskarsten/mibi/main/screenshots/logo.png" alt="mibi" width="120" />

# mibi

### Plataforma de RH com inteligência artificial para equipes modernas

Gestão de pessoas com **multi-tenancy real, automação inteligente e IA integrada** — tudo em um só lugar.

<br />

[![Demo ao vivo](https://img.shields.io/badge/Demo%20ao%20vivo-→-6366f1?style=for-the-badge)](https://demonstracao.rh.lucaskarsten.com.br)
[![Next.js](https://img.shields.io/badge/Next.js-15-black?style=for-the-badge&logo=next.js)](https://nextjs.org)
[![Vercel](https://img.shields.io/badge/Vercel-deployed-black?style=for-the-badge&logo=vercel)](https://vercel.com)
[![PostgreSQL](https://img.shields.io/badge/PostgreSQL-NeonDB-336791?style=for-the-badge&logo=postgresql)](https://neon.tech)

<br />

</div>

---

## ✨ O que é o mibi?

**mibi** é uma plataforma de RH construída para empresas que querem usar inteligência artificial de forma prática no dia a dia de pessoas.

Cada empresa opera em um **ambiente completamente isolado** — com seus próprios dados, agentes de IA personalizados e histórico exclusivo. Sem compartilhamento. Sem risco de vazamento entre organizações.

> **Acesse agora:** [demonstracao.rh.lucaskarsten.com.br](https://demonstracao.rh.lucaskarsten.com.br)
> `beatriz@demonstracao.com` · `lucas1`

---

## 🖼️ Visão geral

<div align="center">

![Dashboard principal](./screenshots/dashboard.png)
*Painel principal — visão consolidada da equipe*

</div>

---

## 🚀 Funcionalidades

### 👥 Gestão de Colaboradores

Onboarding simples, controle de acesso granular e perfis completos para cada pessoa da sua equipe.

- Convite por e-mail com link personalizado por empresa
- Perfis individuais com histórico de atividades
- Controle de papéis: `admin` e `member` por organização

<div align="center">

![Gestão de colaboradores](./screenshots/colaboradores.png)
*Painel de gestão de colaboradores*

</div>

---

### 🤖 Agentes de IA

Cada empresa tem seus próprios agentes configuráveis, baseados em templates globais que **evoluem continuamente** com o uso.

| Agente | O que faz |
|---|---|
| **Assistente de RH** | Responde dúvidas sobre benefícios, férias, políticas internas e folha de pagamento |
| **Assistente de Recrutamento** | Analisa candidatos, sugere perguntas e gera pareceres estruturados |

Os agentes aprendem com os feedbacks dos colaboradores via um sistema de **digest anônimo** — ficam mais inteligentes com o tempo, sem comprometer a privacidade.

<div align="center">

![Agente de IA](./screenshots/agente-rh.png)
*Assistente de RH em ação — respostas contextualizadas para sua equipe*

</div>

---

### 🎯 Módulo de Recrutamento

Do processo seletivo ao parecer final, tudo em um único painel. A IA analisa candidatos, sugere perguntas de entrevista e gera avaliações estruturadas — economizando horas do seu time de recrutamento.

- Processos seletivos com controle de status em tempo real
- Cadastro e acompanhamento de candidatos
- **Painel de entrevista** para recrutadores: notas, perguntas/respostas e cronômetro de sessão
- Análise de candidatos por IA com parecer detalhado e recomendação final
- Histórico completo vinculado ao candidato para comparações futuras

<div align="center">

![Módulo de recrutamento](./screenshots/recrutamento.png)
*Painel de recrutamento — do processo seletivo ao parecer da IA*

![Painel de entrevista](./screenshots/entrevista.png)
*Painel de entrevista ao vivo — notas e cronômetro integrados*

</div>

---

### 🏢 Multi-tenancy Real

Arquitetura de isolamento total: cada empresa possui um **schema dedicado no PostgreSQL**. Não existe camada de compartilhamento — os dados da sua empresa não se misturam com os de nenhuma outra organização.

```
empresa_a.rh.app  →  schema isolado da empresa A
empresa_b.rh.app  →  schema isolado da empresa B
```

Isso significa privacidade de dados por design, não por configuração.

---

## 🗺️ Roadmap

| Funcionalidade | Status |
|---|---|
| Assistente de RH com IA | ✅ Em produção |
| Módulo de recrutamento | ✅ Em produção |
| Painel de entrevista em tempo real | 🔜 Em desenvolvimento |
| Comparação de candidatos por IA | 🔜 Em breve |
| Agente do colaborador (feedbacks internos) | 📅 v2 |
| SSO (Google / Microsoft) | 📅 v2 |
| Dashboards analíticos | 📅 v2 |

---

## 🛠️ Stack técnica

| Camada | Tecnologia |
|---|---|
| **Frontend / Backend** | Next.js 15 · JavaScript |
| **Roteamento / Proxy** | `proxy.js` (custom, sem middleware.js) |
| **Banco de dados (DEV)** | PostgreSQL local |
| **Banco de dados (PRD)** | NeonDB (serverless Postgres) |
| **Hospedagem** | Vercel |
| **Domínio** | Registro.br |

---

## ⚡ Acesso à demo

Explore todas as funcionalidades em nosso ambiente de demonstração:

```
URL:   https://demonstracao.rh.lucaskarsten.com.br
Email: beatriz@demonstracao.com
Senha: lucas1
```

---

## 📬 Contato

Desenvolvido por **Lucas Karsten**

Tem interesse no produto ou quer conversar sobre integrações? Entre em contato.
