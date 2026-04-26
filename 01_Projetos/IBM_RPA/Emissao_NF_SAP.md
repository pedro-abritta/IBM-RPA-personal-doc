---
type: projeto
status: finalizado
cliente: "[[dados_sensiveis#cliente_emissao_nf]]"
data_produção: 08/2024
tags:
  - ibm-rpa
  - projeto
---
# Projeto: Emissão de Notas Fiscais em ERP (SAP)

## Objetivo

Acessar o SAP dentro de uma máquina virtual e verificar se há novas notas fiscais para serem emitidas de forma autônoma. 

Ao final do processo é enviado uma mensagem via webhook para o teams notificando o status da execução - Se falhou ao processar, se emitiu corretamente, se não há notas a serem processadas.

O processo inteiro é desenvolvido utilizando OCR e mapeamentos e focos de janelas para o robô atuar em cada etapa por vez.

Se a automação falha ou acontece algum cenário de WARN (erro mapeado) um e-mail também é disparado aos responsáveis. 

A automação acessa a VM a cada 15 minutos para fazer a verificação.

## Print da Lógica Principal


*Legenda: Relatório gerado por RPA após mapeamento de valores

## Estrutura de Script
```
Projeto: Emissão de Notas Fiscais em ERP
├── Orquestrador: Executor principal. Ativa todos os outros scripts.
├───── Captura texto com todas as notas em aberto e cria uma tabela por regex
├─────── Ordena de forma crescente/decrescente (parametrizado via tenant) 
├───── Emite NF: chama script de geração de NF
├─────── realiza processo de ações para emitir uma NF por vez
├───── Fecha abas: chama script que fecha todas as janelas abertas do SAP
├───── Salva log do SAP
├───── Salva evidência de execução
├───── Envia log de status de execução no teams via webhook
├───── Task kill para finalizar todos os .exe do SAP
```

## Comandos Utilizados
- [[Regex]]
- [[gravar_tela|Gravar tela (processo completo)]]
- [[classificar_tabela|Classificar (ordenar) tabela]]
- [[esperar_janela|Esperar janela]]
- [[janela_foco|Janela Foco]]
- [[dividir_texto|Dividir texto (transformar em lista)]]
- [[obter_parametros_tenant|Obter parâmetro tenant]]
- [[conectar_smtp_server|Conectar ao SMTP server]]
- [[esperar_imagem|Esperar imagem]]
- [[logout_via_cmd|Fazer logout]]
- [[escrever_arquivo|Escrever no arquivo]]
- [[incluir_coluna|Incluir Coluna]]
- [[chatbot_teams|Enviar mensagem no teams via webhoook]]


## Pontos de Atenção
- Se alguma coluna fundamental do excel vier escrita errada ou faltando, a automação irá notificar o problema e o processo será cancelado. 
- Se a fatura baixada for imagem ou for ilegível, será mostrado no relatório final e não haverá a análise da mesma. 
- Todas as faturas em pdf são baixadas em uma VM, agrupadas por ano e mês
- Todas as faturas são enviadas ao OneDrive para salvar em nuvem

## Eficiência Atingida
- **Antes**: processo manual realizado em final de expediente por analistas
	- **problema**: final de mês, época de fechamento sempre acumulavam MUITAS notas
- **Automatizado**: emissão 24/7 de todas as notas. gastando 1:20min para emitir cada uma
	- Processo emite mais de 2 mil notas por mês de forma autônoma