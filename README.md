<div align="center">

# MIBI
### Módulo de Inteligência Binária Interna

**Plataforma de RH com IA para equipes modernas**

Gestão de pessoas com **multi-tenancy real, assistentes inteligentes e aprendizado contínuo** — cada empresa no seu próprio ambiente isolado.

<br />

[![Demo ao vivo](https://img.shields.io/badge/%E2%96%B6%20Demo%20ao%20vivo-demonstracao.rh.lucaskarsten.com.br-6366f1?style=for-the-badge)](https://demonstracao.rh.lucaskarsten.com.br)

<br />

![Login](./screenshots/Login.png)

</div>

---

## O que é o MIBI?

**MIBI** é uma plataforma de RH com inteligência artificial integrada, construída para empresas que querem ir além do básico. O assistente não apenas responde perguntas — ele **aprende com o feedback dos colaboradores** e melhora automaticamente ao longo do tempo.

Cada empresa opera em um **ambiente completamente isolado**: dados próprios, agentes configuráveis e histórico exclusivo. Sem compartilhamento entre organizações.

---

## Para quem é o MIBI?

- **Times de RH** que precisam responder dúvidas recorrentes sem criar filas de chamados
- **Recrutadores** que conduzem entrevistas e querem análise de candidatos com suporte de IA
- **Gestores** que precisam de visibilidade sobre a equipe sem complexidade de configuração
- **Empresas** que levam a sério a privacidade dos dados internos

---

## Funcionalidades

### 🤖 Assistente de RH com IA

O colaborador pergunta. A IA responde — com contexto real da empresa: benefícios, políticas internas, férias, folha de pagamento. Sem abrir chamado. Sem esperar o RH.

As respostas podem ser copiadas com um clique. O feedback (👍 / 👎) é enviado diretamente na mensagem — e alimenta o sistema de aprendizado do agente.

![Chat com IA](./screenshots/chat.png)

---

### 👥 Gestão de Equipe

Visão completa dos colaboradores com controle de acesso granular. Suporte a tema claro e escuro.

![Painel da Equipe](./screenshots/Painel%20Equipe.png)

- Convite por e-mail com link personalizado por empresa
- Controle de papéis: `admin` e `member` por organização
- Flag de recrutador para acesso ao módulo de seleção
- Perfis individuais com histórico de atividades

![Lista da Equipe](./screenshots/Equipe.png)

---

### 🎯 Módulo de Recrutamento

Do processo seletivo ao parecer final, tudo em um único painel.

![Recrutamento](./screenshots/recrutamento.png)

- Processos com status em tempo real: `Aberto`, `Em espera`, `Encerrado`, `Cancelado`
- Cadastro e acompanhamento de candidatos com histórico completo
- Filtros por status com visualização instantânea
- Botão **Entrevistar** direto na lista de candidatos

#### 🎬 Painel de Entrevista em Tempo Real

Ambiente dedicado para conduzir entrevistas de forma estruturada e documentada.

![Dashboard Geral](./screenshots/dashboard%20geral.png)

| Aba | Para quê serve |
|---|---|
| **Geral** | Visão completa do candidato + análise de currículo por IA |
| **Anotações** | Notas livres e observações comportamentais durante a entrevista |
| **Comportamento** | Registro de perguntas e respostas estruturadas |
| **Análise de Currículo** | Parecer detalhado com recomendação final gerada por IA |

![Dashboard Comportamental](./screenshots/dashboard%20comportamental.png)

O recrutador tem à disposição: cronômetro de sessão com alerta visual, notas por dimensão (técnica, comunicação, cultura, experiência, motivação), modo de preparação pré-entrevista, modal de conclusão e exportação completa para PDF ou clipboard.

Ao concluir, o candidato passa automaticamente para o status **Entrevistado**.

![Avaliação do Candidato](./screenshots/avalia%C3%A7%C3%A3o%20candidato.png)

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

Cada organização controla seu próprio ambiente: agentes, base de conhecimento, integrações e preferências.

![Configurações](./screenshots/configura%C3%A7%C3%B5es.png)

---

### 🏢 Multi-tenancy Real

Cada empresa possui um **schema dedicado no PostgreSQL** — não há camada de compartilhamento. Os dados de uma organização jamais se misturam com os de outra.

```
empresa_a.rh.app  →  schema isolado da empresa A
empresa_b.rh.app  →  schema isolado da empresa B
```

Privacidade de dados por design, não por configuração.

---

## ⚡ Acesse a Demo

URL: `https://demonstracao.rh.lucaskarsten.com.br` · Senha: `123456`

| Perfil | Email | O que explorar |
|---|---|---|
| **Admin** | `ana@demonstracao.com` | Gestão de equipe, configurações, agentes de IA e base de conhecimento |
| **Membro** | `rafael@demonstracao.com` | Chat com o assistente de RH, feedback de respostas |
| **Recrutador** | `beatriz@demonstracao.com` | Processos seletivos, candidatos, painel de entrevista completo |

> A demo usa currículos públicos reais como base de dados de candidatos, permitindo validar a análise de IA com conteúdo representativo.

---

## 🗺️ Roadmap

| Funcionalidade | Status |
|---|---|
| Assistente de RH com IA | ✅ Em produção |
| Módulo de recrutamento | ✅ Em produção |
| Painel de entrevista em tempo real | ✅ Em produção |
| Comparação de candidatos por IA | 🔜 Em breve |
| Upload de currículo com extração automática | 🔜 Em breve |
| Resumo de currículo por IA | 🔜 Em breve |
| Sugestão de perguntas por IA | 🔜 Em breve |
| Agente do colaborador (feedbacks internos) | 📅 v2 |
| SSO (Google / Microsoft) | 📅 v2 |
| Dashboards analíticos | 📅 v2 |

---

## 🛠️ Stack

| Camada | Tecnologia |
|---|---|
| **Frontend / Backend** | Next.js · JavaScript |
| **Banco de dados (DEV)** | PostgreSQL local via Docker |
| **Banco de dados (PRD)** | NeonDB (serverless Postgres) |
| **IA** | Claude Sonnet (Anthropic) |
| **Hospedagem** | Vercel |

Código-fonte e documentação técnica: [lucaskarsten/mibi-core](https://github.com/lucaskarsten/mibi-core)

---

Desenvolvido por **Lucas Karsten**
