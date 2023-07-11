# Seção 13: Módulo 3: Iniciando o projeto da Won e criando primeiros fundações

## Iniciando o projeto através do Boilerplate

```bash
yarn create next-app -e https://github.com/felipebbarbosa/curso_udemy_react-avancado_boilerplate client
```

Onde:

- `-e <link>`: Flag que diz que é apartir de um exemplo do link do repositório especificado.
- `client`: É o nome do novo projeto gerado apartir do exemplo.


## Utilizando Web Fonts no Next e detalhes

Existem algumas maneiras de carregar uma fonte no seu projeto, seja utilizando um CDN e importando via HTML ou diretamente no CSS; Ou fazendo download da fonte e adicionando no seu código. Essa segunda opção é melhor para no casos de PWA, por exemplo.

> Um ótimo [artigo](https://www.zachleat.com/web/comprehensive-webfonts/) sobre as melhores estratégias de carregamento de fontes

Para facilitar o trabalho caso siga pela segunda opção, o site [google-webfonts-helper](https://gwfh.mranftl.com/fonts) é uma ótima ferramenta de auxilio.

Neste site, você tem a opção de querer atender todos os browsers ou se pretente atender somente os modernos. Aí basta fazer o download, colocar as fontes em `public\fonts` e colocar o código sugerido no arquivo `src\styles\global.ts`, desta forma:

```typescript
import { createGlobalStyle } from 'styled-components'

const GlobalStyles = createGlobalStyle`
  @font-face {
    font-display: swap; /* Check https://developer.mozilla.org/en-US/docs/Web/CSS/@font-face/font-display for other options. */
    font-family: 'Poppins';
    font-style: normal;
    font-weight: 100;
    src: url('/fonts/poppins-v20-latin-100.woff2') format('woff2');
  }

  @font-face {
    font-display: swap; /* Check https://developer.mozilla.org/en-US/docs/Web/CSS/@font-face/font-display for other options. */
    font-family: 'Poppins';
    font-style: normal;
    font-weight: 400;
    src: url('/fonts/poppins-v20-latin-regular.woff2') format('woff2');
  }

  @font-face {
    font-display: swap; /* Check https://developer.mozilla.org/en-US/docs/Web/CSS/@font-face/font-display for other options. */
    font-family: 'Poppins';
    font-style: normal;
    font-weight: 600;
    src: url('/fonts/poppins-v20-latin-600.woff2') format('woff2');
  }


  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }

  html {
    font-size: 62.5%;
  }

  html, body, #__next {
    height: 100%;
  }

  body {
    font-family: 'Poppins', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif
  }
`

export default GlobalStyles
```

### font-display: swap

Uma outra configuração para cada `@font-face` é adicionar a propriedade `font-display: swap;`, isso informa ao browser que pode carregar uma fonte padrão enquanto está carregando a página e troque para fonte de desajada quando o carregamento estiver completo. Por padrão, sem opção, o browser não carrega texto nenhum enquanto a fonte não tiver sido totalmente carregada.

### Corrigindo problema de Antialising

No seletor global de CSS, adicione as seguintes propriedades: 

```css
* {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
```


---

[Voltar](./README.md)