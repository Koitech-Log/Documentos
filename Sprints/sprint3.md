# Sprint 3 — KOITECH-LOG

⬅️ [Voltar ao README principal](../README.md)

**Período:** 02/11 a 22/11

**Demonstração:** [Assistir](#)


## 🎯 Objetivo da Sprint

Entregar a gestão de usuários (cadastro, senha inicial, listagem, alteração de
perfil e histórico de alterações) e o ranking mensal da frota, com regras de
valorização de rotas e cálculo padronizado de pontuação por motorista e por
veículo.

## 📦 História de Usuário (User Stories)

**Legenda:** 🟩 Concluído | 🟨 Em andamento | ❌ Não iniciado

| Rank | Prioridade | Épico | User Story | Estimativa | Status |
|------|-----------|-------|------------|------------|--------|
| 8 | Média | 10 | Como gestor, quero cadastrar um novo usuário informando nome, e-mail e perfil (gestor ou operador), para que novas pessoas tenham acesso ao sistema. | 8 | 🟩 |
| 9 | Média | 10 | Como gestor, quero definir uma senha inicial ao cadastrar o usuário, para que ele consiga acessar sem depender de e-mail. | 5 | 🟩 |
| 10 | Baixa | 11 | Como gestor, quero ver os usuários cadastrados e buscar por nome, e-mail ou perfil, para encontrar rápido quem preciso ajustar. | 5 | 🟩 |
| 11 | Média | 11 | Como gestor, quero alterar o perfil de um usuário entre gestor e operador, para controlar o que cada pessoa pode fazer no sistema. | 5 | 🟩 |
| 12 | Baixa | 11 | Como gestor, quero que as alterações de perfil fiquem registradas, para saber quem mudou o quê e quando. | 13 | 🟨 |
| 13 | Média | 12 | Como gestor, quero que as viagens para São Paulo sejam valorizadas acima das demais, para que o desempenho reflita o valor real da rota. | 8 | ❌ |
| 14 | Baixa | 12 | Como gestor, quero que o sistema calcule automaticamente a pontuação de cada motorista e de cada veículo no mês, para que o ranking seja padronizado. | 13 | ❌ |
| 15 | Baixa | 12 | Como gestor, quero ver o ranking mensal de motoristas e de veículos, para identificar quem gera o melhor resultado financeiro. | 5 | 🟨 |


## ✅ Critérios de Aceitação

### Épico 10 — Cadastro de usuários

#### US12 – Cadastrar usuário

- O gestor informa nome, e-mail e perfil.
- O e-mail precisa ser válido e único, senão o sistema exibe erro.
- Só os perfis gestor e operador estão disponíveis.
- O usuário criado passa a existir no sistema e consegue fazer login.

#### US13 – Definir senha inicial e trocar no primeiro acesso

- O gestor informa a senha inicial no cadastro.
- No primeiro login, o usuário é obrigado a trocar a senha.
- A senha inicial não é exibida depois de salva.


### Épico 11 — Gestão de perfis de acesso

#### US14 – Listar e buscar usuários

- A lista mostra nome, e-mail e perfil atual.
- O gestor busca ou filtra por nome, e-mail e perfil.
- Só o gestor acessa a tela.

#### US15 – Alterar o perfil de um usuário

- O gestor altera o perfil e salva.
- A mudança vale na próxima ação do usuário.
- O gestor não pode remover o próprio perfil de gestor.
- O sistema não permite remover o último gestor.

#### US16 – Registrar histórico das alterações de perfil

- Cada alteração grava quem alterou, quando, o perfil anterior e o novo.
- O histórico não pode ser editado pela interface.
- O gestor consegue consultar o histórico de um usuário.


### Épico 12 — Ranking mensal da frota

#### US18 – Regras de valorização das rotas

- Viagens com destino a São Paulo recebem valorização maior que as demais.
- O fator de valorização fica em configuração, não fixo no código, porque o cliente ainda vai definir os valores.
- Viagens fora de qualquer regra usam o valor base.
- A estrutura permite incluir novas regras (por exemplo quilometragem) sem refazer o cálculo.

#### US19 – Calcular a pontuação por motorista e por veículo

- A pontuação considera rentabilidade, quantidade de viagens e valorização.
- O cálculo é feito para motorista e para veículo com a mesma fórmula.
- O mesmo conjunto de dados sempre gera o mesmo resultado.
- Os casos de empate e de quem não tem viagens no mês têm tratamento definido.

#### US17 – Visualizar o ranking mensal da frota

- O gestor escolhe o mês e alterna entre ranking de motoristas e de veículos.
- A lista vem ordenada por pontuação, com rentabilidade, viagens e pontuação.
- Mês sem dados mostra mensagem vazia.
- Só o gestor acessa, por fazer parte do dashboard financeiro.


## 📝 Cenários

### US12 – Cadastrar usuário

**Cenário 1:** Cadastro bem-sucedido<br>
Dado que estou logado como gestor<br>
E que estou na tela de cadastro de usuário<br>
Quando eu informo nome, e-mail válido, perfil e senha inicial<br>
E confirmo o cadastro<br>
Então o usuário deve ser criado no sistema<br>
E deve conseguir fazer login com o e-mail e a senha informados<br>


**Cenário 2:** E-mail inválido<br>
Dado que estou na tela de cadastro de usuário<br>
Quando eu informo um e-mail em formato inválido<br>
E tento salvar<br>
Então o sistema deve exibir uma mensagem de erro informando que o e-mail é inválido<br>
E o usuário não deve ser criado<br>


**Cenário 3:** E-mail já cadastrado<br>
Dado que já existe um usuário cadastrado com o e-mail informado<br>
Quando eu tento cadastrar um novo usuário com esse mesmo e-mail<br>
Então o sistema deve exibir uma mensagem informando que o e-mail já está em uso<br>
E o usuário não deve ser criado<br>


**Cenário 4:** Campos obrigatórios não preenchidos<br>
Dado que estou na tela de cadastro de usuário<br>
Quando eu deixo de preencher nome, e-mail ou perfil<br>
E tento salvar<br>
Então o sistema deve destacar os campos obrigatórios não preenchidos<br>
E o usuário não deve ser criado<br>


**Cenário 5:** Perfis disponíveis<br>
Dado que estou na tela de cadastro de usuário<br>
Quando eu abro a seleção de perfil<br>
Então devo visualizar apenas as opções "Gestor" e "Operador"<br>


### US13 – Definir senha inicial e trocar no primeiro acesso

**Cenário 1:** Definição da senha inicial no cadastro<br>
Dado que estou cadastrando um novo usuário como gestor<br>
Quando eu informo a senha inicial e salvo o cadastro<br>
Então a senha deve ser armazenada de forma segura<br>
E não deve ser exibida novamente em nenhuma tela após salva<br>


**Cenário 2:** Troca obrigatória no primeiro acesso<br>
Dado que um usuário foi cadastrado com senha inicial<br>
Quando ele faz login pela primeira vez<br>
Então o sistema deve redirecioná-lo para a tela de troca de senha<br>
E ele não deve acessar nenhuma outra funcionalidade até definir uma nova senha<br>


**Cenário 3:** Troca de senha concluída<br>
Dado que estou na tela de troca de senha do primeiro acesso<br>
Quando eu informo uma nova senha válida e confirmo<br>
Então a senha deve ser atualizada<br>
E devo ser direcionado para a tela inicial do sistema<br>
E nos próximos logins não devo ser obrigado a trocar a senha novamente<br>


**Cenário 4:** Nova senha igual à senha inicial<br>
Dado que estou na tela de troca de senha do primeiro acesso<br>
Quando eu informo uma nova senha igual à senha inicial<br>
Então o sistema deve exibir uma mensagem informando que a nova senha deve ser diferente da atual<br>


### US14 – Listar e buscar usuários

**Cenário 1:** Listagem de usuários<br>
Dado que estou logado como gestor<br>
E que existem usuários cadastrados<br>
Quando eu acesso a tela de usuários<br>
Então devo visualizar a lista com nome, e-mail e perfil atual de cada usuário<br>


**Cenário 2:** Busca por nome ou e-mail<br>
Dado que estou na tela de usuários<br>
Quando eu digito um nome ou e-mail no campo de busca<br>
Então devo visualizar somente os usuários que correspondem ao termo buscado<br>


**Cenário 3:** Filtro por perfil<br>
Dado que estou na tela de usuários<br>
Quando eu filtro pelo perfil "Gestor" ou "Operador"<br>
Então devo visualizar somente os usuários com o perfil selecionado<br>


**Cenário 4:** Busca sem resultados<br>
Dado que estou na tela de usuários<br>
Quando eu busco por um termo que não corresponde a nenhum usuário<br>
Então devo visualizar uma mensagem informando que nenhum usuário foi encontrado<br>


**Cenário 5:** Acesso negado ao operador<br>
Dado que estou logado como operador<br>
Quando eu tento acessar a tela de usuários<br>
Então o sistema deve bloquear o acesso<br>
E exibir uma mensagem informando que não tenho permissão<br>


### US15 – Alterar o perfil de um usuário

**Cenário 1:** Alteração de perfil bem-sucedida<br>
Dado que estou logado como gestor<br>
E que existe um usuário com perfil "Operador"<br>
Quando eu altero o perfil dele para "Gestor" e salvo<br>
Então o novo perfil deve ser exibido na listagem<br>
E a mudança deve valer a partir da próxima ação desse usuário no sistema<br>


**Cenário 2:** Gestor tenta remover o próprio perfil de gestor<br>
Dado que estou logado como gestor<br>
Quando eu tento alterar o meu próprio perfil para "Operador"<br>
Então o sistema deve impedir a alteração<br>
E exibir uma mensagem informando que não posso remover o meu próprio perfil de gestor<br>


**Cenário 3:** Tentativa de remover o último gestor<br>
Dado que existe apenas um usuário com perfil "Gestor" no sistema<br>
Quando é feita uma tentativa de alterar o perfil desse usuário para "Operador"<br>
Então o sistema deve impedir a alteração<br>
E exibir uma mensagem informando que o sistema precisa ter ao menos um gestor<br>


**Cenário 4:** Usuário rebaixado perde acesso imediatamente<br>
Dado que um usuário com perfil "Gestor" está usando o sistema<br>
E que seu perfil foi alterado para "Operador"<br>
Quando ele tenta acessar uma funcionalidade exclusiva de gestor<br>
Então o sistema deve bloquear o acesso conforme o novo perfil<br>


### US16 – Registrar histórico das alterações de perfil

**Cenário 1:** Registro automático da alteração<br>
Dado que estou logado como gestor<br>
Quando eu altero o perfil de um usuário e salvo<br>
Então o sistema deve registrar no histórico quem fez a alteração, a data e hora, o perfil anterior e o novo perfil<br>


**Cenário 2:** Consulta do histórico de um usuário<br>
Dado que um usuário teve o perfil alterado uma ou mais vezes<br>
Quando eu acesso o histórico desse usuário<br>
Então devo visualizar todas as alterações, da mais recente para a mais antiga<br>


**Cenário 3:** Usuário sem alterações de perfil<br>
Dado que um usuário nunca teve o perfil alterado<br>
Quando eu acesso o histórico desse usuário<br>
Então devo visualizar uma mensagem informando que não há alterações registradas<br>


**Cenário 4:** Histórico não editável<br>
Dado que estou visualizando o histórico de alterações de um usuário<br>
Quando eu procuro uma opção para editar ou excluir um registro<br>
Então a interface não deve oferecer nenhuma opção de edição ou exclusão<br>


### US18 – Regras de valorização das rotas

**Cenário 1:** Viagem com destino a São Paulo<br>
Dado que existe uma regra de valorização configurada para o destino São Paulo<br>
Quando uma viagem com destino a São Paulo é considerada no cálculo<br>
Então o sistema deve aplicar o fator de valorização configurado<br>
E a viagem deve receber valor maior que uma viagem equivalente para outro destino<br>


**Cenário 2:** Viagem fora de qualquer regra<br>
Dado que uma viagem não se enquadra em nenhuma regra de valorização<br>
Quando ela é considerada no cálculo<br>
Então o sistema deve utilizar o valor base<br>


**Cenário 3:** Alteração do fator de valorização<br>
Dado que o fator de valorização de São Paulo está definido na configuração<br>
Quando o valor desse fator é alterado na configuração<br>
Então os próximos cálculos devem utilizar o novo fator<br>
E não deve ser necessária nenhuma alteração no código<br>


**Cenário 4:** Inclusão de nova regra<br>
Dado que existe a regra de valorização por destino<br>
Quando uma nova regra (ex: por quilometragem) é incluída<br>
Então o cálculo deve passar a considerá-la sem que a lógica existente precise ser refeita<br>


### US19 – Calcular a pontuação por motorista e por veículo

**Cenário 1:** Cálculo da pontuação mensal<br>
Dado que existem viagens registradas no mês de referência<br>
Quando o sistema calcula a pontuação<br>
Então cada motorista e cada veículo deve receber uma pontuação considerando rentabilidade, quantidade de viagens e valorização das rotas<br>


**Cenário 2:** Mesma fórmula para motorista e veículo<br>
Dado que um motorista realizou todas as suas viagens do mês com o mesmo veículo<br>
E que esse veículo não teve viagens com outros motoristas<br>
Quando o sistema calcula a pontuação<br>
Então o motorista e o veículo devem receber a mesma pontuação<br>


**Cenário 3:** Resultado determinístico<br>
Dado um mesmo conjunto de viagens e configurações<br>
Quando o cálculo da pontuação é executado mais de uma vez<br>
Então o resultado deve ser sempre o mesmo<br>


**Cenário 4:** Empate na pontuação<br>
Dado que dois ou mais motoristas (ou veículos) obtêm a mesma pontuação no mês<br>
Quando o sistema calcula a pontuação<br>
Então deve aplicar o critério de desempate definido (ex: maior rentabilidade, depois maior quantidade de viagens)<br>


**Cenário 5:** Motorista ou veículo sem viagens no mês<br>
Dado que um motorista ou veículo não possui viagens no mês de referência<br>
Quando o sistema calcula a pontuação<br>
Então deve aplicar o tratamento definido (pontuação zero ou ausência no ranking)<br>
E o cálculo não deve gerar erro<br>


### US17 – Visualizar o ranking mensal da frota

**Cenário 1:** Visualização do ranking de motoristas<br>
Dado que estou logado como gestor<br>
E que existem viagens registradas no mês selecionado<br>
Quando eu acesso o ranking mensal<br>
Então devo visualizar os motoristas ordenados pela pontuação, da maior para a menor<br>
E cada linha deve exibir rentabilidade, quantidade de viagens e pontuação<br>


**Cenário 2:** Alternar para o ranking de veículos<br>
Dado que estou na tela de ranking mensal<br>
Quando eu alterno a visualização para veículos<br>
Então devo visualizar os veículos ordenados pela pontuação, com rentabilidade, viagens e pontuação<br>


**Cenário 3:** Alteração do mês de referência<br>
Dado que estou na tela de ranking mensal<br>
Quando eu seleciono outro mês<br>
Então o ranking deve ser atualizado considerando somente as viagens daquele mês<br>


**Cenário 4:** Mês sem dados<br>
Dado que estou na tela de ranking mensal<br>
Quando eu seleciono um mês sem viagens registradas<br>
Então devo visualizar uma mensagem informando que não há dados para o mês selecionado<br>


**Cenário 5:** Acesso negado ao operador<br>
Dado que estou logado como operador<br>
Quando eu tento acessar o ranking mensal<br>
Então o sistema deve bloquear o acesso<br>
E exibir uma mensagem informando que não tenho permissão<br>


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
