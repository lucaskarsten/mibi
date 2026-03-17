<div align="center">

# mibi

### A plataforma de RH que pensa com você

Gerencie pessoas, conduza processos seletivos e responda dúvidas da equipe — com **inteligência artificial integrada** e cada empresa no seu próprio ambiente isolado.

<br />

[![Demo ao vivo](https://img.shields.io/badge/▶%20Acessar%20demo-demonstracao.rh.lucaskarsten.com.br-6366f1?style=for-the-badge)](https://demonstracao.rh.lucaskarsten.com.br)

<br />

![Painel principal do mibi](./screenshots/01-painel.png)

> **Dados fictícios.** Todos os nomes, vagas, candidatos, métricas e conteúdos exibidos nas capturas de tela são gerados para fins de demonstração e não representam pessoas ou empresas reais.

</div>

---

## O problema que o mibi resolve

Times de RH gastam horas respondendo as mesmas perguntas, acompanhando candidatos em planilhas e conduzindo entrevistas sem estrutura. O mibi centraliza tudo isso — e ainda usa IA para automatizar o que pode ser automatizado.

Cada empresa opera em um **ambiente completamente isolado**: dados próprios, agentes configuráveis e histórico exclusivo. Sem compartilhamento entre organizações. Sem risco.

---

## Para quem é

- **Times de RH** que querem escalar o atendimento sem aumentar a equipe
- **Recrutadores** que precisam de mais estrutura e menos retrabalho em cada processo
- **Empresas** que levam privacidade de dados a sério

---

## Assistente de RH com IA

O colaborador pergunta, a IA responde — com contexto real da empresa: benefícios, políticas internas, férias, folha de pagamento. Sem abrir chamado. Sem esperar o RH.

O assistente usa a base de conhecimento da própria empresa. Cada resposta traz um aviso legal e pode ser copiada com um clique. O colaborador ainda pode avaliar a resposta com thumbs up/down — e esse feedback alimenta o aprendizado contínuo do agente.

![Conversa com o Assistente de RH](./screenshots/02-chat.png)

Conversas podem ser salvas como **snapshots** com resumo gerado por IA, impressas ou compartilhadas — útil para registros de decisão e processos internos.

![Snapshot da conversa com resumo e opção de impressão](./screenshots/03-impressao-chat.png)

---

## Módulo de Recrutamento

Do processo aberto ao candidato contratado, tudo em um lugar só — com IA analisando em cada etapa.

### Visão geral do pipeline

Acompanhe todos os candidatos ativos, entrevistas agendadas, taxa de conversão e tempo médio de pipeline em tempo real. A atividade recente aparece automaticamente, sem precisar atualizar nada.

![Dashboard de recrutamento com pipeline e atividade recente](./screenshots/04-pipeline.png)

### Ranking de candidatos por processo

O mibi pontua e classifica candidatos automaticamente por aderência à vaga. O recrutador vê os melhores candidatos de cada processo sem precisar ler currículo por currículo.

![Ranking de candidatos por processo seletivo](./screenshots/05-top-candidatos.png)

### Processos seletivos

Crie e gerencie processos com controle de status em tempo real: `Aberto`, `Em espera`, `Encerrado` e `Cancelado`. Cada processo tem número único, responsável e histórico completo de candidatos.

![Lista de processos seletivos com status e candidatos](./screenshots/06-processos-seletivos.png)

### Candidatos

Cadastre, busque e filtre candidatos por status, etapa e data de entrevista. Upload de currículo com análise automática por IA — o sistema extrai dados estruturados e gera um parecer sem nenhuma entrada manual.

![Lista de candidatos com filtros e detalhes](./screenshots/07-candidatos.png)

### Painel de entrevista

Ambiente dedicado para conduzir entrevistas com estrutura e sem distrações. O recrutador vê o perfil completo do candidato, avalia por dimensões (técnica, comunicação, cultura, experiência, motivação) e registra observações comportamentais em tempo real.

![Painel de entrevista com avaliação por dimensões](./screenshots/08-entrevista.png)

O cronômetro de sessão fica sempre visível. Ao concluir, o candidato avança automaticamente para `Entrevistado` e o sistema oferece geração de resumo por IA sob demanda.

---

## Agentes de IA configuráveis

Cada empresa tem seus próprios agentes, baseados em templates globais que evoluem com o uso. O feedback dos colaboradores alimenta um sistema de digest anônimo — os agentes ficam mais inteligentes ao longo do tempo, sem comprometer a privacidade.

| Agente | O que faz |
|---|---|
| **Assistente de RH** | Responde dúvidas sobre benefícios, férias, políticas e folha de pagamento |
| **Assistente de Recrutamento** | Analisa candidatos, sugere perguntas e gera pareceres estruturados |
| **Assistente do Recrutador** | Apoia o recrutador durante entrevistas com contexto de preferências pessoais |
| **Arena** | Compara candidatos lado a lado com análise aprofundada por IA |
| **Digest do Recrutador** | Processa preferências do recrutador em texto livre e as injeta nos demais agentes |

---

## Multi-tenancy real

Cada empresa possui um **schema dedicado no PostgreSQL**. Não existe camada de compartilhamento — os dados de uma organização jamais se misturam com os de outra.

```
empresa_a.rh.app  →  schema isolado da empresa A
empresa_b.rh.app  →  schema isolado da empresa B
```

Privacidade de dados por arquitetura, não por configuração.

---

## Compliance e Legal

- **LGPD compliant** — exportação e anonimização de dados disponíveis
- **Aceite de termos** com versionamento no registro
- **Geo-blocking** para regiões sem adequação regulatória (EU/EEA/UK)
- **Audit log** de operações de IA e decisões de dados
- **Disclaimer de IA** em todas as respostas geradas
- Documentação legal completa: [mibi-legal](https://github.com/lucaskarsten/mibi-legal)

---

## Acesse a demo

| | |
|---|---|
| **URL** | https://demonstracao.rh.lucaskarsten.com.br |
| **Admin** | `ana@demonstracao.com` — gestão de equipe, agentes e configurações |
| **Membro** | `rafael@demonstracao.com` — chat com assistente de RH |
| **Recrutador** | `beatriz@demonstracao.com` — processos, candidatos e entrevistas |
| **Senha** | `123456` |

> Todos os dados do ambiente de demonstração — nomes, vagas, candidatos, métricas e conversas — são **inteiramente fictícios** e gerados para fins de teste. Não representam pessoas, empresas ou situações reais.

---

## Roadmap

| Funcionalidade | Status |
|---|---|
| Assistente de RH com IA | ✅ Em produção |
| Módulo de recrutamento completo | ✅ Em produção |
| Painel de entrevista em tempo real | ✅ Em produção |
| Upload e análise de currículo por IA | ✅ Em produção |
| Snapshots de conversa com resumo por IA | ✅ Em produção |
| Perfil de preferências do recrutador | ✅ Em produção |
| LGPD e compliance | ✅ Em produção |
| Responsividade mobile | ✅ Em produção |
| Arena — comparação de candidatos por IA | 🔜 Em breve |
| Kanban do pipeline | 🔜 Em breve |
| Billing e planos (Stripe) | 🔜 Em breve |
| SSO (Google / Microsoft) | 📅 v2 |
| Dashboards analíticos | 📅 v2 |

---

## Stack

| Camada | Tecnologia |
|---|---|
| **Frontend / Backend** | Next.js 16 · React 19 · JavaScript |
| **Banco de dados (DEV)** | PostgreSQL local via Docker |
| **Banco de dados (PRD)** | NeonDB (serverless Postgres) |
| **IA** | Claude Sonnet (Anthropic) |
| **Hospedagem** | Vercel |

Repositório técnico: [lucaskarsten/mibi-core](https://github.com/lucaskarsten/mibi-core)

---

Desenvolvido por **Lucas Karsten**
