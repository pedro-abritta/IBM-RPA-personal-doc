---
type: comando
tags: [ibm-rpa, comando]
---
# Comando: Esperar a janela aparecer

## Descrição
Espera uma janela aparecer para criar instância dela

## Print do Fluxo![[esperar_janela.png]]
*Legenda: tool 'Esperar a janela aparecer'

## Sintaxe/Parâmetros
- **Título**: o título da janela que será mapeada
- **Nome de classe**: nome da classe que a janela pertence. As vezes ajuda, as vezes é melhor deixar vazio
- **Nome do processo**: nome do processo que a janela pertence. As vezes ajuda, as vezes é melhor deixar vazio
- **Esperar janela filha**: marcar caso a janela seja um pop-up ou uma 'sub' janela
- **recursivo/busca segura**: ajuda a identificar uma janela na tela
- **Janela**: instância da janela identificada
- **Com sucesso**: boolean para saber se achou ou não
- **Estilos**: se for uma janela aparecendo de sistema por exemplo pode ser marcado 'filho'


## Links Relacionados
- [[janela_foco]]

## Observações Práticas
- As vezes compensa usar 'recursivo' e 'busca janela', as vezes não.

## Troubleshooting
