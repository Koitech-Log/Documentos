# Sprint 1 — KOITECH-LOG

⬅️ [Voltar ao README principal](../README.md)

**Período:** 07/09 a 27/09

**Demonstração:** [Assistir](#)


## 🎯 Objetivo da Sprint

Estabelecer a base do sistema: cadastro oficial de motoristas, visualização
rápida de disponibilidade e vínculo das viagens via upload de manifesto.


## 📦 História de Usuário (User Stories)

**Legenda:** 🟩 Concluído | 🟨 Em andamento | ❌ Não iniciado


| Rank | Prioridade | User Story | Status |
|------|-----------|------------|--------|
| 1 | Alta | Como operador, quero visualizar rapidamente a situação de cada motorista (Disponível ou Ocupado) para identificar quem está livre para novas operações e evitar a ociosidade da frota. | 🟨 |
| 2 | Alta | Como operador, quero realizar o upload do manifesto para que o sistema vincule as viagens aos motoristas já cadastrados. | 🟨 |
| 3 | Média | Como gestor, quero realizar a carga inicial da base de motoristas para que o sistema tenha o cadastro oficial (Nome, CPF/CNPJ, Telefone, Veículo, Placa, Status). | 🟨 |


## ✅ Critérios de Aceitação

### US01 – Cadastrar motoristas agregados

- O back-end deve permitir a importação de uma carga inicial de motoristas via script ou painel.
- Deve existir uma tela de CRUD básico para visualizar/editar esses motoristas.


### US02 – Importar dados

- O sistema deve ler o CSV e relacionar a operação a um motorista da base.
-Se o CSV contiver um motorista não cadastrado, o sistema NÃO deve criá-lo automaticamente, mas sim gerar um "Alerta de Cadastro Pendente".
- O front-end deve exibir uma mensagem clara de sucesso (ou erro, detalhando a falha) após a leitura do arquivo.


### US03 – Visualizar painel de disponibilidade de motoristas

- A interface deve destacar visualmente o status (Disponível/Ocupado) na listagem principal.
- A listagem deve exibir colunas com: motoristas em operação; Número de viagens realizadas; Dias disponíveis e dias em operação; Utilização dos motoristas; Valor dos fretes; Custos das operações Rentabilidade por motorista; Rentabilidade média por viagem.
- Deve existir um filtro funcional na tela para buscar motoristas pelo status e pelo tipo de veículo (Fiorino, Van, VUC, 3/4, Toco, Truck, Carreta).
- O Operador NÃO pode visualizar a coluna de valores financeiros ou rentabilidade nesta tela.
- O Operador pode atualizar manualmente o status de disponibilidade do motorista


## 📝 Cenários

### US01 – Visualizar situação dos motoristas
**Cenário 1:** Visualizar lista de motoristas com status atualizado<br>
Dado que existem motoristas cadastrados no sistema<br>
E que estou logado como operador<br>
Quando eu acesso a tela de visualização de motoristas<br>
Então devo visualizar a lista de motoristas<br>
E cada motorista deve exibir seu status atual como "Disponível" ou "Ocupado"<br>


**Cenário 2:** Identificar motoristas disponíveis para nova operação<br>
Dado que estou na tela de visualização de motoristas<br>
Quando eu filtro pelo status "Disponível"<br>
Então devo visualizar somente os motoristas com status "Disponível"<br>


**Cenário 3:** Status atualizado automaticamente após vínculo a uma viagem<br>
Dado que um motorista está com status "Disponível"<br>
Quando uma viagem é vinculada a esse motorista<br>
Então o status do motorista deve ser atualizado automaticamente para "Ocupado"<br>


**Cenário 4:** Nenhum motorista disponível no momento<br>
Dado que todos os motoristas estão com status "Ocupado"<br>
Quando eu acesso a tela de visualização de motoristas<br>
Então devo visualizar uma mensagem informando que não há motoristas disponíveis no momento<br>


### US02 – Upload do manifesto

**Cenário 1:** Upload de manifesto válido<br>
Dado que estou logado como operador<br>
E que possuo um arquivo de manifesto no formato aceito pelo sistema<br>
Quando eu realizo o upload do arquivo<br>
Então o sistema deve processar o manifesto com sucesso<br>
E as viagens contidas no manifesto devem ser vinculadas aos motoristas cadastrados<br>
E devo visualizar uma mensagem de confirmação do upload<br>


**Cenário 2:** Upload de manifesto com motorista não cadastrado<br>
Dado que estou realizando o upload de um manifesto<br>
E que o manifesto contém uma viagem vinculada a um motorista não cadastrado no sistema<br>
Quando o sistema processa o arquivo<br>
Então o sistema deve identificar a inconsistência<br>
E devo visualizar uma mensagem informando quais viagens não puderam ser vinculadas e o motivo<br>


**Cenário 3:** Upload de arquivo em formato inválido<br>
Dado que estou na tela de upload de manifesto<br>
Quando eu tento enviar um arquivo em formato não suportado<br>
Então o sistema deve rejeitar o upload<br>
E devo visualizar uma mensagem de erro informando o formato esperado<br>


**Cenário 4:** Upload de manifesto vazio ou corrompido<br>
Dado que estou na tela de upload de manifesto<br>
Quando eu envio um arquivo vazio ou corrompido<br>
Então o sistema não deve processar nenhuma viagem<br>
E devo visualizar uma mensagem de erro informando que o arquivo não pôde ser lido<br>


### US03 – Carga inicial da base de motoristas

**Cenário 1:** Carga inicial bem-sucedida<br>
Dado que estou logado como gestor<br>
E que possuo um arquivo com os dados dos motoristas (Nome, CPF/CNPJ, Telefone, Veículo, Placa, Status)<br>
Quando eu realizo a carga inicial da base<br>
Então todos os motoristas devem ser cadastrados no sistema<br>
E devo visualizar uma mensagem de confirmação com a quantidade de registros importados<br>


**Cenário 2:** Carga com campos obrigatórios ausentes<br>
Dado que estou realizando a carga inicial da base de motoristas<br>
E que um ou mais registros estão sem campos obrigatórios preenchidos (Nome, CPF/CNPJ)<br>
Quando eu submeto o arquivo<br>
Então o sistema deve rejeitar os registros inválidos<br>
E devo visualizar uma lista dos registros com erro e o campo faltante<br>


**Cenário 3:** Carga com CPF/CNPJ duplicado<br>
Dado que estou realizando a carga inicial da base de motoristas<br>
E que o arquivo contém um CPF/CNPJ já cadastrado no sistema<br>
Quando eu submeto o arquivo<br>
Então o sistema não deve duplicar o cadastro<br>
E devo visualizar um alerta indicando o registro duplicado<br>


**Cenário 4:** Carga com CPF/CNPJ em formato inválido<br>
Dado que estou realizando a carga inicial da base de motoristas<br>
E que um registro possui CPF/CNPJ em formato inválido<br>
Quando eu submeto o arquivo<br>
Então o sistema deve rejeitar esse registro<br>
E devo visualizar uma mensagem indicando o erro de formatação<br>


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
