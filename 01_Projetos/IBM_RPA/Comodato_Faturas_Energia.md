---
type: projeto
status: finalizado
cliente: "[[dados_sensiveis#cliente_comodato]]"
data_produção: 02/2024
tags:
  - ibm-rpa
  - projeto
---
# Projeto: Comodato Faturas de Energia

## Objetivo

O cliente submete em um portal o arquivo comodato do mês/ano referente e a automação é ativada via API. Ao receber mensalmente um arquivo comodato de excel que contenha unidades consumidoras com faturas de energia em aberto a automação irá ler cada linha, baixar a fatura via [[02_Base_Conhecimento/IBM_RPA/Fluxo_HTTP_Arquivo|Fluxo_HTTP_Arquivo]] e validar 5 informações que estão no excel com as que estão na fatura referente: 
- Mês referência
- Data Vencimento
- Valor Total
- Número da Nota Fiscal
- Valor da Nota Fiscal
Se houver divergência de informação, aquela fatura não será paga naquele mês. Ao final do processamento é gerado um arquivo excel com o relatório comparativo dos campos informando se houve ou não divergência de informação. 

O projeto possui mais de 90 templates mapeados via [[regex]] e OCR, cada um para uma concessionária de energia diferente no país. 

Antes de começar o mapeamento de cada fatura, o robô insere TODAS as linhas do excel em 2 tabelas de controle no banco. Ao final do processamento e validação, é inserido o relatório final em uma terceira tabela que é refletida no [Cognos](https://www.ibm.com/br-pt/products/cognos-analytics). 

## Print da Lógica Principal

![[relatorio_final_RPA.png]]
*Legenda: Relatório gerado por RPA após mapeamento de valores

## Estrutura de Script
```
Projeto: Comodato Faturas de Energia
├── Orquestrador: Executor principal. Ativa todos os outros scripts.
├───── Inserir dados tabela 1: Script para adicionar registros na tabela 1
├───── Inserir dados tabela 2: Script para adicionar registros na tabela 2
├───── Baixar arquivo: Script para baixar todas as faturas via http (uma de cada vez)
├───── Valida arquivo: Valida se o pdf é válido, se é imagem (sem texto)
├───── Mapear template: identifica concessionária, chamar script da mesma e usar regex/OCR para capturar todas as informações necessárias
├───── Validar regras: faz match das informações para saber se está divergente
├───── Gerar relatório final: gerar excel com as informações de divergência ou match de cada linha
```

## Comandos Utilizados
- [[Regex]]
- [[02_Base_Conhecimento/IBM_RPA/Fluxo_HTTP_Arquivo|Fluxo HTTP do Arquivo]]
- [[map_excel_ODBC|Conectar ao ODBC]]
- [[executar_leitor_SQL|Executar o leitor de SQL]]
- [[conectar_microsoft_onedrive|Conectar ao Microsoft OneDrive]]
- [[enviar_sistema_arquivos|Enviar para o sistema de arquivos]]
- [[converter_tipo_arquivo|Converter tipo de arquivo via cmd]]
- [[Query_timestemp|Query para capturar horário específico]]
- [[remove_zero_esquerda|Remove zero a esquerda por regex usando "replace"]]
- [[uso_switch_case|Aplicação de switch case]]


## Pontos de Atenção
- Se alguma coluna fundamental do excel vier escrita errada ou faltando, a automação irá notificar o problema e o processo será cancelado. 
- Se a fatura baixada for imagem ou for ilegível, será mostrado no relatório final e não haverá a análise da mesma. 
- Todas as faturas em pdf são baixadas em uma VM, agrupadas por ano e mês
- Todas as faturas são enviadas ao OneDrive para salvar em nuvem

