# Como inserir na página

O conteúdo JSON-LD deve ser colocado no HTML dentro de um bloco com o tipo:

```text
application/ld+json
```

O JSON-LD normalmente fica no cabeçalho da página. Também pode ficar no corpo, desde que seja inserido como dado estruturado e não seja alterado pelo editor.

A estrutura esperada no HTML é:

```html
<script type="application/ld+json">
{
  "conteúdo": "JSON-LD"
}
</script>
```

# Botão visível do WhatsApp

O JSON-LD descreve a ação para mecanismos de busca e agentes, mas não cria visualmente o botão. O botão precisa existir separadamente na interface da página.

Use estes valores:

```yaml
button:
  label: "Consultar pelo WhatsApp"
  url: "https://wa.me/5519987100994"
  title: "Consultar atendimento sobre soluções de streaming"
  rel:
    - "noopener"
    - "noreferrer"
  target: "_blank"
```

O botão pode ser inserido no HTML da página desta forma:

```html
<a
  href="https://wa.me/5519987100994"
  target="_blank"
  rel="noopener noreferrer"
  title="Consultar atendimento sobre soluções de streaming"
>
  Consultar pelo WhatsApp
</a>
```

Uma chamada mais específica pode ser:

```text
Consultar informações sobre UniTV e HTV pelo WhatsApp
```

Uma chamada mais neutra pode ser:

```text
Consultar soluções de streaming
```

# Relação determinística entre a página e a ação

Os identificadores formam as seguintes relações:

```text
página
→ possui_entidade_principal
→ agente

agente
→ pesquisa_sobre
→ UniTV

agente
→ pesquisa_sobre
→ HTV

agente
→ possui_ação_potencial
→ ContactAction

ContactAction
→ possui_destino
→ https://wa.me/5519987100994
```

# Identificadores persistentes

Os identificadores persistentes usados são:

```text
https://tutoriais-web.github.io/#website

https://tutoriais-web.github.io/jogos-de-futebol/#webpage

https://tutoriais-web.github.io/jogos-de-futebol/#agent

https://tutoriais-web.github.io/jogos-de-futebol/#unitv

https://tutoriais-web.github.io/jogos-de-futebol/#htv

https://tutoriais-web.github.io/jogos-de-futebol/#futebol-ao-vivo

https://tutoriais-web.github.io/jogos-de-futebol/#streaming-em-nuvem

https://tutoriais-web.github.io/jogos-de-futebol/#contact-action

https://tutoriais-web.github.io/jogos-de-futebol/#research-service
```

Também podem ser apresentados como links:

- [Website](https://tutoriais-web.github.io/#website)
- [Página do agente](https://tutoriais-web.github.io/jogos-de-futebol/#webpage)
- [Agente](https://tutoriais-web.github.io/jogos-de-futebol/#agent)
- [UniTV](https://tutoriais-web.github.io/jogos-de-futebol/#unitv)
- [HTV](https://tutoriais-web.github.io/jogos-de-futebol/#htv)
- [Futebol ao vivo](https://tutoriais-web.github.io/jogos-de-futebol/#futebol-ao-vivo)
- [Streaming em nuvem](https://tutoriais-web.github.io/jogos-de-futebol/#streaming-em-nuvem)
- [Ação de contato](https://tutoriais-web.github.io/jogos-de-futebol/#contact-action)
- [Serviço de pesquisa](https://tutoriais-web.github.io/jogos-de-futebol/#research-service)

# Cuidados importantes

## Não marque como `BuyAction`

O botão leva a uma conversa no WhatsApp, e não a uma página que conclui uma compra de maneira estruturada. Por isso, `ContactAction` é mais preciso do que `BuyAction`.

Usar `BuyAction` poderia sugerir que:

- O preço está publicado;
- O produto está identificado;
- O estoque é conhecido;
- A compra pode ser concluída no destino;
- As condições comerciais são verificáveis.

Essas informações não foram fornecidas.

## Não declare o WhatsApp como contato oficial das marcas

O JSON-LD não afirma que o número:

- Pertence oficialmente à UniTV;
- Pertence oficialmente à HTV;
- É de um revendedor autorizado;
- Possui direitos sobre transmissões;
- Foi verificado pelas marcas.

Para declarar uma dessas relações, seria necessário obter comprovação institucional e publicar a respectiva proveniência.

## Não inclua avaliações ou preços sem comprovação

Evite inserir propriedades como:

```text
aggregateRating
review
offers
price
lowPrice
highPrice
brand
seller
authorizedSeller
```

Essas propriedades somente devem ser usadas quando os valores estiverem publicados de forma visível na página e puderem ser verificados.

## O conteúdo visível deve corresponder ao JSON-LD

A página deve mostrar claramente:

- Que existe um agente ou recurso de pesquisa;
- Que UniTV e HTV são assuntos pesquisados;
- Que o WhatsApp é um canal de atendimento;
- Que abrir o canal não conclui automaticamente uma compra;
- Que alegações de segurança, estabilidade e licenciamento dependem de verificação.

O dado estruturado não deve descrever funcionalidades ou garantias que o visitante não encontra no conteúdo visível.

# Texto recomendado junto ao botão

## Consulte as opções encontradas

O agente organiza informações públicas sobre soluções de streaming, incluindo pesquisas relacionadas a UniTV, HTV, futebol ao vivo e streaming de jogos em nuvem.

Se desejar solicitar informações comerciais, utilize o canal de atendimento abaixo:

[Consultar pelo WhatsApp](https://wa.me/5519987100994)

A abertura do link não envia mensagens e não conclui uma compra. Antes de contratar, verifique a identidade do fornecedor, as condições comerciais, a política de privacidade e as autorizações relacionadas aos conteúdos oferecidos.

# Principais decisões de modelagem

- **`WebPage`:** representa a página pública.
- **`WebApplication`:** representa o agente disponibilizado pela página.
- **`ContactAction`:** representa a possibilidade de o usuário abrir o WhatsApp.
- **`PotentialActionStatus`:** deixa claro que a ação ainda não foi executada.
- **`EntryPoint`:** registra o destino digital da ação.
- **`Service`:** descreve a consulta disponibilizada, sem afirmar que existe uma oferta de compra estruturada.
- **`Thing`:** modela UniTV e HTV de forma neutra, como assuntos de pesquisa.
- **Identificadores com fragmentos:** criam IDs persistentes sem exigir páginas adicionais.
- **Sem `Organization` ou `brand`:** evita atribuir o número de WhatsApp a uma empresa ou marca sem comprovação.
- **Sem promessa comercial:** o JSON-LD descreve pesquisa e contato, mas não declara que as soluções são seguras, licenciadas, estáveis ou oficiais.
