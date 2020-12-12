# Responsividade na Prática | Masterclass</h1>
Repositório dedicado à prática da masterclass "Responsividade na Prática", do Mayk Brito, que mostra como usar estratégias do CSS para que tanto o layout, quanto os textos, fiquem fluidos.

Você pode acessar a aula através desse link: <a href="https://www.youtube.com/watch?v=H91DhKPjhPk">https://www.youtube.com/watch?v=H91DhKPjhPk</a><br>

## O que responsividade?

Responsividade é um conceito muito importante no desenvolvimento web. Um site responsivo é aquele que tem seu contéudo adaptado de acordo com o tamanho da tela do usuário. Assim, independente do dispositivo que estiver utilizando, a página será carregada sem erros e com uma navegação agradável.

A responsividade vai além do simples redimensionamento do conteúdo, e pode envolver mudança no tamanho de fontes, links, botões, e a ocultação e redistribuição de determinados elementos.

Uma boa forma de testar a responsividade de um site é utilizar as ferramentas de emulação de dispositivos móveis, presente na maioria dos navegadores.

<div align="center">
  <img src="https://developers.google.com/web/tools/chrome-devtools/device-mode/imgs/iphone-frame.png?hl=pt-br" width="700"/>
</div>

## Unidades no CSS
É possível usar muitas unidades de medida no CSS, para diversos fins. Podemos agrupar as unidades em dois tipos: **medidas absolutas** e **medidas relativas**.

Enquanto que as medidas absolutas são fixas - não dependendo de um valor de referência - as medidas relativas são calculadas com base em outras unidades de medida, ajudando na construção de layouts fluidos.

Medidas absolutas:
- `px` - Pixel
- `pt` - Point
- `in` - Inch (Polegada)
- `cm` - Centímetro
- `mm` - Milímetro
- `pc` - Paica

Medidas relativas:
- `%` - Porcentagem
- `auto` - Automático
- `vh` - Viewport Height
- `vw` - Viewport Width
- `vmin` - Viewport Minimum
- `vmax` - Viewport Maximum
- `em` - Ems
- `rem` - Root Ems

A medida `em` muda os elementos filhos de acordo com o tamanho do elemento pai, por exemplo:

```html

<div id="pai">
    div pai
    <div id="filho">
        div filho
    </div>
</div>

<style>
    #pai {
        font-size: 16px;
    }

    #filho {
        font-size: 2em; /* 32px */
    }
</style>
```

Parecido com a `em`, a unidade `rem` muda os elementos filhos de acordo com o root (elemento raiz). Um ótimo truque é definir o tamanho do root como 62,5%, facilitando a conversão de `rem` para `px` e posteriormente permitindo que se adapte o tamanho de acordo com as telas.

```css

html {
    font-size: 62,5%;
}

#filho1 {
    font-size: 1.2rem;  /* 12px */
}

#filho2 {
    font-size: 2.4rem; /* 24px */
}
```


## Media Queries

Nem sempre o contéudo vai ser adaptado corretamente, então precisamos forçá-lo através das **media queries** que delimitam alguns tamanhos e ajustam o contéudo. Elas podem ser declaradas tanto através do HTML, na tag `<link>`, quanto no CSS, pela regra `@media`.

```html
<!-- Media no HTML -->
<link rel="stylesheet" media="(max-width: 800px)" href="exemplo.css" />

<!-- Media no CSS -->
<style>
@media (max-width: 600px) 
{
  .exemplo
   {
    display: none;
   }
}
</style>
```

Numa media query, é possível usar operadores lógicos - como `ànd`, `ǹot` e `only` - além de várias outras opções. Por exemplo, para formatar o contéudo do site para impressão existe a opção `print`.

## Imagens Dinâmicas

Uma das preocupações que um desenvolvedor deve ter durante a programação de um site é o consumo de memória. Imagens muito grandes podem ser um problema, por isso é bom evitá-las em situações desnecessárias.

Para ajudar, existem as tags `<picture>` e `<source>` do HTML, que permitem o navegador escolher a imagem mais adequada de acordo com o layout atual da página, caracteristicas do dispositivo em que será exibido, e a habilidade do navegador de renderizar um certo tipo de imagem. A seguir, um exemplo usando o atributo `media`.

```html
<picture class="image" alt="Imagem">
    <source media="(min-width: 768px)" srcset="https://i.ytimg.com/vi/GykTLqODQuU/maxresdefault.jpg" />
    <source media="(min-width: 320px)" srcset="https://i.ytimg.com/vi/GykTLqODQuU/hqdefault.jpg" />
    <source media="(min-width: 10px)" srcset="https://i.ytimg.com/vi/GykTLqODQuU/mqdefault.jpg" />
    <img src="https://i.ytimg.com/vi/GykTLqODQuU/hqdefault.jpg" alt="Imagem" />
</picture>
```

## Vantagens do SVG
Os quatro mformatos de imagem mais populares são: `jpg`, `png`, `gif` e `svg`. Eles podem possuir diversas funcionalidades, como animações, transparência e rasterização. Entre eles, porém, o `svg` se destaca por não perder sua resolução ao ser redimensionado.

<div align="center">
  <img src="https://raw.githubusercontent.com/diegoeis/tableless-static-images/master/2012/11/svg-versus-png.jpg" width="400" />
</div>
