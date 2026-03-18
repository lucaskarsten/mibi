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

Times de RH gastam horas respondendo as mesmas perguntas, acompanhando candidatos em planilhas e conduzindo entrevistas sem estrutura. O mibi centraliza tudo isso — e usa IA para automatizar o que pode ser automatizado.

Cada empresa opera em um **ambiente completamente isolado**: dados próprios, agentes configuráveis e histórico exclusivo. Sem compartilhamento entre organizações. Sem risco.

---

## Para quem é

- **Times de RH** que querem escalar o atendimento sem aumentar a equipe
- **Recrutadores** que precisam de mais estrutura e menos retrabalho em cada processo
- **Empresas** que levam privacidade de dados a sério

---

## Assistente de RH com IA

O colaborador pergunta, a IA responde — com contexto real da empresa: benefícios, políticas internas, férias, folha de pagamento. Sem abrir chamado. Sem esperar o RH.

O assistente usa a base de conhecimento configurada pela própria empresa. Cada resposta inclui aviso legal e pode ser copiada com um clique. O colaborador ainda avalia com thumbs up/down — esse feedback alimenta o aprendizado contínuo do agente.

![Conversa com o Assistente de RH](./screenshots/02-chat.png)

Conversas podem ser salvas como **snapshots** com resumo gerado por IA, impressas ou compartilhadas — útil para registros de decisão e processos internos.

![Snapshot da conversa com resumo e opção de impressão](./screenshots/03-impressao-chat.png)

---

## Módulo de Recrutamento

Do processo aberto ao candidato contratado, tudo em um lugar só — com IA analisando em cada etapa.

### Visão geral do pipeline

Acompanhe todos os candidatos ativos, entrevistas conduzidas, taxa de conversão e atividade recente em tempo real.

![Dashboard de recrutamento com pipeline e atividade recente](./screenshots/04-pipeline.png)

### Score Mibi

O mibi pontua candidatos automaticamente em três dimensões: **técnica**, **comportamental** e **holística** — com pesos configuráveis por processo. O score evolui conforme as etapas avançam: triagem, pós-entrevista e análise final por IA. O recrutador vê os melhores perfis de cada processo sem precisar ler currículo por currículo.

![Ranking de candidatos por processo seletivo](./screenshots/05-top-candidatos.png)

### Processos seletivos

Crie e gerencie processos com controle de status: `Aberto`, `Em espera`, `Encerrado` e `Cancelado`. Cada processo tem responsável, histórico completo de candidatos e configuração independente de scoring.

![Lista de processos seletivos com status e candidatos](./screenshots/06-processos-seletivos.png)

### Candidatos

Cadastre, busque e filtre candidatos por status, etapa e data de entrevista. Upload de currículo com análise automática por IA — o sistema extrai dados estruturados e gera um parecer sem entrada manual.

O ciclo de vida de cada candidato percorre: **Em processo → Entrevistado → Contratado / Reprovado / Desistiu**.

![Lista de candidatos com filtros e detalhes](./screenshots/07-candidatos.png)

### Painel de entrevista

Ambiente dedicado para conduzir entrevistas com estrutura. O recrutador vê o perfil completo do candidato, avalia por dimensões (técnica, comunicação, cultura, experiência, motivação) e registra observações em tempo real.

![Painel de entrevista com avaliação por dimensões](./screenshots/08-entrevista.png)

O cronômetro de sessão fica sempre visível. Ao concluir, o candidato avança para `Entrevistado` e o sistema oferece geração de resumo por IA.

---

## Agentes de IA configuráveis

Cada empresa tem seus próprios agentes, baseados em templates globais que evoluem com o uso. O feedback dos colaboradores alimenta um sistema de digest anônimo — os agentes ficam mais inteligentes ao longo do tempo, sem comprometer privacidade.

| Agente                     | O que faz                                                                |
| -------------------------- | ------------------------------------------------------------------------ |
| **Assistente de RH**       | Responde dúvidas sobre benefícios, férias, políticas e folha de pagamento |
| **Assistente de Recrutamento** | Analisa candidatos, sugere perguntas e gera pareceres estruturados   |
| **Assistente do Recrutador** | Apoia o recrutador durante entrevistas com contexto de preferências   |
| **Digest do Recrutador**   | Processa preferências do recrutador em texto livre e as injeta nos demais agentes |
| **Arena** *(em breve)*     | Compara candidatos lado a lado com análise aprofundada por IA            |

---

## Multi-tenancy real

Cada empresa possui um **schema dedicado no PostgreSQL**. Não há camada de compartilhamento — os dados de uma organização jamais se misturam com os de outra.

```
empresa_a.rh.app  →  schema isolado da empresa A
empresa_b.rh.app  →  schema isolado da empresa B
```

Privacidade de dados por arquitetura, não por configuração.

---

## Compliance e LGPD

O mibi é **operador de dados** nos termos da LGPD — as empresas clientes são as controladoras. Essa distinção define as obrigações de cada parte.

- **LGPD compliant** — exportação e anonimização de dados disponíveis para colaboradores e candidatos
- **Aceite de termos** com versionamento no registro
- **Geo-blocking** para regiões sem adequação regulatória (EU/EEA/UK)
- **Audit log** de operações de IA e decisões sobre dados
- **Disclaimer de IA** em todas as respostas geradas — toda decisão automatizada é passível de revisão humana
- Documentação legal completa: [mibi-legal](https://github.com/lucaskarsten/mibi-legal)

---

## Acesse a demo

|              |                                                                 |
| ------------ | --------------------------------------------------------------- |
| **URL**      | https://demonstracao.rh.lucaskarsten.com.br                     |
| **Admin**    | `ana@demonstracao.com` — gestão de equipe, agentes e configurações |
| **Membro**   | `rafael@demonstracao.com` — chat com assistente de RH           |
| **Recrutador** | `beatriz@demonstracao.com` — processos, candidatos e entrevistas |
| **Senha**    | `123456`                                                        |

> Todos os dados do ambiente de demonstração — nomes, vagas, candidatos, métricas e conversas — são **inteiramente fictícios** e gerados para fins de teste.

---

## Roadmap

| Funcionalidade                          | Status            |
| --------------------------------------- | ----------------- |
| Assistente de RH com IA                 | ✅ Em produção    |
| Módulo de recrutamento                  | ✅ Em produção    |
| Painel de entrevista                    | ✅ Em produção    |
| Upload e análise de currículo por IA    | ✅ Em produção    |
| Snapshots de conversa com resumo por IA | ✅ Em produção    |
| Perfil de preferências do recrutador    | ✅ Em produção    |
| Score Mibi (scoring por dimensões)      | ✅ Em produção    |
| LGPD e compliance                       | ✅ Em produção    |
| Mobile (chat, recrutamento, equipe)     | ✅ Em produção    |
| Arena — comparação de candidatos por IA | 🔜 Em breve      |
| Kanban do pipeline                      | 🔜 Em breve      |
| Billing e planos (Stripe)               | 🔜 Em breve      |
| Mobile completo (agentes, config)       | 🔜 Em breve      |
| SSO (Google / Microsoft)                | 📅 v2            |
| Dashboards analíticos                   | 📅 v2            |
| Onboarding de colaboradores             | 📅 v2            |

---

## Stack

| Camada               | Tecnologia                          |
| -------------------- | ----------------------------------- |
| **Frontend / Backend** | Next.js 16 · React 19 · JavaScript |
| **Banco (dev)**      | PostgreSQL local via Docker         |
| **Banco (produção)** | NeonDB (serverless Postgres)        |
| **IA**               | Claude Sonnet (Anthropic)           |
| **Hospedagem**       | Vercel                              |

Repositório técnico: [lucaskarsten/mibi-core](https://github.com/lucaskarsten/mibi-core)

---

Desenvolvido por **Lucas Karsten**
