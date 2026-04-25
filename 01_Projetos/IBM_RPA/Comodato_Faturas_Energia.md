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

Receber mensalmente um arquivo comodato de excel que contenha unidades consumidoras com faturas de energia em aberto. A automação irá ler cada linha, baixar via [[02_Base_Conhecimento/IBM_RPA/Fluxo_HTTP_Arquivo|Fluxo_HTTP_Arquivo]] e validar 5 informações que estão no excel com as que estão na fatura referente: 
- Mês referência
- Data Vencimento
- Valor Total
- Número da Nota Fiscal
- Valor da Nota Fiscal
Se houver divergência de informação, aquela fatura não será paga naquele mês. Ao final do processamento é gerado um arquivo excel com o relatório comparativo dos campos informando se houve ou não divergência de informação. 

O projeto possui mais de 90 templates mapeados via [[regex]] e OCR, cada um para uma concessionária de energia diferente no país. 

Antes de começar o mapeamento de cada fatura, o robô insere TODAS as linhas do excel em 2 tabelas de controle no banco. Ao final do processamento e validação, é inserido o relatório final em uma terceira tabela que é refletida no [Cognos](https://www.ibm.com/br-pt/products/cognos-analytics). 

## Print da Lógica Principal
![[{{fluxo_comodato_vtal.png}}]]

*Legenda: {{Descrever o fluxo: extração de dados → validação → geração de fatura → envio}}*

## Escopo
- **Processos**: {{Lista de processos automatizados}}
- **Volume**: {{Dados/transações por período}}
- **Sistema**: {{Sistema ou aplicação envolvida}}

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
- 

## Manutenção
### Verificações Regulares
- {{Frequência}}: {{O que verificar}}
- {{Frequência}}: {{Outro check}}

### Pontos de Atenção
- {{Risco/problema potencial 1}}
- {{Risco/problema potencial 2}}

## Contato
- **Responsável**: {{Nome}}
- **Suporte**: [[03_Solucoes_e_Erros|Guia de troubleshooting]]
