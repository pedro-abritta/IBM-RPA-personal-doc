---
type: comando
tags: [ibm-rpa, comando]
---
# Comando: Executar o leitor de SQL

## Descrição
Executa um comando SQL à partir de uma conexão de banco.

## Print do Fluxo
![[executa_leitor_SQL.png|596]]
*Legenda: tool 'Executar o leitor de SQL'

## Sintaxe/Parâmetros
- **Conexão**: Informa a conexão de banco criada
- **Declaração**: query normal de SQL
- **Tabela de dados**: a tabela que será gerada
- **Linhas/Colunas**: quantidade de linhas e colunas na tabela gerada

## Links Relacionados
- [[map_excel_ODBC]] irá gera a conexão que será usada para mapear o excel por tabela SQL

## Observações Práticas
- dentro dos colchetes é informado o nome da sheet que será mapeada e é obrigatório deixar '$' no final, caso contrário não irá identificar a sheet. 
- é possível também parametrizar a sheet trazendo dinâmica e não algo estático.

## Troubleshooting
- **Problema comum**: {{Solução}}
