---
type: projeto
status: ativo
cliente: MDS
data_inicio: 
data_conclusao: 
tags: [ibm-rpa, projeto, mds]
---

# Projeto: Conciliação Financeira - MDS

## Objetivo
{{Automatização da conciliação financeira de transações para cliente MDS}}

## Print da Lógica Principal
![[{{fluxo_conciliacao_mds.png}}]]

*Legenda: {{Descrever o fluxo: extração de dados → comparação → identificação de divergências → relatório}}*

## Escopo
- **Processos**: {{Lista de processos automatizados}}
- **Volume**: {{Dados/transações por período}}
- **Sistema**: {{Sistema ou aplicação envolvida}}

## Estrutura de Bots
```
Projeto: Conciliação Financeira
├── Bot Principal: [[{{Bot_Principal}}]]
├── Bot Auxiliar: [[{{Bot_Auxiliar}}]]
└── Serviço: [[{{Bot_Servico}}]]
```

## Comandos Utilizados
- [[T_Comando_IBM|Comando 1]]
- [[T_Comando_IBM|Comando 2]]
- [[T_Comando_IBM|Comando 3]]

## Manutenção
### Verificações Regulares
- {{Frequência}}: {{O que verificar}}
- {{Frequência}}: {{Outro check}}

### Pontos de Atenção
- {{Risco/problema potencial 1}}
- {{Risco/problema potencial 2}}

## Histórico de Mudanças
| Data | Alteração | Responsável |
|------|-----------|------------|
| {{YYYY-MM-DD}} | Criação do projeto | {{Nome}} |

## Contato
- **Responsável**: {{Nome}}
- **Suporte**: [[03_Solucoes_e_Erros|Guia de troubleshooting]]
