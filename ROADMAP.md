# Mibi — Roadmap do Produto

> Módulo de Inteligência Binária Interna
> Plataforma de RH com IA para empresas — ATS + People Platform

---

## Visão geral

O Mibi é um SaaS B2B multi-tenant com arquitetura API-first, onde cada empresa opera em schema PostgreSQL isolado. A IA (Claude, Anthropic) atua como camada de suporte à decisão humana — nunca como decisor final.

**Evolução:** De plataforma de recrutamento com IA para **ATS completo com autoatendimento do colaborador e onboarding integrado**, onde o lifecycle é contínuo: candidato → contratado → onboarding → colaborador — tudo num sistema só.

**Diferencial competitivo:** Nenhum ATS no Brasil combina recrutamento com IA nativa + banco de talentos inteligente + onboarding completo + autoatendimento do colaborador + analytics de satisfação num produto multi-tenant com isolamento real de dados.

---

## O que NÃO construir (integrar via parceiro)

| Área | Motivo | Estratégia |
|---|---|---|
| Folha de pagamento / cálculos trabalhistas | Complexidade regulatória (CLT, eSocial, INSS, IRRF, FGTS) | Integrar com Convenia, ADP, Domínio |
| Registro Eletrônico de Ponto (REP) | Regulamentação MTE (Portaria 671) | Integrar com Tangerino, Pontotel |
| Benefícios (billing de operadoras) | Cada benefício tem operadora própria | Apenas informativo + IA para dúvidas |
| Assinatura digital de contratos | Soluções maduras existem | Integrar com DocuSign, Clicksign |

**Princípio:** Integrar, não reinventar. O Mibi é a camada de experiência e inteligência.

---

## Fase 1 — Estabilização do Core

**Objetivo:** Garantir que o produto base está sólido, refatorado e com a identidade visual definitiva antes de abrir para o mercado.

### Módulo de Recrutamento (refatoração v5)

- Ciclo de vida do candidato completo: Em processo → Entrevistado → Contratado / Reprovado / Desistiu
- Estados de processo seletivo: aberto, em espera, cancelado, encerrado
- Migração para UUID em todas as entidades
- Entidade `person` para vinculação cross-processo dentro do mesmo tenant
- Painel de entrevistas: notas, perguntas, tempo de sessão
- Análise de candidatos por IA com recomendações
- Score Mibi composto (técnico + comportamental + holístico) com pesos configuráveis por processo
- Placeholder `person_id` nullable em `collaborator` (reservado para onboarding)

### Identidade Visual (Inteligência Acolhedora)

- Paleta: teal primary, amber/gold accent, slate-blue dark mode
- Tipografia: Plus Jakarta Sans (display) + Figtree (body)
- `theme.css` como fonte única de design tokens (light + dark mode)
- Componentes migrados de valores hardcoded para custom properties

### Agentes de IA

- Agentes configuráveis por empresa: assistente RH e assistente de recrutamento
- Prompt engineering com tags XML, 6+ few-shot examples, anti-hallucination, fallback phrases
- Proteção contra prompt injection
- Protocolos para situações sensíveis (assédio, demissão, saúde, denúncias)
- Variável `{company_name}` para multi-tenancy
- Limites de escopo: informa — não dá conselho jurídico, não calcula, não resolve conflitos

### AI Provider Layer

- Interface unificada (`lib/ai/provider.js`) para abstração de provider
- Adapter Anthropic (refatorar código atual)
- Seleção por `process.env.AI_PROVIDER`
- Preparação para fallback (OpenAI, Gemini) sem reescrever produto

---

## Fase 2 — Compliance e LGPD

**Objetivo:** Atender todos os requisitos legais obrigatórios antes do beta aberto. O Mibi é operador de dados (LGPD); as empresas clientes são controladoras.

### Documentos obrigatórios

- Termos de Uso (contrato B2B com cláusula explícita sobre IA)
- Política de Privacidade (LGPD compliant, com indicação de DPO)
- Legal Disclaimer para IA (acessível nas telas de interação com agentes)
- EULA / Licença Proprietária (código fechado)
- Política de Cookies
- DPA — Data Processing Agreement (template para assinatura com cada cliente)

### Implementação técnica

- Endpoints de direitos do titular (LGPD): exportação e exclusão de dados
- Retenção de dados configurável por tenant (conforme spec v5)
- Log de auditoria para decisões de IA (LGPD Art. 20 — direito à revisão de decisões automatizadas)
- Componente `AIDisclaimer` nas interfaces de IA (bloqueante — exigência Anthropic Usage Policy)
- Human-in-the-loop enforcement: scores/recomendações de IA com etapa de aprovação humana na UI
- Regras LGPD nos prompts dos agentes (não ecoar dados sensíveis compartilhados espontaneamente)

### Conformidade Anthropic

- Disclosure obrigatório em toda interface com output de IA (High-Risk Use Case: Employment)
- DPA do Mibi lista Anthropic como subprocessador com SCCs
- Política de Privacidade documenta transferência internacional (EUA) — LGPD Art. 33
- Plano de Resposta a Incidentes formalizado (48h Anthropic → 72h clientes)
- Anti-bias rules nos prompts (não inferir características protegidas)

### Uso de dados para melhoria da IA

- Pipeline de extração de insights anonimizados/agregados: permitido
- Fine-tuning ou treino com dados pessoais sem consentimento explícito: proibido
- Arquitetura de dois pipelines: insights anônimos + feedback opt-in

---

## Fase 3 — Comercialização

**Objetivo:** Permitir que empresas se cadastrem, assinem e paguem de forma autônoma (self-service).

### Modelo de planos

| | Free | Starter | Pro | Enterprise |
|---|---|---|---|---|
| Colaboradores | 5 | 25 | 100 | Ilimitado |
| Agentes IA | — | 1 | Todos | Customizados |
| Processos seletivos | — | 2 ativos | Ilimitado | Ilimitado |
| Painel de entrevistas | — | — | ✓ | ✓ |
| Score Mibi + Arena | — | — | ✓ | ✓ |
| Banco de talentos | — | — | ✓ | ✓ |
| Onboarding | — | Básico | Completo | Customizado |
| Portal do colaborador | — | Básico | Completo | Completo |
| Analytics | — | Básico | Completo | Custom + API |
| SSO | — | — | — | ✓ |
| White-label | — | — | — | ✓ |
| Suporte | — | E-mail | Prioritário | Dedicado |

### Billing

- Gateway: Stripe (suporta BRL, Pix, cartão, boleto)
- Ciclo: mensal + anual (20% desconto)
- Trial: 7 dias no Pro, com cartão
- Upgrade imediato com prorate; downgrade ao final do ciclo
- Cancelamento ao final do ciclo, dados mantidos por 30 dias (portabilidade LGPD)
- Enterprise: contratação direta, NF + boleto/transferência

### Implementação

- Integração Stripe Billing (plans, subscriptions, webhooks)
- Limites de operações por plano com controle server-side
- Portal do cliente para gestão de assinatura
- Páginas públicas: pricing, comparação de planos

---

## Fase 4 — Features Avançadas de Recrutamento

**Objetivo:** Diferenciar o produto com funcionalidades de alto valor que justificam o tier Pro.

### Recrutamento inteligente

- Score Mibi progressivo (evolui conforme etapas: triagem → pós-entrevista → análise IA)
- Fit logístico: localização, salário, modalidade, disponibilidade
- Comparação de candidatos por IA — Arena (side-by-side com breakdown de scores)
- Refatoração do prompt do assistente de recrutamento (viés, output estruturado, confidencialidade)

### Painel de entrevistas em tempo real

- Sessão de entrevista ao vivo com notas colaborativas
- Timer de sessão
- Sugestões de perguntas pela IA em tempo real

### Banco de Talentos Inteligente

O banco de talentos é a **memória de longo prazo do recrutamento**. Todo candidato que já passou pelo Mibi — aprovado, reprovado ou desistente — alimenta um pool pesquisável com contexto completo.

**Core:**

- Candidatos não selecionados permanecem no banco automaticamente (com consentimento LGPD e retenção configurável)
- Perfil no banco preserva: dados pessoais, CV, Score Mibi de cada processo, pareceres de entrevista, recomendação, tags
- Busca avançada: por skills, senioridade, score, área, data, tags
- Filtro por disponibilidade para recontato (respeitando `expires_at` LGPD)

**Match inteligente (IA ativa ao abrir vaga nova):**

- Ao criar um novo processo seletivo, o Mibi automaticamente busca no banco de talentos e apresenta candidatos compatíveis
- Ranking por relevância: combinação de Score Mibi histórico + aderência ao novo perfil da vaga
- Para cada candidato sugerido, a IA gera um resumo: "Participou do processo [X] em [data]. Score Mibi: [N]. Pontos fortes: [A, B]. Motivo de não contratação: [C]. Adequação à nova vaga: [análise]."
- O recrutador pode revisar a entrevista antiga completa (notas, Q&A, parecer, score breakdown) direto do card do candidato
- Com um clique: adicionar o candidato ao novo processo (status "Em processo")
- O candidato recebe notificação automática de que foi considerado para uma nova oportunidade
- O recrutador agenda entrevista direto pelo sistema

**Fluxo completo:**

```
Nova vaga criada
  → IA busca no banco de talentos
  → Lista candidatos por score de match
  → Recrutador revisa histórico + resumo IA
  → Seleciona candidatos promissores
  → Candidatos adicionados ao novo processo
  → Notificação automática ao candidato
  → Recrutador agenda entrevista
  → Processo segue normalmente
```

**Regras:**

- Match inteligente é sugestão — recrutador decide (human-in-the-loop)
- Candidatos anonimizados não aparecem nas buscas
- Candidatos com `expires_at` vencido são removidos automaticamente do banco ativo
- Cross-processo: a entidade `person` vincula o candidato entre processos do mesmo tenant, acumulando histórico
- Score de match é gerado pela IA considerando a nova vaga, não apenas o score antigo — um candidato "reprovado" para engenharia pode ser excelente para produto

---

## Fase 5 — Onboarding Completo

**Objetivo:** O candidato contratado faz todo o onboarding pelo Mibi — do aceite da oferta ao primeiro dia produtivo. O Mibi é a ferramenta de onboarding tanto para o RH quanto para o novo colaborador.

### Fluxo de onboarding

```
Candidato aceita oferta
  → Status: "Contratado"
  → person vinculada a collaborator (person_id ativado)
  → Onboarding iniciado automaticamente
  → Novo colaborador recebe acesso ao portal de onboarding
  → Checklist guiado com etapas
  → Agente de onboarding disponível para dúvidas
  → RH acompanha progresso em dashboard
  → Onboarding concluído → colaborador ativo
```

### Para o novo colaborador (portal de onboarding)

- Tela dedicada de boas-vindas com nome da empresa, mensagem do gestor e foto do time
- Checklist interativo de etapas (o colaborador vai marcando conforme completa):
  - Aceitar termos de uso da plataforma
  - Preencher dados pessoais (endereço, contato de emergência, dados bancários, dependentes)
  - Upload de documentos admissionais (RG, CPF, CTPS, comprovante de endereço, foto)
  - Agendar/confirmar exame admissional
  - Ler e aceitar políticas da empresa (código de conduta, política de home office, etc.)
  - Receber credenciais e acessos (email corporativo, Slack, sistemas)
  - Completar treinamento introdutório (vídeos, documentos, quiz)
  - Conhecer a equipe (organograma interativo, quem é quem)
  - Agendar 1:1 com gestor
- Barra de progresso visível ("Você está 60% concluído")
- Prazo para cada etapa (configurável pelo RH)
- Notificações e lembretes automáticos para etapas pendentes

### Agente de Onboarding (IA)

- Agente dedicado com base de conhecimento específica de onboarding da empresa
- O colaborador pergunta: "Onde fico sentado?", "Qual é o dress code?", "Como funciona o VR?", "Quem é meu gestor?", "Como acesso o email corporativo?"
- Base de conhecimento configurável por empresa (FAQ de onboarding, guia do novo colaborador)
- Protocolos: não dá informação que não está na base, orienta para RH quando não sabe
- Após os primeiros 30 dias, o agente de onboarding transiciona para o assistente de RH regular

### Para o RH (dashboard de onboarding)

- Visão de todos os onboardings em andamento
- Status por colaborador: quais etapas completou, quais estão pendentes, quais estão atrasadas
- Alertas automáticos: "3 colaboradores com documentos pendentes há mais de 5 dias"
- Checklist de tarefas do RH por admissão:
  - Criar conta no sistema de folha
  - Solicitar equipamento (notebook, crachá)
  - Configurar acessos (email, sistemas internos)
  - Enviar kit de boas-vindas
  - Agendar integração com equipe
- Templates de onboarding por cargo/departamento (engenharia tem etapas diferentes de vendas)
- Métricas: tempo médio de onboarding, taxa de conclusão, etapas com maior atraso
- Pesquisa de satisfação pós-onboarding (30 dias): "Como foi sua experiência de integração?"

### Dados e continuidade

- A entidade `person` garante que todo o histórico do candidato (CV, entrevistas, score) está disponível no perfil do colaborador
- O recrutador que entrevistou pode deixar notas para o gestor que vai receber
- Documentos enviados durante o onboarding ficam no perfil do colaborador (com retenção LGPD)
- Se o colaborador já estava no banco de talentos, seu histórico completo está vinculado
- Lifecycle completo: candidatura → entrevistas → contratação → onboarding → colaborador ativo — tudo num sistema, sem retrabalho

---

## Fase 6 — Portal do Colaborador (autoatendimento)

**Objetivo:** O colaborador resolve 80% das dúvidas de RH sem abrir chamado.

### Gestão de férias

- Saldo de férias visível no painel
- Solicitação de férias pelo sistema (período, tipo: integral, fracionada, abono)
- Fluxo de aprovação: colaborador → gestor → RH
- Calendário de férias da equipe
- Regras configuráveis: antecedência mínima, blackout periods, limite simultâneo por time
- IA responde "quando posso pedir férias?" com base nas regras e no saldo real

### Atestados e afastamentos

- Upload de atestado (foto do celular ou PDF)
- Classificação automática: tipo, período, CID (opcional)
- Fluxo: colaborador envia → RH valida → registro no histórico
- IA orienta: "como entregar atestado?", "até quando tenho prazo?"
- Alerta ao RH quando afastamento excede 15 dias (encaminhamento INSS)

### Informações de pagamento (via integração)

- Visualização do holerite (integração com folha)
- Próxima data de pagamento
- Detalhamento de descontos (INSS, IRRF, VT, VR, plano de saúde)
- IA responde "quanto vou receber?", "por que meu salário foi menor?", "o que é esse desconto?"
- Histórico de holerites (últimos 12 meses)
- Informe de rendimentos anual

### Solicitações e documentos

- Solicitar declaração de vínculo, carta de recomendação, comprovante de renda
- Status da solicitação (pendente, pronto para download)
- Upload de documentos (atualização cadastral, dependentes)

### Agente do Colaborador (IA)

- Canal direto entre colaborador e IA da empresa
- Consultas sobre benefícios, férias, folha, políticas internas
- Escopo restrito ao que a empresa configurou
- Disclosure obrigatório de IA no início de cada sessão

---

## Fase 7 — ATS Completo

**Objetivo:** Paridade com Ashby/Greenhouse, com o diferencial de IA nativa e banco de talentos inteligente.

### Página de vagas (career page)

- Página pública customizável por empresa (logo, cores, descrição, cultura)
- URL: `empresa.mibi.app.br/vagas` ou domínio custom
- SEO otimizado, mobile-first
- Candidato se cadastra e aplica diretamente
- Formulário configurável por vaga

### Parsing de currículo avançado

- Upload de CV → extração automática (IA): nome, email, experiências, formação, skills
- Preenchimento automático do perfil
- Suporte a PDF, DOCX e LinkedIn URL

### Pipeline visual (Kanban)

- Kanban drag-and-drop por processo seletivo
- Colunas configuráveis (etapas do processo)
- Ações em batch: mover múltiplos, enviar email em massa
- Filtros: score, status, data, recrutador, tags

### Agendamento de entrevistas

- Integração com Google Calendar e Outlook
- Self-scheduling: candidato escolhe horário via link
- Confirmação e lembretes automáticos
- Suporte a entrevistas em painel

### Comunicação automatizada

- Templates de email por etapa (recebimento, agendamento, feedback, rejeição, oferta)
- Variáveis dinâmicas (nome, vaga, recrutador, data)
- Envio automático ao mover de etapa
- Email de rejeição com feedback construtivo (gerado por IA, revisão humana obrigatória)

### Oferta e contratação

- Geração de proposta dentro do sistema
- Fluxo de aprovação (recrutador → gestor → RH → diretoria)
- Candidato aceita/rejeita online
- Ao aceitar: transição automática para onboarding (Fase 5)
- Checklist de admissão

### Indicações (referral)

- Colaborador indica via link pessoal
- Tracking de indicações
- Programa de incentivo configurável

---

## Fase 8 — Analytics e Satisfação

**Objetivo:** Dashboards acionáveis para RH, gestores e diretoria. Satisfação como métrica de primeira classe.

### Analytics de recrutamento

- Time-to-hire e time-to-fill
- Taxa de conversão por etapa do funil
- Source effectiveness (career page, indicação, LinkedIn, banco de talentos)
- Custo por contratação (estimativa)
- Offer acceptance rate
- Drop-off rate por etapa
- Score Mibi médio por processo
- **Banco de talentos: taxa de reaproveitamento** (% de contratações que vieram do banco vs. candidatos novos)

### Satisfação de candidatos

- Pesquisa NPS/CSAT enviada após o processo (aprovados e rejeitados)
- Perguntas configuráveis: clareza, comunicação, tempo de resposta, respeito
- Score médio por processo, recrutador e período
- IA gera insights: "processos do time de engenharia têm NPS 30% menor — principal queixa: demora"

### Satisfação de colaboradores

- Pulse surveys configuráveis (semanal, quinzenal, mensal)
- eNPS (Employee Net Promoter Score)
- Respostas anônimas, agregação por time (mínimo 5 respostas para exibir)
- Tendências: "satisfação de vendas caiu 15% nos últimos 3 meses"
- IA interpreta e sugere ações
- **Pesquisa pós-onboarding (30 dias):** "Como foi sua integração?"

### Analytics de IA

- Perguntas mais frequentes (por empresa e global)
- Taxa de resolução vs. fallback
- Satisfação com respostas (thumbs up/down)
- Tópicos não cobertos (oportunidade de melhoria da base)

### Dashboards executivos

- Consolidado: headcount, turnover, custo de contratação, eNPS, time-to-hire
- Comparação período a período
- Exportação em PDF
- Filtros: departamento, período, tipo de vaga

---

## Fase 9 — Enterprise

**Objetivo:** Atender requisitos de grandes empresas.

### Autenticação

- SSO (SAML / OpenID Connect)
- Provisionamento de usuários via SCIM (opcional)

### Personalização

- White-label (logo, cores, domínio customizado)
- Onboarding assistido com implantação personalizada
- SLA contratual com suporte dedicado

### Gestão avançada

- Organograma visual (quem reporta a quem)
- Gestão de times e departamentos
- Avaliação de desempenho (autoavaliação + gestor + 360)
- Plano de desenvolvimento individual (PDI)
- Métricas por time: headcount, turnover, eNPS

---

## Fase 10 — Integrações

**Objetivo:** Conectar com ecossistema sem construir DP.

### Folha de pagamento

- MVP: importação CSV/XLSX (empresa exporta do sistema de folha)
- API: Convenia, ADP, Domínio, BambooHR
- Leitura: holerite, saldo férias, descontos
- Escrita: nova admissão, afastamento, férias aprovadas
- Webhook: notificação quando folha é processada

### Recrutamento e comunicação

- Google Calendar + Outlook (agendamento)
- LinkedIn (Easy Apply, profile import)
- Indeed, Catho, Infojobs (post de vagas)
- WhatsApp Business API (comunicação com candidato)
- Slack/Teams (notificações)
- Zapier/Make (automação genérica)

### API pública

- REST API documentada (Swagger)
- Webhooks: candidato mudou status, entrevista concluída, oferta aceita, colaborador admitido
- API keys por tenant, rate limiting por plano

---

## Fase 11 — Experiência do Candidato

**Objetivo:** Processo seletivo transparente e positivo.

### Portal do candidato

- Área logada com status em tempo real
- Timeline visual: "Você está na etapa Entrevista Técnica"
- Upload de documentos adicionais
- Chat assíncrono com recrutador

### Feedback automático

- Feedback construtivo por IA para candidatos rejeitados (opt-in da empresa)
- Baseado no Score Mibi: "Seu perfil técnico está forte, mas identificamos gap em liderança"
- Revisão humana obrigatória (compliance Anthropic)
- Convite para banco de talentos: "Podemos guardar seu perfil para oportunidades futuras?"

### Chatbot do candidato

- IA responde dúvidas sobre o processo: "quantas etapas?", "quando receberei retorno?"
- Escopo limitado ao processo do candidato
- Disclosure obrigatório de IA

---

## Fase 12 — Escala e Observabilidade

**Objetivo:** Preparar a infraestrutura para crescimento sustentável.

### Jobs assíncronos

- Trigger.dev ou Inngest para processamento pesado (análise de CVs, match banco de talentos, relatórios)
- Desacoplar operações longas do request/response cycle

### Observabilidade

- Sentry para erros e performance monitoring
- Logs estruturados (Axiom ou Logtail) integrados com Vercel

### E-mail transacional

- Resend para convites, notificações de processos, alertas, comunicação com candidatos

### Infraestrutura

- Avaliação de limites do Neon conforme crescimento de tenants
- Estratégia de backup e disaster recovery por tenant
- Rate limiting e proteção contra abuso da API

---

## Stack atual

| Camada | Tecnologia |
|---|---|
| Frontend + Backend | Next.js (Pages Router, JavaScript) |
| Hosting | Vercel + Git CI |
| Banco de dados | PostgreSQL (Neon em produção, local em dev) |
| Multi-tenancy | Schema isolado por empresa |
| IA | Anthropic Claude API (com AI Provider Layer para fallback) |
| Design tokens | `theme.css` (custom properties) + Tailwind (utilities) |
| API | API-first com Swagger |
| Proxy | `proxy.js` (sem middleware) |

---

## Princípios

- **Multi-tenancy é inegociável:** zero vazamento de dados entre tenants em todas as camadas.
- **LGPD molda a arquitetura:** retenção configurável, consentimento explícito, direitos do titular implementados.
- **IA é suporte, não decisor:** toda decisão automatizada é passível de revisão humana.
- **Integrar, não reinventar:** DP, folha, ponto e benefícios financeiros são integrados via parceiros.
- **IA em cada touchpoint:** candidato, colaborador, recrutador e gestor — todos assistidos por IA com contexto real da empresa.
- **Candidato vira colaborador:** lifecycle contínuo via entidade `person`. Sem retrabalho.
- **Satisfação é métrica:** NPS de candidato e eNPS de colaborador são métricas de primeira classe.
- **`theme.css` é a fonte da verdade:** mudanças visuais fluem dos tokens para os componentes.
- **Commits pequenos e focados:** escopo incremental, não varreduras amplas.
- **Auditoria antes de mudança:** em refatorações, levantar o estado atual antes de alterar.

---

## Horizonte

| Fase | Nome | Horizonte |
|---|---|---|
| 1 — Core | Recrutamento, IA, identidade visual | Em andamento |
| 2 — Compliance | LGPD, documentos legais, Anthropic ToS | Em andamento |
| 3 — Comercialização | Stripe, planos, self-service | 2026 Q2 |
| 4 — Recrutamento avançado | Arena, entrevista real-time, banco de talentos | 2026 Q2–Q3 |
| 5 — Onboarding | Checklist, portal, agente, fluxo admissional | 2026 Q3 |
| 6 — Portal colaborador | Férias, atestados, holerite, documentos | 2026 Q3–Q4 |
| 7 — ATS completo | Career page, Kanban, agendamento, oferta | 2026 Q4–2027 Q1 |
| 8 — Analytics | Dashboards, NPS, eNPS, analytics IA | 2027 Q1–Q2 |
| 9 — Enterprise | SSO, white-label, avaliação de desempenho | 2027 Q2 |
| 10 — Integrações | Folha, calendário, LinkedIn, WhatsApp, API | 2027 Q1–Q2 |
| 11 — Experiência candidato | Portal, feedback IA, chatbot, banco de talentos público | 2027 Q3 |
| 12 — Escala | Jobs async, Sentry, Resend, infra | Contínuo |

---

## Status

| Fase | Estado |
|---|---|
| 1 — Core | Em andamento |
| 2 — Compliance | Em andamento (documentos redigidos, implementação técnica pendente) |
| 3 — Comercialização | Modelo definido, implementação pendente |
| 4 — Recrutamento avançado | Em desenvolvimento (Arena) |
| 5 — Onboarding | Planejado (entidade `person` e `person_id` já reservados) |
| 6 — Portal colaborador | Planejado |
| 7 — ATS completo | Planejado |
| 8 — Analytics | Planejado |
| 9 — Enterprise | Planejado |
| 10 — Integrações | Planejado |
| 11 — Experiência candidato | Planejado |
| 12 — Escala | Planejado |

---

*Última atualização: março de 2026*
