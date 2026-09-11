# Sprint 2 — KOITECH-LOG

⬅️ [Voltar ao README principal](../README.md)

**Período:** 05/10 a 25/10

**Demonstração:** [Assistir](#)


## 🎯 Objetivo da Sprint

Entregar indicadores financeiros e de desempenho: dashboard financeiro,
ranking mensal da frota, rentabilidade média e histórico de viagens por
motorista.

## 📦 História de Usuário (User Stories)

**Legenda:** 🟩 Concluído | 🟨 Em andamento | ❌ Não iniciado

| Rank | Prioridade | User Story | Status |
|------|-----------|------------|--------|
| 4 | Alta | Como gestor, quero acessar o dashboard financeiro para visualizar os custos, fretes e rentabilidade consolidadas. | ❌ |
| 5 | Alta | Como gestor, quero visualizar um ranking mensal da frota para identificar quem gera o melhor resultado financeiro, aplicando as regras de valorização de rotas (SP Capital, Km, etc). | ❌ |
| 6 | Média | Como gestor, quero ver a rentabilidade média (Rentabilidade total / Número de viagens) para saber quem gera mais lucro com menos esforço. | ❌ |
| 7 | Baixa | Como gestor, quero visualizar o histórico individual de viagens de cada motorista para analisar detalhadamente as últimas entregas e o desempenho ao longo dos meses. | ❌ |

## ✅ Critérios de Aceitação

### US04 – Calcular e exibir rentabilidade financeira

- O sistema deve processar e exibir a fórmula: Rentabilidade = Valor do Frete - Custos da Operação.
- Os valores devem ser exibidos em formato monetário padrão (R$).
- Acesso restrito apenas ao Gestor. O cálculo deve ser rastreável (mostrar de onde vieram os custos).


### US05 – Calcular e exibir rentabilidade média por viagem

- O sistema deve processar e exibir no painel do motorista a fórmula: Rentabilidade média por viagem = Rentabilidade total / Número de viagens
- Os valores devem ser exibidos em formato monetário padrão (R$).
- Acesso restrito apenas ao Gestor. O cálculo deve ser rastreável (mostrar de onde vieram os custos).


### US06 – Visualizar histórico de cada motorista 

- A interface deve possuir uma tela de "Perfil do Motorista", acessível ao clicar no nome dele na listagem geral ou no ranking.
- O histórico deve listar as viagens passadas exibindo a rota, o veículo utilizado e a data.
- Como é uma visão de Gestor, a lista deve exibir o valor do frete e o custo de cada viagem histórica.


### US07 – Gerar ranking mensal gamificado 

- O ranking deve ser gerado considerando o resultado financeiro (rentabilidade) e não apenas o volume bruto de viagens.
- A tela deve exibir uma tabela consolidada cruzando: Tipo de veículo, Disponibilidade, Viagens, Valor de frete, Custos e Rentabilidade.
- Regras de valorização (como viagens para SP Capital) devem estar implementadas no peso da pontuação.
- Acesso apenas para Gestores.


## 📝 Cenários

### US04 – Dashboard financeiro

**Cenário 1:** Acesso ao dashboard com dados consolidados<br>
Dado que estou logado como gestor<br>
E que existem viagens e custos registrados no sistema<br>
Quando eu acesso o dashboard financeiro<br>
Então devo visualizar os indicadores consolidados de custos, fretes e rentabilidade<br>


**Cenário 2:** Filtro do dashboard por período<br>
Dado que estou na tela do dashboard financeiro<br>
Quando eu seleciono um período específico (data inicial e final)<br>
Então os indicadores exibidos devem ser recalculados considerando apenas o período selecionado<br>



**Cenário 3:** Dashboard sem dados no período selecionado<br>
Dado que estou na tela do dashboard financeiro<br>
Quando eu seleciono um período sem viagens ou custos registrados<br>
Então devo visualizar uma mensagem informando que não há dados para o período selecionado<br>


### US05 – Ranking mensal da frota

**Cenário 1:** Geração do ranking mensal<br>
Dado que estou logado como gestor<br>
E que existem viagens registradas no mês de referência<br>
Quando eu acesso o ranking mensal da frota<br>
Então os motoristas devem ser listados em ordem decrescente de resultado financeiro<br>
E as regras de valorização de rotas (SP Capital, Km, etc.) devem ser aplicadas no cálculo<br>


**Cenário 2:** Alteração do mês de referência<br>
Dado que estou na tela de ranking da frota<br>
Quando eu seleciono um mês de referência diferente<br>
Então o ranking deve ser recalculado considerando somente as viagens daquele mês<br>


**Cenário 3:** Empate no resultado financeiro entre motoristas<br>
Dado que dois ou mais motoristas possuem o mesmo resultado financeiro no mês<br>
Quando o ranking é gerado<br>
Então os motoristas empatados devem ser exibidos seguindo um critério de desempate definido (ex: número de viagens ou ordem alfabética)<br>


**Cenário 4:** Mês sem viagens registradas<br>
Dado que estou na tela de ranking da frota<br>
Quando eu seleciono um mês sem nenhuma viagem registrada<br>
Então devo visualizar uma mensagem informando que não há dados para gerar o ranking<br>



### US06 – Rentabilidade média por motorista

**Cenário 1:** Cálculo da rentabilidade média<br>
Dado que um motorista possui viagens registradas com rentabilidade calculada<br>
Quando eu visualizo os indicadores desse motorista<br>
Então o sistema deve exibir a rentabilidade média, calculada como rentabilidade total dividida pelo número de viagens<br>


**Cenário 2:** Motorista sem viagens registradas<br>
Dado que um motorista não possui nenhuma viagem registrada<br>
Quando eu visualizo os indicadores desse motorista<br>
Então o sistema não deve realizar a divisão por zero<br>
E devo visualizar a rentabilidade média como "N/A" ou "0"<br>


**Cenário 3:** Ordenação por rentabilidade média<br>
Dado que estou visualizando a lista de motoristas com rentabilidade média calculada<br>
Quando eu ordeno a lista por rentabilidade média<br>
Então os motoristas devem ser reordenados do maior para o menor valor (ou vice-versa, conforme selecionado)<br>



### US07 – Histórico individual de viagens do motorista

**Cenário 1:** Visualização do histórico de viagens<br>
Dado que estou logado como gestor<br>
E que um motorista possui viagens registradas<br>
Quando eu acesso o histórico individual desse motorista<br>
Então devo visualizar a lista de viagens realizadas, com detalhes de cada uma (data, rota, valor, status, etc.)<br>


**Cenário 2:** Filtro do histórico por período<br>
Dado que estou na tela de histórico de viagens do motorista<br>
Quando eu aplico um filtro por período (data inicial e final)<br>
Então devo visualizar somente as viagens realizadas dentro do período selecionado<br>


**Cenário 3:** Motorista sem histórico de viagens<br>
Dado que estou acessando o histórico de um motorista sem viagens registradas<br>
Quando a tela é carregada<br>
Então devo visualizar uma mensagem informando que não há viagens registradas para esse motorista<br>


**Cenário 4:** Visualização da evolução de desempenho ao longo dos meses<br>
Dado que um motorista possui viagens registradas em múltiplos meses<br>
Quando eu acesso o histórico individual desse motorista<br>
Então devo visualizar um comparativo ou gráfico de desempenho mês a mês<br>


## 👥 Equipe

| Membro | Papel | GitHub | LinkedIn |
|--------|-------|--------|----------|
| João Cavalcante | Product Owner | — | — |
| Rayssa Rizzi | Scrum Master | — | — |
| Felipe Silva | Desenvolvedor | — | — |
| Giovana Tarozo | Desenvolvedora | — | — |
| João Luis | Desenvolvedor | — | — |
| Lucas Pereira | Desenvolvedor | — | — |
| Mariana Neves | Desenvolvedora | — | — |
