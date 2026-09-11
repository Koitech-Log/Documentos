# Sprint 3 — KOITECH-LOG

⬅️ [Voltar ao README principal](../README.md)

**Período:** 02/11 a 22/11

**Demonstração:** [Assistir](#)


## 🎯 Objetivo da Sprint

Permitir a exportação de dados e estatísticas dos motoristas para análises
externas e apresentações gerenciais.

## 📦 História de Usuário (User Stories)

**Legenda:** 🟩 Concluído | 🟨 Em andamento | ❌ Não iniciado

| Rank | Prioridade | User Story | Status |
|------|-----------|------------|--------|
| 8 | Alta | Como gestor, quero exportar os dados e estatísticas dos motoristas em uma planilha para realizar análises externas ou apresentar em reuniões gerenciais. | ❌ |

## ✅ Critérios de Aceitação

### US08 – Exportar relatório de motoristas em planilha

- O arquivo baixado deve estar no formato CSV ou XLSX (Excel).
- A planilha deve conter todas as colunas visíveis da tabela de ranking do sistema.


## 📝 Cenários

### US08 – Exportação de dados e estatísticas dos motoristas

**Cenário 1:** Exportação bem-sucedida<br>
Dado que estou logado como gestor<br>
E que existem motoristas e estatísticas registradas no sistema<br>
Quando eu solicito a exportação dos dados<br>
Então o sistema deve gerar um arquivo de planilha (ex: .xlsx ou .csv)<br>
E o arquivo deve conter os dados e estatísticas dos motoristas<br>
E devo conseguir realizar o download do arquivo gerado<br>


**Cenário 2:** Exportação com filtros aplicados<br>
Dado que estou na tela de listagem de motoristas<br>
E que apliquei filtros (ex: período, status, região)<br>
Quando eu solicito a exportação<br>
Então a planilha gerada deve conter apenas os dados filtrados


**Cenário 3:** Exportação sem dados disponíveis<br>
Dado que não existem motoristas ou estatísticas cadastradas no sistema (ou nenhum resultado após os filtros aplicados)<br>
Quando eu solicito a exportação<br>
Então o sistema deve informar que não há dados para exportar<br>
E nenhum arquivo deve ser gerado


**Cenário 4:** Falha na geração do arquivo<br>
Dado que estou solicitando a exportação dos dados<br>
Quando ocorre uma falha no processo de geração do arquivo<br>
Então devo visualizar uma mensagem de erro informando a falha<br>
E devo ter a opção de tentar novamente


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
