<div align="center">

# mibi 🤖

### Plataforma de RH com inteligência artificial para equipes modernas

Gestão de pessoas com **multi-tenancy real, automação e IA integrada**.

[Demo ao vivo](https://demonstracao.rh.lucaskarsten.com.br)

</div>

---

## O que é o mibi

**mibi** é uma plataforma de RH construída para empresas que querem usar inteligência artificial de forma prática no dia a dia de pessoas.

Cada empresa roda em um **ambiente completamente isolado**, sem compartilhar dados com outras organizações.

---

## Funcionalidades

### 👥 Gestão de colaboradores
- Cadastro e convite por e-mail
- Perfis com permissões por empresa
- Controle de acesso por papel (`admin` / `member`)

### 🤖 Agentes de IA
Cada empresa tem seus próprios agentes configuráveis, baseados em templates globais que evoluem com o uso.

| Agente | O que faz |
|---|---|
| **Assistente de RH** | Responde dúvidas sobre benefícios, férias, políticas internas e folha de pagamento |
| **Assistente de Recrutamento** | Analisa candidatos, sugere perguntas e gera pareceres estruturados |

Os agentes aprendem continuamente com os feedbacks dos colaboradores via um sistema de digest anônimo.

### 🎯 Módulo de recrutamento
- Processos seletivos com controle de status
- Cadastro e acompanhamento de candidatos
- Painel de entrevista para recrutadores — notas, perguntas/respostas, tempo de sessão
- Análise de candidatos por IA com parecer e recomendação
- Histórico completo vinculado ao candidato para comparações futuras

### 🏢 Multi-tenancy real
Cada empresa possui um **schema isolado no PostgreSQL** — não há risco de vazamento de dados entre organizações.

```
empresa_a.rh.app → schema isolado da empresa A
empresa_b.rh.app → schema isolado da empresa B
```

---

## Demo

```
https://demonstracao.rh.lucaskarsten.com.br
```

```
email: beatriz@demonstracao.com
senha: lucas1
```

---

## Roadmap

| Funcionalidade | Status |
|---|---|
| Assistente de RH com IA | ✅ Produção |
| Módulo de recrutamento | ✅ Produção |
| Painel de entrevista em tempo real | 🔜 Em desenvolvimento |
| Comparação de candidatos por IA | 🔜 Breve |
| Agente do colaborador (feedbacks internos) | 📅 v2 |
| SSO (Google / Microsoft) | 📅 v2 |
| Dashboards analíticos | 📅 v2 |

---

## Contato

Desenvolvido por **Lucas Karsten**
