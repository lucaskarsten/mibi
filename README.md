<div align="center">

# mibi

### Plataforma de RH com inteligência artificial para equipes modernas

Gestão de pessoas com **multi-tenancy real, automação inteligente e IA integrada** — tudo em um só lugar.

<br />

[![Demo ao vivo](https://img.shields.io/badge/▶%20Demo%20ao%20vivo-demonstracao.rh.lucaskarsten.com.br-6366f1?style=for-the-badge)](https://demonstracao.rh.lucaskarsten.com.br)

<br />

![Login](./screenshots/Login.png)

</div>

---

## O que é o mibi?

**mibi** é uma plataforma de RH construída para empresas que querem usar inteligência artificial de forma prática no dia a dia de pessoas.

Cada empresa opera em um **ambiente completamente isolado** — com seus próprios dados, agentes de IA personalizados e histórico exclusivo. Sem compartilhamento. Sem risco de vazamento entre organizações.

---

## Funcionalidades

### 🤖 Assistente de RH com IA

O colaborador pergunta. A IA responde — com contexto real da empresa: benefícios, políticas internas, férias, folha de pagamento. Sem precisar abrir chamado ou esperar o RH.

![Chat com IA](./screenshots/chat.png)

![Painel de Chat](./screenshots/Painel%20Chat.png)

---

### 👥 Gestão de Equipe

Visão completa da sua equipe com controle de acesso granular. Suporte a tema claro e escuro.

![Painel da Equipe](./screenshots/Painel%20Equipe.png)

![Painel da Equipe - Tema Claro](./screenshots/Painel%20Equipe%20Tema%20Claro.png)

- Convite por e-mail com link personalizado por empresa
- Controle de papéis: `admin` e `member` por organização
- Perfis individuais com histórico de atividades

![Lista da Equipe](./screenshots/Equipe.png)

---

### 🎯 Módulo de Recrutamento

Do processo seletivo ao parecer final, tudo em um único painel. A IA analisa candidatos, sugere perguntas de entrevista e gera avaliações estruturadas.

![Recrutamento](./screenshots/recrutamento.png)

- Processos seletivos com controle de status em tempo real
- Cadastro e acompanhamento de candidatos
- Painel de entrevista para recrutadores: notas, perguntas/respostas e cronômetro de sessão
- Análise de candidatos por IA com parecer detalhado e recomendação final
- Histórico completo vinculado ao candidato para comparações futuras

---

### ⚙️ Agentes de IA Configuráveis

Cada empresa tem seus próprios agentes, baseados em templates globais que **evoluem continuamente** com o uso e os feedbacks da equipe.

![Agentes](./screenshots/agentes.png)

| Agente | O que faz |
|---|---|
| **Assistente de RH** | Responde dúvidas sobre benefícios, férias, políticas internas e folha de pagamento |
| **Assistente de Recrutamento** | Analisa candidatos, sugere perguntas e gera pareceres estruturados |

Os agentes aprendem via um sistema de **digest anônimo** — ficam mais inteligentes com o tempo, sem comprometer a privacidade.

---

### 🔧 Configurações por Empresa

Cada organização controla seu próprio ambiente: agentes, integrações e preferências.

![Configurações](./screenshots/configura%C3%A7%C3%B5es.png)

---

### 🏢 Multi-tenancy Real

Cada empresa possui um **schema dedicado no PostgreSQL** — não há camada de compartilhamento. Os dados da sua empresa não se misturam com os de nenhuma outra organização.

```
empresa_a.rh.app  →  schema isolado da empresa A
empresa_b.rh.app  →  schema isolado da empresa B
```

Privacidade de dados por design, não por configuração.

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

## ⚡ Acesse a demo

```
URL:   https://demonstracao.rh.lucaskarsten.com.br
Email: beatriz@demonstracao.com
Senha: lucas1
```

---

## 🛠️ Stack

| Camada | Tecnologia |
|---|---|
| **Frontend / Backend** | Next.js · JavaScript |
| **Proxy / Roteamento** | `proxy.js` |
| **Banco de dados (DEV)** | PostgreSQL local |
| **Banco de dados (PRD)** | NeonDB |
| **Hospedagem** | Vercel |
| **Domínio** | Registro.br |

---

Desenvolvido por **Lucas Karsten**
