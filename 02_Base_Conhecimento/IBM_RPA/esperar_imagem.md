---
type: comando
tags: [ibm-rpa, comando]
---
# Comando: Esperar imagem

## Descrição
Espera uma imagem específica aparecer

## Print do Fluxo![[esperar_imagem.png]]
*Legenda: tool 'Esperar imagem'

## Sintaxe/Parâmetros
- **Buscar na tela**: faz a busca da imagem na tela ou janela focada
- **Imagem**: cria um asset da imagem que será buscada
- **Grau de similaridade**: quanto porcento o match deve ser (número bom é 70~80)
- **Tempo limite**: timeout para ficar buscando
- **Intervalo de análise**: de quanto tempo será feita a busca
- **Seletor**: o tipo de busca que será feita. Se for visão será preciso informar a imagem (asset)
- **Atualizar cache da tela**: bom marcar as vezes para sempre buscar de uma tela atualizada
- **Com sucesso**: retorna um boolean se achou ou não


## Links Relacionados
- [[janela_foco]]
- [[esperar_janela]] fazer busca de imagem em uma janela em foco


## Observações Práticas
- As vezes compensa usar 'recursivo' e 'busca janela', as vezes não.

## Troubleshooting
