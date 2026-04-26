---
type: comando
tags: [ibm-rpa, comando]
---
# Comando: Iniciar/parar gravação de tela

## Descrição
grava tela durante um período de tempo definido.

## Print do Fluxo![[iniciar_gravação_tela.png]]
*Legenda: tool 'Iniciar gravação de tela'
## Sintaxe/Parâmetros
- **Pasta**: onde será salvo a gravação
- **Índice da tela**: qual tela será gravada
- **Quadros por segundo**: quantidade de frames. 24 é ok, mas fica muito pixelado, se for necessário avaliar detalhes, tem que aumentar o fps

![[parar_gravação_tela.png]]
*Legenda: tool 'Parar gravação de tela'

## Sintaxe/Parâmetros
- **caminhos**: é do tipo lista de texto


## Links Relacionados
- para gerar o arquivo de vídeo é necessário percorrer um for each da lista de texto criada depois de 'parar gravação ![[for_each_video.png]]
*Legenda: for each para gerar vídeo de gravação

## Observações Práticas
- Importante a cada iteração salvar o nome do arquivo diferente pois se já existir o arquivo a iteração falha.

## Troubleshooting
