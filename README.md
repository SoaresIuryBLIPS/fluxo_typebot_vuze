# Documentação do Fluxo Typebot: E-com Vuze

## Visão Geral
Este documento descreve o fluxo de trabalho do bot "E-com Vuze" criado no Typebot. O bot foi projetado para auxiliar os usuários na navegação e seleção de equipamentos, seja para compra ou aluguel, fornecendo informações e coletando dados relevantes para o contato com o time comercial.

## Estrutura do Fluxo
O fluxo está organizado em diversos **grupos** e **eventos**. Cada grupo contém **blocos** que representam ações, como mensagens de texto, entrada de dados ou conexões externas. 

### Grupos Principais
1. **CURIOSIDADE**
   - Exibe uma saudação personalizada baseada no horário do dia.
   - Apresenta o bot como assistente virtual da Vuze Equipamentos.
   - Pergunta se o usuário deseja comprar ou alugar equipamentos.

2. **FITNESS**
   - Lista opções de equipamentos fitness mais procurados.
   - Permite que o usuário escolha entre diferentes tipos de esteiras e escadas.

3. **COMUNICAÇÃO VISUAL (CV)**
   - Oferece opções relacionadas a plotters, lasers e outros equipamentos para comunicação visual.

4. **CONFECÇÃO**
   - Direciona o usuário para categorias de equipamentos, como plotters de impressão e impressoras DTF.

5. **SORVETE**
   - Apresenta equipamentos relacionados à produção e armazenamento de sorvetes.

6. **CONSTRUÇÃO CIVIL**
   - Lista mini escavadeiras disponíveis para aluguel ou compra.

### Coleta de Dados
No final de cada interação, o bot coleta as seguintes informações:
- Nome completo
- Telefone (com DDD)
- E-mail
- CNPJ

Esses dados são enviados para o time comercial por meio de um webhook.

## Funcionalidades Especiais
- **Saudação Dinâmica:** Utiliza um script para determinar a saudação baseada na hora do dia.
- **Entradas Dinâmicas:** Os usuários podem selecionar equipamentos ou inserir informações nos campos solicitados.
- **Webhook:** Integração com o sistema externo para envio dos dados coletados.

## Estrutura do Código
Cada grupo é definido por um conjunto de blocos, que podem incluir:
- Mensagens de texto (`text`)
- Inputs de escolha (`choice input`)
- Inputs de texto ou número (`text input`, `number input`)
- Configurações de variáveis (`Set variable`)
- Conexões externas (`Webhook`)

### Exemplo de Bloco
#### Saudação
```json
{
  "id": "j9vd4aa745ptfb4rv29fa5ce",
  "type": "Set variable",
  "options": {
    "variableId": "vhelqw62p87e0zh1ahbttdvut",
    "isExecutedOnClient": false,
    "expressionToEvaluate": "const agora = new Date(); const horaAtual = agora.toLocaleString('pt-BR', { timeZone: 'America/Sao_Paulo', hour: 'numeric', hour12: false }); let saudacao; if (horaAtual >= 5 && horaAtual < 12) { saudacao = \"Bom diaaa\"; } else if (horaAtual >= 12 && horaAtual < 18) { saudacao = \"Boa tardeee\"; } else { saudacao = \"Boa noiteee\"; } return saudacao;",
    "isCode": true
  }
}
