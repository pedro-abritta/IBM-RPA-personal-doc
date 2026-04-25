# 🛠️ Protocolo de Documentação - IBM RPA Wiki

Este arquivo define as regras de estrutura e escrita para garantir que o cofre seja útil tanto para consulta manual quanto para o "Consultor de IA".

## 📂 Estrutura de Pastas
- `00_Templates/`: Modelos `.md` para novos comandos e projetos.
- `01_Projetos/IBM_RPA/`: Documentação de bots na ferramenta IBM RPA (Escopo e Fluxo).
- `02_Base_Conhecimento/IBM_RPA/`: O "como fazer" de comandos específicos.
- `03_Solucoes_e_Erros/`: Registro de bugs e "pulos do gato".

## ⚙️ Regra de Ouro (Anexos)
- **Configuração**: `Settings` > `Files & Links` > `Default location for new attachments` = **"Same folder as current file"**.
- **Uso**: Prints devem ser colados diretamente na nota. O arquivo de imagem DEVE residir na mesma pasta da nota `.md`.

## ✍️ Padrão de Escrita e Imagens
1. **Contexto Visual**: Como o IBM RPA é drag-and-drop, toda lógica complexa deve ter um print.
2. **Descrição para IA**: Abaixo de cada imagem, adicione uma breve descrição textual (ex: "Print do comando 'Wait for Control' com seletor ID X"). Isso permite que ferramentas de busca e IA entendam o conteúdo da imagem.
3. **Wikilinks**: Conecte soluções a projetos usando `[[Nome da Nota]]`.

## 🏷️ Tags Obrigatórias
- `#comando`: Para notas na Base de Conhecimento.
- `#projeto`: Para documentação de bots específicos.
- `#bug-fix`: Para soluções em `03_Solucoes_e_Erros`.
- `#ibm-rpa`: Para assuntos relacionados a projetos e base de conhecimentos sobre IBM_RPA.

---
*Documentação gerada para eficiência técnica. Sem distrações.*