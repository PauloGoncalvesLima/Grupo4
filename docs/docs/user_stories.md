# 5. Histórias de Usuário (User Stories)

## Épico 1: Análise em Tempo Real

### US001 - Monitoramento de Ativos em Tempo Real
**Como** trader profissional  
**Eu quero** visualizar dados de mercado atualizados em tempo real  
**Para** identificar oportunidades rapidamente e tomar decisões informadas

**Critérios de Aceitação:**
- [ ] Dashboard atualiza preços a cada segundo sem refresh manual
- [ ] Visualização de OHLCV, volume e spread em gráficos interativos
- [ ] Latência de atualização < 1 segundo
- [ ] Suporte a visualização de múltiplos ativos simultaneamente (até 20)
- [ ] Indicadores técnicos calculados e exibidos em tempo real
- [ ] Histórico de pelo menos 24 horas disponível para análise

**Prioridade:** MUST HAVE  
**Story Points:** 13  
**Sprint:** 1

---

### US002 - Alertas de Movimentos Significativos
**Como** investidor  
**Eu quero** receber alertas quando um ativo tiver movimento de preço significativo  
**Para** reagir rapidamente a oportunidades ou riscos

**Critérios de Aceitação:**
- [ ] Configuração de thresholds personalizados por ativo (% ou valor absoluto)
- [ ] Alertas via push notification, email e SMS
- [ ] Histórico de alertas com timestamp e contexto
- [ ] Possibilidade de snooze ou dismiss de alertas
- [ ] Filtros para evitar spam (mínimo intervalo entre alertas do mesmo tipo)
- [ ] Indicação de severidade (baixa, média, alta, crítica)

**Prioridade:** MUST HAVE  
**Story Points:** 8  
**Sprint:** 2

---

## Épico 2: Predições e Recomendações

### US003 - Previsão de Direção de Preço
**Como** trader  
**Eu quero** ver predições do modelo ML sobre a direção provável do preço  
**Para** embasar minhas decisões de compra ou venda

**Critérios de Aceitação:**
- [ ] Predição clara (UP/DOWN/NEUTRAL) com confidence score
- [ ] Atualização das predições a cada 5 minutos
- [ ] Visualização gráfica da predição vs realidade
- [ ] Histórico de acurácia das últimas predições (últimas 24h, 7 dias)
- [ ] Explicação das principais features que influenciaram a predição
- [ ] Indicação de risco associado à operação sugerida

**Prioridade:** MUST HAVE  
**Story Points:** 21  
**Sprint:** 3-4

---

### US004 - Análise de Sentimento de Notícias
**Como** analista de mercado  
**Eu quero** ver o sentimento agregado de notícias sobre um ativo  
**Para** entender o contexto além dos números técnicos

**Critérios de Aceitação:**
- [ ] Score de sentimento (-1 a +1) atualizado a cada 15 minutos
- [ ] Lista de headlines recentes com classificação individual
- [ ] Fontes das notícias claramente identificadas
- [ ] Histórico de sentimento nas últimas 48 horas em gráfico
- [ ] Correlação entre sentimento e movimento de preço
- [ ] Filtro por fonte de notícia (Bloomberg, Reuters, etc.)

**Prioridade:** SHOULD HAVE  
**Story Points:** 13  
**Sprint:** 5

---

### US005 - Recomendações Personalizadas
**Como** investidor conservador  
**Eu quero** receber recomendações filtradas por meu perfil de risco  
**Para** ver apenas oportunidades alinhadas com minha tolerância a risco

**Critérios de Aceitação:**
- [ ] Perfil de risco configurável (conservador, moderado, arrojado)
- [ ] Recomendações filtradas automaticamente por perfil
- [ ] Score de risco visível em cada recomendação (0-100)
- [ ] Estimativa de stop-loss e take-profit sugeridos
- [ ] Tamanho de posição recomendado baseado em capital disponível
- [ ] Rationale explicando por que a recomendação se adequa ao perfil

**Prioridade:** SHOULD HAVE  
**Story Points:** 13  
**Sprint:** 6

---

## Épico 3: Interface e Interação

### US006 - Consulta por Chat
**Como** usuário não técnico  
**Eu quero** fazer perguntas em linguagem natural sobre ativos  
**Para** obter análises sem navegar por múltiplas telas

**Critérios de Aceitação:**
- [ ] Chatbot responde perguntas como "Como está PETR4?"
- [ ] Suporte a comandos predefinidos documentados
- [ ] Resposta em < 3 segundos
- [ ] Histórico de conversas salvo e pesquisável
- [ ] Sugestões contextuais de perguntas relacionadas
- [ ] Capacidade de gerar gráficos sob demanda via chat

**Prioridade:** SHOULD HAVE  
**Story Points:** 21  
**Sprint:** 7-8

---

### US007 - Dashboard Personalizável
**Como** day trader  
**Eu quero** customizar meu dashboard com widgets relevantes  
**Para** ter acesso rápido às informações que mais uso

**Critérios de Aceitação:**
- [ ] Drag-and-drop de widgets no dashboard
- [ ] Biblioteca de widgets: gráficos, listas, alertas, heatmaps
- [ ] Múltiplos layouts salvos (ex: "Morning View", "End of Day")
- [ ] Compartilhamento de layouts com outros usuários
- [ ] Temas claro/escuro
- [ ] Responsive design (desktop, tablet, mobile)

**Prioridade:** SHOULD HAVE  
**Story Points:** 13  
**Sprint:** 9

---

## Épico 4: Backtesting e Simulação

### US008 - Backtesting de Estratégias
**Como** trader quantitativo  
**Eu quero** testar minhas estratégias com dados históricos  
**Para** validar sua eficácia antes de arriscar capital real

**Critérios de Aceitação:**
- [ ] Interface para definir estratégias com regras if-then
- [ ] Seleção de período histórico para teste (até 2 anos)
- [ ] Métricas de performance: Sharpe, Win Rate, Max DD, Profit Factor
- [ ] Visualização equity curve e drawdown
- [ ] Análise de trades individuais (winners vs losers)
- [ ] Exportação de relatório em PDF

**Prioridade:** SHOULD HAVE  
**Story Points:** 21  
**Sprint:** 10-11

---

### US009 - Paper Trading
**Como** trader iniciante  
**Eu quero** simular operações em tempo real sem risco financeiro  
**Para** aprender e testar estratégias com dados reais

**Critérios de Aceitação:**
- [ ] Conta virtual com capital configurável
- [ ] Execução simulada de ordens em tempo real
- [ ] Latência simulada realista (~100-500ms)
- [ ] Portfolio tracking com P&L atualizado
- [ ] Comparação com mercado real (benchmark)
- [ ] Histórico completo de operações simuladas

**Prioridade:** COULD HAVE  
**Story Points:** 13  
**Sprint:** 12

---

### US010 - Simulação de Cenários
**Como** analista de risco  
**Eu quero** simular diferentes cenários de mercado  
**Para** avaliar o impacto no portfolio

**Critérios de Aceitação:**
- [ ] Configuração de parâmetros: volatilidade, tendência, correlações
- [ ] Simulação Monte Carlo com N iterações configuráveis
- [ ] Distribuição de resultados esperados em gráfico
- [ ] Métricas de risco: VaR, CVaR, probabilidade de perda
- [ ] Comparação lado a lado de múltiplos cenários
- [ ] Exportação de resultados

**Prioridade:** COULD HAVE  
**Story Points:** 21  
**Sprint:** 13-14

---

## Épico 5: Automação e Estratégias

### US011 - Criação de Estratégias Automatizadas
**Como** trader algorítmico  
**Eu quero** criar estratégias de trading automatizadas  
**Para** executar operações sem intervenção manual

**Critérios de Aceitação:**
- [ ] Builder visual de estratégias (flowchart-style)
- [ ] Biblioteca de blocos: indicadores, condições, ações
- [ ] Validação de sintaxe e lógica da estratégia
- [ ] Preview de sinais gerados pela estratégia
- [ ] Configuração de limites de risco (max loss, max positions)
- [ ] Versionamento de estratégias

**Prioridade:** COULD HAVE  
**Story Points:** 34  
**Sprint:** 15-17

---

### US012 - Execução Automatizada com Aprovação
**Como** gestor de fundos  
**Eu quero** que estratégias sejam executadas automaticamente mas com minha aprovação  
**Para** manter controle sobre operações críticas

**Critérios de Aceitação:**
- [ ] Modo "semi-automático" configurável por estratégia
- [ ] Notificação de operação sugerida com timeout
- [ ] Aprovação via app mobile ou web
- [ ] Auto-aprovação após timeout (configurável)
- [ ] Log de aprovações/rejeições
- [ ] Estatísticas de adesão às sugestões

**Prioridade:** COULD HAVE  
**Story Points:** 13  
**Sprint:** 18

---

## Épico 6: Relatórios e Analytics

### US013 - Relatórios Automatizados
**Como** gestor  
**Eu quero** receber relatórios diários de performance automaticamente  
**Para** acompanhar resultados sem esforço manual

**Critérios de Aceitação:**
- [ ] Relatórios diários, semanais e mensais configuráveis
- [ ] Envio automático por email no horário agendado
- [ ] Conteúdo customizável (métricas, gráficos, ativos)
- [ ] Formato PDF profissional
- [ ] Comparação com períodos anteriores
- [ ] Highlights automáticos (best/worst performers)

**Prioridade:** SHOULD HAVE  
**Story Points:** 13  
**Sprint:** 19

---

### US014 - Analytics de Performance do Modelo
**Como** cientista de dados  
**Eu quero** visualizar métricas de performance do modelo ML  
**Para** identificar degradação e necessidade de retreinamento

**Critérios de Aceitação:**
- [ ] Dashboard com métricas em tempo real: acurácia, precision, recall
- [ ] Análise de drift (data drift e concept drift)
- [ ] Gráficos de feature importance ao longo do tempo
- [ ] Alertas quando métricas caem abaixo de threshold
- [ ] Comparação entre versões de modelo
- [ ] Explicabilidade (SHAP) de predições específicas

**Prioridade:** MUST HAVE  
**Story Points:** 13  
**Sprint:** 20

---

## Épico 7: Administração e Segurança

### US015 - Gestão de Usuários
**Como** administrador do sistema  
**Eu quero** gerenciar usuários e suas permissões  
**Para** controlar acesso aos recursos

**Critérios de Aceitação:**
- [ ] CRUD de usuários com perfis (Admin, Trader, Viewer)
- [ ] Permissões granulares por funcionalidade
- [ ] Log de auditoria de ações dos usuários
- [ ] Autenticação via OAuth2 (Google, Microsoft)
- [ ] 2FA obrigatório para operações financeiras
- [ ] Sessões expiram após inatividade (30min)

**Prioridade:** MUST HAVE  
**Story Points:** 13  
**Sprint:** 21

---

### US016 - Auditoria de Decisões
**Como** compliance officer  
**Eu quero** auditar todas as decisões tomadas pelo sistema  
**Para** garantir conformidade regulatória

**Critérios de Aceitação:**
- [ ] Log imutável de todas as predições e recomendações
- [ ] Explicação completa de cada decisão (features usadas)
- [ ] Filtros por data, ativo, usuário, tipo de operação
- [ ] Exportação em formato auditável (CSV, JSON)
- [ ] Retenção de logs por 5 anos
- [ ] Interface de busca avançada

**Prioridade:** MUST HAVE  
**Story Points:** 13  
**Sprint:** 22

---

## Resumo de Priorização

### Must Have (MVP)
- US001, US002, US003, US014, US015, US016

### Should Have (Release 1.0)
- US004, US005, US007, US008, US013

### Could Have (Releases Futuras)
- US006, US009, US010, US011, US012

---

*Total Story Points: 287*  
*Estimativa de Sprints: 22 (11 meses, sprints de 2 semanas)*  
*Última atualização: [Data]*