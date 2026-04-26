---
type: comando
tags: [ibm-rpa, comando]
---
# Comando: Obter texto de expressão regular

## Descrição
Capturar o texto literal desejado. 
Site [Regex101](https://regex101.com/) ajuda a testar mas ele não funciona 100% igual ao regex do próprio Studio.


## Print do Fluxo
![[regex.png]]

*Legenda: tool 'Obter texto de expressão regular'

## Sintaxe/Parâmetros
- **Opções**: 'Várias linhas' e 'Ignorar tipo de letra'
- **Número do grupo**: se o regex estiver entre vários parênteses e houver mais de um match, o 'grupo' significa qual índice que será capturado (1, 2, 3, 4)
- **Obter por índice**: mesma regra se aplica acima ![[regex_match_por_indice.png]]



## Links Relacionados
- [[Comodato_Faturas_Energia]]

## Observações Práticas (utilitários)
- captura quebra de linha: \n
- captura caracteres de whitespace: \s
- captura token anterior de zero a infinito: * (greedy)
- captura qualquer palavra: \p{L}+
- captura texto contido em um range de palavras: [\s\S]+? 
	- Exemplo: Impostos\s*Valor([\s\S]+?)Grandeza (tudo que estiver contido entre 'Impostos Valor' e 'Grandeza' será capturado)
-  captura mais de uma opção se identificada:  |
- se for usar sinais gráficos (ponto, vírgula, barra, etc) gosto sempre de usar contra barra (\) antes
	- Exemplo: \- \/ \(
- captura tabulação no texto (tab): \t

## Troubleshooting
