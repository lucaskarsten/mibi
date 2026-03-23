# Mibi — Roadmap do Produto

> Módulo de Inteligência Binária Interna  
> Plataforma de RH com IA para empresas B2B  
> **Status:** Open Beta Q2 2026

---

## Sumário Executivo

O Mibi é uma plataforma SaaS B2B de gestão de RH potencializada por IA, com foco em recrutamento inteligente e gestão de colaboradores. Arquitetura multi-tenant API-first com schema PostgreSQL isolado por empresa, garantindo compliance LGPD e zero vazamento de dados entre clientes.

**Diferenciais:**
- Agentes de IA configuráveis por empresa (assistente RH + assistente de recrutamento)
- Score Mibi composto (técnico + comportamental + holístico) para avaliação de candidatos
- Painel de entrevistas com análise em tempo real
- 100% compliance LGPD desde o design

**Stack:** Next.js, PostgreSQL (Neon), Anthropic Claude API, Vercel, design system proprietário (Inteligência Acolhedora).

---

## Fase 1 — Estabilização do Core
**Status:** 85% concluído | **ETA Open Beta:** Abril 2026

### ✅ Concluído

**Identidade Visual (Inteligência Acolhedora)**
- Paleta definida: teal primary (#0D9488), amber/gold accent (#F59E0B), slate-blue dark mode
- Tipografia: Plus Jakarta Sans (display) + Figtree (body)
- `theme.css` implementado como fonte única de design tokens (light + dark mode)
- Preview interativo de dashboard com toggle dark/light
- Configuração Claude Code para migração de componentes

**Refatoração do Módulo de Recrutamento (v5)**
- Especificação técnica completa (16 páginas) aprovada
- Ciclo de vida do candidato: Em processo → Entrevistado → Contratado/Reprovado/Desistiu
- Estados de processo: aberto, em_espera, cancelado, encerrado
- Migração para UUID planejada
- Entidade `person` especificada para vinculação cross-processo
- Score Mibi com pesos configuráveis por processo
- Placeholder `person_id` em `collaborator` reservado para onboarding futuro

**Documentação Legal (LGPD)**
- Termos de Uso (B2B com cláusula IA)
- Política de Privacidade (LGPD compliant)
- Legal Disclaimer para IA
- EULA / Licença Proprietária
- Política de Cookies
- Template DPA (Data Processing Agreement)
- Componente `AIDisclaimer` React desenvolvido

### 🔄 Em andamento

**Implementação da refatoração v5**
- Migração de banco de dados (UUID, entidade `person`, retenção configurável)
- Refatoração de componentes UI para `theme.css`
- Painel de entrevistas: notas, perguntas, cronômetro de sessão
- Análise de candidatos por IA com recomendações estruturadas

**Agentes de IA**
- Prompts com tags XML, 6+ few-shot examples, regras anti-hallucination
- Proteção contra prompt injection implementada
- Protocolos para situações sensíveis (assédio, demissão, saúde, denúncias)
- Variável `{company_name}` para multi-tenancy
- Limites de escopo documentados: informa, não aconselha juridicamente

### 📋 Pendente (Q2 2026)

- Refatoração do prompt do assistente de recrutamento (mitigação de viés, output estruturado)
- Migração completa de componentes para design system
- Testes de carga multi-tenant
- Demo pública atualizada em `demonstracao.rh.lucaskarsten.com.br`

---

## Fase 2 — Compliance e LGPD
**Status:** 60% concluído | **ETA:** Maio 2026

### ✅ Concluído

- Todos os documentos legais obrigatórios redigidos
- Arquitetura de dados desenhada com LGPD em mente
- Retenção configurável por tenant especificada (v5)
- Componente `AIDisclaimer` para interfaces de IA

### 🔄 Em andamento

**Implementação técnica**
- Endpoints de direitos do titular (LGPD Art. 18):
  - Exportação de dados pessoais em formato estruturado
  - Exclusão definitiva de dados (right to be forgotten)
- Log de auditoria para decisões automatizadas (LGPD Art. 20)
- Regras LGPD nos prompts dos agentes (não ecoar dados sensíveis)

### 📋 Pendente

- Validação jurídica dos documentos legais
- Testes de conformidade dos endpoints LGPD
- Política de uso de dados para melhoria da IA:
  - Pipeline de insights anonimizados (permitido)
  - Pipeline de feedback opt-in para fine-tuning (consentimento explícito)
- Integração com Anthropic ToS validation
- Resolução de licença jszip (eleição MIT)

---

## Fase 3 — Comercialização
**Status:** Planejado | **ETA:** Junho 2026

### Modelo de Planos

| Plano | Free | Starter | Pro | Enterprise |
|---|---|---|---|---|
| **Tokens/mês** | 50k | 500k | 2M | Customizado |
| **Funcionários** | 5 | 25 | Ilimitado | Ilimitado |
| **Agentes IA** | 0 | 1 (RH ou Recrutamento) | Todos | Customizados |
| **Processos seletivos ativos** | — | 2 | Ilimitado | Ilimitado |
| **Painel de entrevistas** | — | — | ✓ | ✓ |
| **Score Mibi** | — | Básico | Completo | Completo + Custom |
| **SSO** | — | — | — | ✓ |
| **Suporte** | — | E-mail (48h) | Prioritário (12h) | Dedicado (SLA) |
| **White-label** | — | — | — | ✓ |
| **Preço (BRL/mês)** | Grátis | R$ 297 | R$ 997 | Sob consulta |

**Descontos:** 15% mensal, 20% anual

### Billing Stripe

**Implementação planejada:**
- Gateway: Stripe (Pix, cartão, boleto)
- Trial: 14 dias no Pro sem cartão obrigatório
- Upgrade: imediato com prorate
- Downgrade: ao final do ciclo
- Cancelamento: dados mantidos por 30 dias (portabilidade LGPD)
- Tokens adicionais: compra avulsa (top-up) no Starter e Pro
- Enterprise: contrato direto, NF + boleto/transferência, setup fee opcional

**Tarefas:**
- Integração Stripe Billing (plans, subscriptions, webhooks)
- Controle server-side de limites por plano
- Portal do cliente (Stripe Customer Portal)
- Páginas públicas: /pricing, /plans

---

## Fase 4 — Features Avançadas
**Status:** Planejado | **ETA:** Q3-Q4 2026

### Recrutamento Inteligente

**Score Mibi Progressivo**
- Evolui conforme etapas: triagem → entrevista → análise IA
- Componentes: técnico (hard skills), comportamental (soft skills), holístico (fit cultural)
- Pesos configuráveis por processo seletivo
- Fit logístico: localização, salário, modalidade, disponibilidade

**Comparação de Candidatos**
- Side-by-side com breakdown detalhado de scores
- Análise diferencial por IA
- Exportação de relatórios comparativos

**Refatoração de Prompts**
- Mitigação de viés (gender, racial, age bias)
- Output estruturado (JSON schemas)
- Confidencialidade reforçada

### Painel de Entrevistas em Tempo Real

- Sessão ao vivo com notas colaborativas multi-usuário
- Timer de sessão com alertas
- Sugestões de perguntas contextuais pela IA
- Transcrição automática (opcional, com consentimento)

### Agente do Colaborador

- Canal direto colaborador ↔ IA da empresa
- Consultas sobre: benefícios, férias, folha de pagamento, políticas internas
- Escopo restrito ao knowledge base configurado pela empresa
- Logs de auditoria para compliance

---

## Fase 5 — Enterprise
**Status:** Planejado | **ETA:** 2027

### Autenticação Enterprise

- SSO via SAML 2.0 / OpenID Connect
- Provisionamento SCIM (opcional)
- MFA obrigatório configurável
- Auditoria de acessos

### Analytics e Dashboards

**Métricas de uso:**
- Tokens consumidos por empresa/período
- Conversas com agentes IA
- Satisfação (thumbs up/down)

**Métricas de recrutamento:**
- Time-to-hire médio
- Funil de candidatos (conversão por etapa)
- Score Mibi médio por vaga/período
- Taxa de aprovação vs rejeição

**Exportação:**
- PDF, CSV, Excel
- Agendamento de relatórios

### Personalização

- White-label completo: logo, cores, domínio customizado
- Onboarding assistido com implantação dedicada
- SLA contratual (99.9% uptime)
- Suporte dedicado (Slack/Teams channel)

### Módulo de Onboarding

- Fluxo guiado para novos colaboradores
- Vinculação `collaborator` → `person` (campo reservado desde Fase 1)
- Agente de onboarding com conteúdo customizável
- Checklist de tarefas (documentos, treinamentos, acessos)

---

## Fase 6 — Escala e Observabilidade
**Status:** Planejado | **ETA:** 2027

### Jobs Assíncronos

- **Trigger.dev** ou **Inngest** para processamento pesado:
  - Análise de CVs em lote
  - Geração de relatórios complexos
  - Notificações agendadas
- Desacoplar operações longas do request/response cycle
- Queue management com retry e dead-letter queue

### Observabilidade

- **Sentry:** error tracking e performance monitoring
- **Axiom** ou **Logtail:** logs estruturados integrados com Vercel
- Métricas de negócio: MAU, token usage, revenue per tenant
- Alertas proativos (downtime, spike de erros, limites atingidos)

### E-mail Transacional

- **Resend** para:
  - Convites de funcionários
  - Notificações de processos seletivos
  - Alertas do sistema
  - Relatórios agendados
- Templates branded com design system

### Infraestrutura

- Avaliação de limites Neon conforme crescimento de tenants
- Estratégia de backup e disaster recovery por tenant
- Rate limiting e proteção contra abuso da API
- CDN para assets estáticos
- Cache distribuído (Redis/Upstash) para queries frequentes

---

## Stack Técnica

| Camada | Tecnologia | Justificativa |
|---|---|---|
| **Frontend + Backend** | Next.js (Pages Router, JavaScript) | Full-stack, SEO-friendly, Vercel-native |
| **Proxy** | `proxy.js` | Sem middleware (recomendação Next.js recente) |
| **Hosting** | Vercel + Git CI | Deploy automático, edge functions |
| **Banco de dados** | PostgreSQL (Neon PRD / local dev) | ACID, schema isolation, JSON support |
| **Multi-tenancy** | Schema isolado por empresa | Zero vazamento de dados |
| **IA** | Anthropic Claude API | Ética, performance, long context |
| **Design tokens** | `theme.css` (custom properties) | Single source of truth |
| **Utilitários CSS** | Tailwind CSS | Produtividade, design system friendly |
| **API** | API-first com Swagger/OpenAPI | Contratos claros, facilita integrações |
| **Armazenamento** | Vercel Blob | Uploads, CVs, attachments |

**Planejado:**
- Stripe (billing)
- Trigger.dev/Inngest (async jobs)
- Sentry (observability)
- Resend (email)
- Redis/Upstash (cache)

---

## Princípios de Arquitetura

### 1. Multi-tenancy é inegociável
Zero vazamento de dados entre tenants em todas as camadas (banco, cache, sessão, logs). Schema PostgreSQL isolado por empresa.

### 2. LGPD molda a arquitetura
- Retenção configurável por tenant
- Consentimento explícito para processamento secundário
- Direitos do titular implementados (exportação, exclusão, revisão)
- Log de auditoria para decisões automatizadas

### 3. IA é suporte, não decisor
- Toda decisão automatizada é passível de revisão humana
- Disclaimers visíveis em todas as interfaces de IA
- Mibi é operador de dados; empresas clientes são controladoras

### 4. `theme.css` é a fonte da verdade
Mudanças visuais fluem dos tokens para os componentes, nunca o contrário. Design system antes de implementação.

### 5. Commits pequenos e focados
Escopo incremental, não varreduras amplas. Auditoria antes de mudança.

### 6. API-first
Contratos claros via Swagger. Toda funcionalidade acessível via API antes de UI.

---

## Riscos e Mitigações

| Risco | Probabilidade | Impacto | Mitigação |
|---|---|---|---|
| **Custos de IA acima do previsto** | Média | Alto | Limites por plano, cache agressivo, fallback para respostas pré-computadas |
| **Compliance LGPD insuficiente** | Baixa | Crítico | Validação jurídica antes do beta, DPA com todos os clientes |
| **Escalabilidade do Neon** | Média | Médio | Monitoramento de limites, plano de migração para self-hosted PostgreSQL |
| **Churn por complexidade** | Alta | Médio | Onboarding guiado, documentação clara, suporte proativo no trial |
| **Viés algorítmico em recrutamento** | Média | Alto | Auditorias de prompts, disclaimers legais, revisão humana obrigatória |

---

## Métricas de Sucesso

### Beta Aberto (Q2 2026)
- 20 empresas ativas
- 500 candidatos processados
- NPS > 40
- 0 incidentes de vazamento de dados

### Comercialização (Q3 2026)
- 50 clientes pagantes
- MRR: R$ 25k
- Churn < 10%/mês
- CAC payback < 6 meses

### Escala (2027)
- 200+ clientes
- MRR: R$ 200k+
- 5+ clientes Enterprise
- 99.9% uptime

---

## Cronograma Consolidado

```
Q2 2026 (Abr-Jun)
├─ Abr: Conclusão Fase 1 (Core) + Open Beta
├─ Mai: Fase 2 (Compliance) completa
└─ Jun: Fase 3 (Comercialização) + primeiros clientes pagantes

Q3-Q4 2026
├─ Features avançadas (Fase 4)
├─ Refinamento de prompts e scores
└─ Dashboards de analytics

2027
├─ Enterprise (Fase 5)
├─ Escala e observabilidade (Fase 6)
└─ Expansão de módulos (onboarding, performance)
```

---

## Status Atual das Fases

| Fase | Progresso | Status | ETA |
|---|---|---|---|
| **1 — Core** | ████████░░ 85% | Em andamento | Abr 2026 |
| **2 — Compliance** | ██████░░░░ 60% | Em andamento | Mai 2026 |
| **3 — Comercialização** | ░░░░░░░░░░ 0% | Planejado | Jun 2026 |
| **4 — Features avançadas** | ░░░░░░░░░░ 0% | Planejado | Q3-Q4 2026 |
| **5 — Enterprise** | ░░░░░░░░░░ 0% | Planejado | 2027 |
| **6 — Escala** | ░░░░░░░░░░ 0% | Planejado | 2027 |

---

## Próximos Passos Imediatos

### Esta semana
1. ✅ Finalizar migração de componentes para `theme.css`
2. ✅ Implementar endpoints LGPD (exportação + exclusão)
3. ✅ Refatorar prompt do assistente de recrutamento
4. 🔄 Testes de carga multi-tenant
5. 🔄 Atualizar demo pública

### Este mês (Abril)
- Concluir implementação v5 do módulo de recrutamento
- Validação jurídica dos documentos legais
- Preparação para open beta (testes, documentação)
- Primeiros beta testers (5-10 empresas)

### Q2 2026
- Open beta público
- Conclusão compliance LGPD
- Setup Stripe + páginas de pricing
- Primeiros clientes pagantes

---

**Repositórios:**
- `mibi-core` (privado): github.com/lucaskarsten/mibi-core
- `mibi` (público): github.com/lucaskarsten/mibi
- `mibi-legal` (privado): github.com/lucaskarsten/mibi-legal

**Demo:** demonstracao.rh.lucaskarsten.com.br

---

*Última atualização: 22 de março de 2026*  
*Documento vivo — revisado semanalmente*
