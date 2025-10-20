# 7. MVP (Minimum Viable Product)

## Definição do MVP

### Visão do MVP
**Um sistema funcional de análise de mercado com ML que permite traders visualizar dados em tempo real, receber alertas automáticos e obter predições sobre direção de preços, com infraestrutura auditável e segura.**

### Objetivo do MVP
Validar as seguintes hipóteses críticas:
1. ✅ **Hipótese Técnica:** Conseguimos processar dados de mercado com latência < 1s
2. ✅ **Hipótese de ML:** Modelo atinge 70%+ de acurácia em predições de direção
3. ✅ **Hipótese de Valor:** Traders pagam por análises automatizadas em tempo real
4. ✅ **Hipótese de UX:** Interface é suficientemente intuitiva para uso sem treinamento extenso

---

## User Stories Incluídas no MVP

### ✅ US001 - Monitoramento em Tempo Real (Sprint 1)
**Por quê no MVP:** Base fundamental. Sem dados em tempo real, não há produto.

**Entregáveis:**
- Dashboard com atualização automática (< 1s refresh)
- Visualização de OHLCV para até 10 ativos
- Indicadores técnicos básicos: SMA, EMA, RSI, MACD
- Histórico de 24 horas

**Critério de Aceitação MVP:**
- [ ] Latência end-to-end < 1 segundo (p95)
- [ ] Zero perda de dados durante 8h de operação contínua
- [ ] 5 usuários conseguem usar simultaneamente

---

### ✅ US002 - Alertas de Movimentos (Sprint 2)
**Por quê no MVP:** Funcionalidade esperada básica. Demonstra valor imediato.

**Entregáveis:**
- Configuração de alertas por threshold (% ou valor absoluto)
- Notificações via email e push notification
- Histórico dos últimos 7 dias de alertas

**Critério de Aceitação MVP:**
- [ ] Alerta dispara em < 5 segundos após evento
- [ ] Taxa de falsos positivos < 5%
- [ ] Histórico persiste corretamente

---

### ✅ US003 - Previsão de Direção (Sprint 3-4)
**Por quê no MVP:** Core value proposition. Diferencial competitivo principal.

**Entregáveis:**
- Modelo de classificação UP/DOWN/NEUTRAL
- Confidence score para cada predição
- Atualização de predições a cada 5 minutos
- Visualização de acurácia histórica (última 24h)

**Critério de Aceitação MVP:**
- [ ] Acurácia ≥ 70% em dados de teste
- [ ] Latência de inferência < 500ms
- [ ] Explicação básica (top 3 features) disponível

---

### ✅ US014 - Analytics de Performance ML (Sprint 20)
**Por quê no MVP:** Essencial para MLOps. Detecta degradação do modelo.

**Entregáveis:**
- Dashboard com métricas básicas: accuracy, precision, recall
- Alertas quando acurácia cai > 10%
- Gráfico de acurácia ao longo do tempo

**Critério de Aceitação MVP:**
- [ ] Métricas atualizam a cada hora
- [ ] Alertas funcionam corretamente
- [ ] Dados retidos por 30 dias

---

### ✅ US015 - Gestão de Usuários (Sprint 21)
**Por quê no MVP:** Requisito de segurança básico. Bloqueante para produção.

**Entregáveis:**
- Autenticação via email/senha
- 2 perfis: Admin e Trader
- Logs de auditoria de login

**Critério de Aceitação MVP:**
- [ ] Autenticação segura (bcrypt/JWT)
- [ ] Sessões expiram após 30min inatividade
- [ ] Admin pode criar/desativar usuários

---

### ✅ US016 - Auditoria de Decisões (Sprint 22)
**Por quê no MVP:** Compliance básico. Essencial para regulatório.

**Entregáveis:**
- Log de todas as predições com timestamp
- Busca por data e ativo
- Exportação em CSV

**Critério de Aceitação MVP:**
- [ ] 100% das predições são logadas
- [ ] Logs são imutáveis
- [ ] Busca retorna resultados em < 2s

---

## O que NÃO está no MVP

### 🚫 Funcionalidades Excluídas (e Por Quê)

| Feature | Motivo da Exclusão | Quando Incluir |
|---------|-------------------|----------------|
| Sentimento de Notícias (US004) | Incerteza técnica em acurácia NLP | Release 1.0 - Sprint 5 |
| Dashboard Customizável (US007) | Nice-to-have UX, não core value | Release 1.0 - Sprint 9 |
| Chat Interface (US006) | Complexidade vs valor no MVP | Release 1.0 - Sprint 7-8 |
| Backtesting (US008) | Validação pode ser feita offline inicialmente | Release 1.0 - Sprint 10-11 |
| Paper Trading (US009) | Feature educacional, não bloqueante | Release 2.0 - Sprint 12 |
| Automação Completa (US011) | Muito complexo, nicho específico | Release 3.0 - Sprint 15+ |
| Mobile App Nativo | Desktop web suficiente para MVP | Backlog futuro |
| Múltiplos Modelos de ML | Modelo único bem calibrado suficiente | Post-MVP após validação |

---

## Increments Futuros (Roadmap)

### 🎯 Release 1.0 (Q2 2025) - "Enhanced Experience"
**Objetivo:** Ampliar capacidades analíticas e melhorar UX

**Features:**
- Análise de sentimento de notícias
- Recomendações personalizadas por perfil de risco
- Dashboard customizável
- Chat para consultas
- Backtesting de estratégias
- Relatórios automatizados

**Métricas de Sucesso:**
- 100+ usuários ativos mensais
- NPS > 50
- Churn < 10%/mês

---

### 🚀 Release 2.0 (Q3 2025) - "Advanced Analytics"
**Objetivo:** Ferramentas para usuários avançados

**Features:**
- Paper trading em tempo real
- Simulações de Monte Carlo
- Multiple timeframes (1min, 5min, 15min, 1h)
- Análise de correlação entre ativos
- Portfolio optimization suggestions

**Métricas de Sucesso:**
- 30% dos usuários são power users
- Tempo médio na plataforma > 45min/dia
- 50+ estratégias em backtesting

---

### 🤖 Release 3.0 (Q4 2025) - "Automation"
**Objetivo:** Automação completa de trading

**Features:**
- Builder visual de estratégias
- Execução automatizada com limites
- Integração com brokers (API)
- Webhook para sistemas externos
- Advanced risk management

**Métricas de Sucesso:**
- 20+ estratégias automatizadas ativas
- Volume de operações automatizadas > R$ 1M/mês
- Win rate médio > 55%

---

## Cronograma Detalhado do MVP

### Fase 1: Fundação (Sprints 1-2) - 4 semanas
**Objetivo:** Infraestrutura de dados e visualização básica

| Semana | Atividades | Responsável | Entregáveis |
|--------|-----------|-------------|-------------|
| 1 | Setup infraestrutura (Kafka, Redis, PostgreSQL) | DevOps | Ambiente provisionado |
| 1-2 | Implementar ingestão de dados | Data Eng | Pipeline de dados funcional |
| 2 | Desenvolver dashboard básico | Frontend | Visualização OHLCV |
| 2 | Sistema de alertas | Backend | Alertas por email |

**Milestone:** ✅ Dados fluindo em tempo real com visualização

---

### Fase 2: Machine Learning (Sprints 3-4) - 4 semanas
**Objetivo:** Modelo preditivo em produção

| Semana | Atividades | Responsável | Entregáveis |
|--------|-----------|-------------|-------------|
| 3 | Feature engineering pipeline | Data Science | 35+ features calculadas |
| 3-4 | Treinamento de modelos (XGBoost, LSTM) | Data Science | Modelos com accuracy > 70% |
| 4 | API de inferência | MLOps | Endpoint com latência < 500ms |
| 4 | Integração frontend-backend | Full Stack | Predições na UI |

**Milestone:** ✅ Predições funcionando em tempo real

---

### Fase 3: MLOps (Sprint 20) - 2 semanas
**Objetivo:** Monitoramento e observabilidade

| Semana | Atividades | Responsável | Entregáveis |
|--------|-----------|-------------|-------------|
| 20 | Dashboard de métricas ML | Data Science | Grafana dashboards |
| 20 | Alertas de degradação | MLOps | Alerting system |

**Milestone:** ✅ Modelo monitorado continuamente

---

### Fase 4: Governance (Sprints 21-22) - 4 semanas
**Objetivo:** Segurança e compliance

| Semana | Atividades | Responsável | Entregáveis |
|--------|-----------|-------------|-------------|
| 21 | Sistema de autenticação | Backend | OAuth2 + JWT |
| 21 | Gestão de permissões | Backend | RBAC implementado |
| 22 | Sistema de auditoria | Backend | Logs imutáveis |
| 22 | Documentação compliance | Compliance | Relatório de conformidade |

**Milestone:** ✅ Sistema pronto para produção com compliance

---

### Fase 5: Testes e Ajustes (Sprint 23) - 2 semanas
**Objetivo:** Validação completa e go-live

| Semana | Atividades | Responsável | Entregáveis |
|--------|-----------|-------------|-------------|
| 23 | Testes de carga | QA | Relatório de performance |
| 23 | Beta testing com 10 usuários | Product | Feedback documentado |
| 23 | Correções críticas | Dev Team | Bugs resolvidos |
| 23 | Preparação go-live | DevOps | Runbook de produção |

**Milestone:** ✅ MVP pronto para lançamento

---

## Cronograma Visual

```
══════════════════════════════════════════════════════════════════════
                      MVP TIMELINE - 16 SEMANAS
══════════════════════════════════════════════════════════════════════

Mês 1-2 │ FUNDAÇÃO + ML
────────┼─────────────────────────────────────────────────────────────
 Sem 1  │ ████████ Infra Setup + Data Ingestion
 Sem 2  │ ████████ Dashboard + Alerts
 Sem 3  │ ████████ Feature Engineering
 Sem 4  │ ████████ ML Training + API
────────┼─────────────────────────────────────────────────────────────

Mês 5-6 │ MLOPS + GOVERNANCE
────────┼─────────────────────────────────────────────────────────────
 Sem 20 │ ████████ MLOps Monitoring
 Sem 21 │ ████████ Authentication + RBAC
 Sem 22 │ ████████ Audit System
 Sem 23 │ ████████ Testing + Go-Live Prep
────────┼─────────────────────────────────────────────────────────────

        🚀 LAUNCH MVP
══════════════════════════════════════════════════════════════════════
```

**Nota:** Sprints 5-19 serão usados para releases futuras (Release 1.0)

---

## Recursos Necessários para MVP

### Time Mínimo

| Papel | Alocação | Sprints Críticos |
|-------|----------|------------------|
| Product Owner | 50% | Todos |
| Tech Lead | 100% | 1-4 |
| Data Engineer | 100% | 1-2 |
| Data Scientist (Senior) | 100% | 3-4, 20 |
| Backend Developer | 100% | 2, 21-22 |
| Frontend Developer | 100% | 2, 4 |
| MLOps Engineer | 50% | 4, 20 |
| DevOps Engineer | 50% | 1, 23 |
| QA Engineer | 50% | 23 |

**Total:** ~6.5 FTEs durante MVP

---

### Infraestrutura

| Recurso | Especificação | Custo Mensal (est.) |
|---------|--------------|---------------------|
| **Compute** | 4x m5.2xlarge (AWS) | $2,400 |
| **GPU** | 1x p3.2xlarge (treino) | $1,200 |
| **Database** | RDS PostgreSQL (db.r5.xlarge) | $600 |
| **Cache** | ElastiCache Redis | $300 |
| **Streaming** | MSK (Kafka) 3 brokers | $800 |
| **Storage** | S3 + EBS | $500 |
| **APIs** | Market data feeds | $3,000 |
| **Monitoring** | DataDog/New Relic | $400 |

**Total MVP:** ~$9,200/mês

---

## Critérios de Sucesso do MVP

### Métricas Técnicas
| Métrica | Target | Medição |
|---------|--------|---------|
| Latência de dados | < 1s (p95) | Logs de sistema |
| Latência de inferência | < 500ms (p95) | APM |
| Uptime | > 99% | Monitoring |
| Acurácia do modelo | > 70% | Métricas ML |
| Taxa de erro | < 0.1% | Error tracking |

### Métricas de Produto
| Métrica | Target | Medição |
|---------|--------|---------|
| Usuários beta ativos | 10+ | Analytics |
| Sessões por usuário/semana | > 5 | Analytics |
| Tempo médio de sessão | > 15min | Analytics |
| NPS (beta users) | > 30 | Survey |
| Bugs críticos | 0 | Issue tracker |

### Métricas de Negócio
| Métrica | Target | Medição |
|---------|--------|---------|
| Conversão beta → pago | > 50% | Sales |
| Willingness to pay | > $100/mês | Survey |
| Churn beta users | < 20% | Analytics |

---

## Riscos do MVP

| Risco | Probabilidade | Impacto | Mitigação |
|-------|---------------|---------|-----------|
| Latência > 1s | Média | Alto | Load testing antecipado, otimizações |
| Acurácia < 70% | Média | Crítico | Baseline estabelecido, múltiplos algoritmos |
| API de dados instável | Alta | Alto | Fallback providers, cache agressivo |
| Falta de usuários beta | Baixa | Médio | Pipeline de early adopters preparado |
| Requisito regulatório novo | Baixa | Alto | Legal review antecipado |
| Dívida técnica acumulada | Alta | Médio | Code reviews, refactoring contínuo |

---

## Definição de "Pronto" (DoD) para MVP

✅ **Código:**
- [ ] Code review aprovado por 2+ desenvolvedores
- [ ] Cobertura de testes > 70%
- [ ] Sem vulnerabilidades críticas (Snyk/SonarQube)
- [ ] Documentação técnica atualizada

✅ **Funcionalidade:**
- [ ] Todas as US do MVP implementadas
- [ ] Critérios de aceitação validados
- [ ] Testes end-to-end passando
- [ ] Performance dentro dos targets

✅ **Deploy:**
- [ ] Deploy automatizado funcional (CI/CD)
- [ ] Rollback testado e funcional
- [ ] Monitoring e alertas configurados
- [ ] Runbook documentado

✅ **Negócio:**
- [ ] 10 usuários beta recrutados
- [ ] Treinamento básico preparado
- [ ] Suporte inicial estruturado
- [ ] Pricing model validado

---

*Data de Launch Target MVP: [Data + 16 semanas]*  
*Responsável: [Product Owner]*  
*Aprovação Stakeholders: [Pendente/Aprovado]*