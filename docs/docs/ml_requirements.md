# 4. Requisitos de Machine Learning

## ML Canvas

### 1. Problema de Negócio
**Predizer a direção do movimento de preços de ativos financeiros nos próximos 5-15 minutos com precisão suficiente para suportar decisões de trading automatizadas.**

**Tipo de Problema:** Classificação multiclasse (UP / DOWN / NEUTRAL) e Regressão (magnitude do retorno)

---

### 2. Dados Disponíveis

#### Dados Primários
- **Histórico de preços:** OHLCV (Open, High, Low, Close, Volume) em granularidade de 1 minuto
- **Order book:** Profundidade de mercado, bid/ask spread, imbalance
- **Trades:** Fluxo de negociações tick-by-tick
- **Fonte:** https://github.com/ranaroussi/yfinance

#### Volume de Dados
- **Treinamento:** ~24 meses × 30 ativos × 390 minutos/dia = ~8.4M observações
- **Features:** 35+ variáveis por observação
- **Tamanho estimado:** ~15GB não comprimido

---

### 3. Stakeholders

| Stakeholder | Interesse | Expectativa |
|------------|-----------|-------------|
| Traders | Sinais precisos e rápidos | Acurácia > 70%, latência < 500ms |
| Gestores de Risco | Controle de exposição | Confidence scores confiáveis |
| Compliance | Auditabilidade | Explicabilidade das decisões |
| Cientistas de Dados | Experimentação | Ambiente MLOps robusto |
| Investidores | ROI | Performance financeira positiva |

---

### 4. Métricas de Sucesso

### Métricas de ML

#### Métricas de Classificação (Direção)
| Métrica | Target | Mínimo Aceitável |
|---------|--------|------------------|
| **Accuracy** | 75% | 65% |
| **Precision (classe UP)** | 72% | 62% |
| **Recall (classe UP)** | 70% | 60% |
| **F1-Score (macro)** | 71% | 61% |
| **AUC-ROC (OvR)** | 0.80 | 0.70 |

#### Métricas de Regressão (Magnitude)
| Métrica | Target | Mínimo Aceitável |
|---------|--------|------------------|
| **RMSE** | < 0.8% | < 1.2% |
| **MAE** | < 0.5% | < 0.8% |
| **R²** | > 0.40 | > 0.25 |

#### Métricas Temporais
| Métrica | Target | Mínimo Aceitável |
|---------|--------|------------------|
| **Latência de Inferência (p95)** | < 300ms | < 500ms |
| **Throughput** | > 1000 pred/s | > 500 pred/s |

### Métricas de Negócio

| Métrica | Target | Descrição |
|---------|--------|-----------|
| **Win Rate** | > 55% | Percentual de operações lucrativas |
| **Profit Factor** | > 1.5 | Razão lucro bruto / perda bruta |
| **Sharpe Ratio** | > 1.2 | Retorno ajustado ao risco |
| **Max Drawdown** | < 15% | Maior perda acumulada |
| **Tempo de Resposta** | < 1s | Da predição à execução |

---

### 5. Hipóteses e Premissas

#### Hipóteses de ML
1. **H1:** Padrões técnicos em janelas de 5-15 minutos são preditivos da direção de preços
2. **H2:** Order book imbalance é um indicador líder de movimento de preços
3. **H3:** Sentimento de notícias tem correlação com volatilidade e direção
4. **H4:** Features de microestrutura melhoram acurácia vs apenas OHLCV
5. **H5:** Modelos ensemble superam modelos individuais em robustez

#### Premissas
- Mercados são parcialmente eficientes (há padrões exploráveis em curto prazo)
- Dados históricos são representativos do comportamento futuro
- Latência de coleta de dados < 100ms é mantida
- Não há look-ahead bias nos dados de treinamento
- Market impact das operações é negligível

---

## Requisitos Funcionais de ML

### RML001 - Arquitetura de Modelos
**Descrição:** Implementar arquitetura ensemble com múltiplos algoritmos.

**Critérios de Aceitação:**
- Mínimo 3 algoritmos base: Gradient Boosting (XGBoost/LightGBM), Random Forest, LSTM/GRU
- Meta-learner para combinação de predições (Stacking ou Voting)
- Pesos adaptativos baseados em performance recente
- Fallback para modelo simples em caso de falha

**Prioridade:** MUST HAVE

---

### RML002 - Feature Engineering
**Descrição:** Pipeline automatizado de engenharia de features.

**Critérios de Aceitação:**
- 35+ features base documentadas no mapeamento
- Features técnicas calculadas em tempo real
- Feature importance tracking e seleção automática
- Versionamento de feature sets

**Prioridade:** MUST HAVE

---

### RML003 - Tratamento de Dados
**Descrição:** Preprocessamento robusto para garantir qualidade.

**Critérios de Aceitação:**
- Tratamento de outliers (IQR ou Z-score > 3)
- Imputação de missing values (forward fill, média móvel)
- Normalização/padronização (StandardScaler ou RobustScaler)
- Detecção de data leakage em pipeline

**Prioridade:** MUST HAVE

---

### RML004 - Balanceamento de Classes
**Descrição:** Lidar com desbalanceamento entre classes UP/DOWN/NEUTRAL.

**Critérios de Aceitação:**
- Análise de distribuição de classes no dataset
- Aplicação de SMOTE, ADASYN ou undersampling conforme necessário
- Class weights nos algoritmos
- Validação de que balanceamento não introduz bias

**Prioridade:** MUST HAVE

---

### RML005 - Validação Temporal
**Descrição:** Validação respeitando ordem temporal dos dados.

**Critérios de Aceitação:**
- Time Series Split (sem shuffle)
- Walk-forward validation
- Validação em múltiplos períodos (bull market, bear market, lateral)
- Métricas por regime de mercado

**Prioridade:** MUST HAVE

---

### RML006 - Explicabilidade
**Descrição:** Capacidade de explicar predições do modelo.

**Critérios de Aceitação:**
- SHAP values para cada predição
- Feature importance global e local
- Visualizações de explicabilidade na interface
- Relatórios de auditoria para compliance

**Prioridade:** MUST HAVE

---

### RML007 - Retreinamento Automático
**Descrição:** Pipeline de retreinamento periódico e triggered.

**Critérios de Aceitação:**
- Retreinamento mensal agendado
- Trigger por degradação de métricas (> 10% queda em acurácia)
- Validação automática antes de deployment
- A/B testing de modelo novo vs antigo

**Prioridade:** MUST HAVE

---

### RML008 - Monitoramento de Drift
**Descrição:** Detecção de drift em features e predições.

**Critérios de Aceitação:**
- Monitoramento de data drift (distribuição de features)
- Monitoramento de concept drift (mudança de padrões)
- Alertas quando drift significativo detectado (KS test p < 0.05)
- Dashboard de health do modelo

**Prioridade:** MUST HAVE

---

### RML009 - Versionamento de Modelos
**Descrição:** Controle de versão completo de modelos e experimentos.

**Critérios de Aceitação:**
- MLflow ou similar para tracking de experimentos
- Versionamento de modelos com metadados completos
- Capacidade de rollback para versões anteriores
- Registro de todos os hiperparâmetros e métricas

**Prioridade:** MUST HAVE

---

### RML010 - Data Augmentation
**Descrição:** Técnicas para aumentar variabilidade do dataset de treino.

**Critérios de Aceitação:**
- Time warping para séries temporais
- Adição de ruído gaussiano controlado
- Mixup/synthetic samples quando apropriado
- Validação de que augmentation melhora generalização

**Prioridade:** SHOULD HAVE

---

## Requisitos Não Funcionais de ML

### RNML001 - Reprodutibilidade
**Descrição:** Garantir que experimentos sejam reproduzíveis.

**Critérios:**
- Seeds fixas para todos os geradores aleatórios
- Versionamento de código, dados e ambiente
- Containers Docker para ambiente de treino
- Documentação de todos os passos do pipeline

**Prioridade:** MUST HAVE

---

### RNML002 - Eficiência Computacional
**Descrição:** Otimizar uso de recursos computacionais.

**Critérios:**
- Treinamento em GPU quando disponível
- Batch processing eficiente
- Model compression (quantização, pruning) para inferência
- Cache de features intermediárias

**Prioridade:** SHOULD HAVE

---

### RNML003 - Robustez
**Descrição:** Modelo deve ser robusto a diferentes condições de mercado.

**Critérios:**
- Performance consistente em diferentes regimes de volatilidade
- Resistência a eventos extremos (outliers)
- Degradação graceful em caso de dados faltantes
- Testes de stress em cenários adversos

**Prioridade:** MUST HAVE

---

### RNML004 - Fairness e Bias
**Descrição:** Evitar vieses sistemáticos no modelo.

**Critérios:**
- Análise de bias em diferentes setores/ativos
- Validação de que não há favorecimento injustificado
- Métricas de fairness documentadas
- Correções quando bias detectado

**Prioridade:** SHOULD HAVE

---

## Pipeline de ML

```
┌─────────────────────────────────────────────────────────────────┐
│                        DATA COLLECTION                          │
│  API Mercado → Kafka → Data Lake → Feature Store                │
└────────────────────┬────────────────────────────────────────────┘
                     │
                     ▼
┌─────────────────────────────────────────────────────────────────┐
│                     FEATURE ENGINEERING                         │
│  Raw Data → Indicators → Derived Features → Feature Selection   │
└────────────────────┬────────────────────────────────────────────┘
                     │
                     ▼
┌─────────────────────────────────────────────────────────────────┐
│                      PREPROCESSING                              │
│  Outliers → Missing Values → Normalization → Train/Val/Test     │
└────────────────────┬────────────────────────────────────────────┘
                     │
                     ▼
┌─────────────────────────────────────────────────────────────────┐
│                      MODEL TRAINING                             │
│  ┌──────────┐  ┌──────────┐  ┌──────────┐                      │
│  │ XGBoost  │  │ LightGBM │  │   LSTM   │                      │
│  └────┬─────┘  └────┬─────┘  └────┬─────┘                      │
│       └─────────────┴─────────────┘                             │
│                      │                                          │
│              ┌───────▼────────┐                                 │
│              │  Meta-Learner  │                                 │
│              │   (Stacking)   │                                 │
│              └───────┬────────┘                                 │
└──────────────────────┼──────────────────────────────────────────┘
                       │
                       ▼
┌─────────────────────────────────────────────────────────────────┐
│                       VALIDATION                                │
│  Time Series CV → Metrics → Explainability → Drift Detection    │
└────────────────────┬────────────────────────────────────────────┘
                     │
                     ▼
┌─────────────────────────────────────────────────────────────────┐
│                      DEPLOYMENT                                 │
│  Model Registry → A/B Testing → Production → Monitoring         │
└─────────────────────────────────────────────────────────────────┘
```

---

## Configuração de Experimentos

### Hiperparâmetros Base - XGBoost
```python
{
    'objective': 'multi:softprob',
    'num_class': 3,
    'max_depth': 7,
    'learning_rate': 0.05,
    'n_estimators': 300,
    'subsample': 0.8,
    'colsample_bytree': 0.8,
    'min_child_weight': 3,
    'gamma': 0.1,
    'reg_alpha': 0.05,
    'reg_lambda': 1.0,
    'scale_pos_weight': [1.0, 1.2, 1.0]  # Ajustar por classe
}
```

### Hiperparâmetros Base - LSTM
```python
{
    'units': [128, 64, 32],
    'dropout': 0.3,
    'recurrent_dropout': 0.2,
    'sequence_length': 60,  # 60 minutos
    'batch_size': 128,
    'epochs': 50,
    'optimizer': 'adam',
    'learning_rate': 0.001,
    'early_stopping_patience': 10
}
```

---

## Estratégia de Otimização

### Busca de Hiperparâmetros
- **Método:** Optuna (Bayesian Optimization)
- **Trials:** 100 iterações
- **Objective:** Maximizar F1-Score macro em validação
- **Pruning:** MedianPruner para early stopping de trials ruins

### Cross-Validation
- **Método:** TimeSeriesSplit com 5 folds
- **Purging:** 1 dia entre treino e validação
- **Embargo:** 2 horas após período de validação

---

## Baseline e Benchmarks

| Modelo | Accuracy | F1-Score | Latência | Notas |
|--------|----------|----------|----------|-------|
| Random | 33.3% | 0.33 | - | Baseline teórico |
| Moving Average Crossover | 52% | 0.48 | < 10ms | Baseline técnico |
| Logistic Regression | 58% | 0.55 | < 50ms | Baseline ML simples |
| **Target XGBoost** | **75%** | **0.71** | **< 300ms** | Objetivo |
| **Target Ensemble** | **77%** | **0.73** | **< 500ms** | Stretch goal |

---

## Riscos de ML

| Risco | Probabilidade | Impacto | Mitigação |
|-------|---------------|---------|-----------|
| Overfitting | Alta | Alto | Cross-validation rigorosa, regularização |
| Data leakage | Média | Crítico | Code review, testes automatizados |
| Concept drift | Alta | Alto | Monitoramento contínuo, retreinamento |
| Feature correlation | Média | Médio | Análise de VIF, PCA se necessário |
| Outliers extremos | Média | Médio | Robust scaling, detecção proativa |
| Latência em produção | Baixa | Alto | Load testing, model optimization |

---

*Última atualização: [Data]*
*Responsável: Equipe de Data Science*