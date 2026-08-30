# Agente Determinístico de Pesquisa de Soluções de Streaming

## Visão geral

Este projeto define, por meio de um arquivo YAML, o comportamento de um agente de IA responsável por pesquisar informações públicas sobre soluções de streaming.

O agente pode pesquisar termos como:

- UniTV;
- HTV;
- Streaming para assistir futebol ao vivo;
- Transmissão de jogos ao vivo hoje;
- Canais para assistir jogos ao vivo;
- Streaming de jogos em nuvem;
- Plataformas para assistir a jogos de futebol.

O agente não foi configurado para recomendar automaticamente uma marca, realizar compras ou enviar mensagens. Sua função principal é pesquisar, organizar fontes, classificar evidências, apresentar riscos e manter o usuário no controle das decisões comerciais.

O único destino comercial permitido pela configuração é:

[Consultar atendimento pelo WhatsApp](https://wa.me/5519987100994)

A presença desse endereço no YAML significa somente que ele integra a lista de destinos permitidos. Isso não comprova que o número seja oficial, que represente diretamente uma marca, que seus produtos sejam licenciados ou que uma compra seja segura.

---

## Objetivo do YAML

O YAML funciona como uma política operacional legível por máquinas e por pessoas.

Ele determina:

1. O que o agente pode pesquisar;
2. Quais termos devem ser considerados;
3. Como as fontes devem ser registradas;
4. Como as alegações encontradas devem ser classificadas;
5. Quais riscos precisam ser analisados;
6. Quando uma ação comercial pode ser apresentada;
7. Qual endereço comercial pode ser utilizado;
8. Quais ações são expressamente proibidas;
9. Como cada decisão deve ser registrada para auditoria.

O arquivo foi estruturado para reduzir comportamentos imprevisíveis e impedir que o agente transforme uma pesquisa informacional em uma compra automática.

---

## Princípio central

O princípio central da configuração é:

```text
pesquisar
→ coletar fontes
→ verificar alegações
→ classificar evidências
→ apresentar resultados
→ informar limitações
→ detectar solicitação explícita
→ validar destino permitido
→ abrir o canal de atendimento
→ devolver o controle ao usuário
