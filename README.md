# Nosso Boilerplate do NextJS

## 0. Para criar um projeto a partir deste boilerplate  

```bash
yarn create next-app -e https://github.com/AugustoCustodio/boilerplate
```

Após executar o comando acima basta informar o nome do projeto.

E pronto já pode começar a codar!

# Agora se quiser saber mais a fundo como este boilerplate foi criado leia as seções abaixo:
## 1.1. Requisitos do projeto

É necessário ter instalado na sua máquina as seguintes ferramentas

1. NodeJs
2. Yarn para gerenciar os pacotes

## 1.2. Criando o boilerplate com create-next-app

Para criar um projeto em NextJs basta rodar o seguinte comando no terminal:

```bash
npx create-next-app
```

## 1.3. Configurando TypeScript no nosso projeto

O primeiro passo é criar o arquivo **tsconfig.json*,*** para isto basta digitar o seguinte comando no terminal

```bash
touch tsconfig.json
```

Logo após é necessário executar o comando:

```bash
yarn dev
```

Uma mensagem irá surgir uma alertando que o projeto ainda não possui os pacotes necessários

![Untitled](Estudos%20Curso%20NextJs%20avanc%CC%A7ado%201dae3e762a1a49818fb0d42d8320c39c/Untitled.png)

Logo é necessário a instalação destes 3 pacotes:

```bash
yarn add --dev typescript @types/react @types/node
```

A partir deste momento precisamos criar qualquer arquivo *.js*  como *.tsx.*

Dentro dos arquivos precisamos adicionar os tipos das nossas props, por exemplo:

```tsx
import Head from 'next/head'
import Image from 'next/image'
import styles from '../styles/Home.module.css'

**type Props = {
  title: string
}**

export default function **Home({ title }: Props) {**
  return (
    <div className={styles.container}>
      <Head>
        <title>Create Next App</title>
        <meta name="description" content="Generated by create next app" />
        <link rel="icon" href="/favicon.ico" />
      </Head>

      <main className={styles.main}>
        <h1 className={styles.title}>
          Welcome to <a href="https://nextjs.org">React Avançado ou NextJs na prática!</a>
        </h1>

        <p className={styles.description}>
          Get started by editing{' '}
          <code className={styles.code}>pages/index.js</code>
        </p>

        <div className={styles.grid}>
          <a href="https://nextjs.org/docs" className={styles.card}>
            <h2>Documentation &rarr;</h2>
            <p>Find in-depth information about Next.js features and API.</p>
          </a>

          <a href="https://nextjs.org/learn" className={styles.card}>
            <h2>Learn &rarr;</h2>
            <p>Learn about Next.js in an interactive course with quizzes!</p>
          </a>

          <a
            href="https://github.com/vercel/next.js/tree/master/examples"
            className={styles.card}
          >
            <h2>Examples &rarr;</h2>
            <p>Discover and deploy boilerplate example Next.js projects.</p>
          </a>

          <a
            href="https://vercel.com/new?utm_source=create-next-app&utm_medium=default-template&utm_campaign=create-next-app"
            className={styles.card}
          >
            <h2>Deploy &rarr;</h2>
            <p>
              Instantly deploy your Next.js site to a public URL with Vercel.
            </p>
          </a>
        </div>
      </main>

      <footer className={styles.footer}>
        <a
          href="https://vercel.com?utm_source=create-next-app&utm_medium=default-template&utm_campaign=create-next-app"
          target="_blank"
          rel="noopener noreferrer"
        >
          Powered by{' '}
          <span className={styles.logo}>
            <Image src="/vercel.svg" alt="Vercel Logo" width={72} height={16} />
          </span>
        </a>
      </footer>
    </div>
  )
}
```

## 1.4. Configurando o EditorConfig

---

O EditorConfig é responsável por definir regras iniciais para o editor, por exemplo, tamanho da identação, se vamos utilizar tabs ou espaços para editar os arquivos.

```bash
# editorconfig.org
root = true

[*]
indent-style = spaces
indent_size = 2
end_of_line = lf
charset = utf-8
trim_trailing_whitespace = true
insert_final_newline = true
```

## 1.5. Configurando EsLint

---

É muito importante para verificação de inconsistência, ele irá nos informar se estamos usando hooks de forma errada, se os componentes estão criados de forma errada. Ele nos informa dos erros sublinhando os erros para que possamos fazer as correções.

Vamos lá, para instalar basta executar o comando no terminal

```bash
npx eslint --init
```

Uma série de perguntas para configuração serão realizadas e precisamos respondê-las de acordo com as convenções do nosso projeto, no final do processo será informado uma série de pacotes que precisamos instalar com o yarn

```bash
yarn add --dev eslint-plugin-react@latest @typescript-eslint/eslint-plugin@latest @typescript-eslint/parser@latest
```

Logo após você poderá configurar o seu arquivo eslintrc.json

```json
{
  "name": "boilerplate",
  "version": "0.1.0",
  "private": true,
  "scripts": {
    "dev": "next dev",
    "build": "next build",
    "start": "next start",
    "lint": "eslint src"
  },
  "dependencies": {
    "next": "11.1.2",
    "react": "17.0.2",
    "react-dom": "17.0.2"
  },
  "devDependencies": {
    "@types/node": "^16.11.1",
    "@types/react": "^17.0.30",
    "@typescript-eslint/eslint-plugin": "^5.1.0",
    "@typescript-eslint/parser": "^5.1.0",
    "eslint": "7.32.0",
    "eslint-config-next": "11.1.2",
    "eslint-plugin-react": "^7.26.1",
    "eslint-plugin-react-hooks": "^4.2.0",
    "typescript": "^4.4.4"
  }
}
```

---

## 1.6. Instalando Prettier

Seguir os passos que estão no site da Prettier [https://prettier.io/docs/en/install.html](https://prettier.io/docs/en/install.html)

```bash
yarn add --dev --exact prettier
```

De modo prático os passos são:

1. Instalar o Prettier
2. Instalar os plugins "eslint-config-prettier" e o "eslint-plugin-prettier"
3. E depois configurar o arquivo .prettierrc

```json
{
  "trailingComma": "none",
  "semi": false,
  "singleQuote": true
}
```

---

1. Dentro do .eslintrc.json adicione a extensão dos plugins

```json
"extends": [
"plugin:prettier/recommended"
]
```

1. Dentro da pasta .vscode no arquivo settings.json as seguintes configurações

```json
{
  "editor.formatOnSave": false,
  "editor.codeActionsOnSave": {
    "source.fixAll": true
  }
}
```

## 1.7. Instalando o Husky

O Husky executa uma série de comandos para facilitar as correções após a edição do código, para isto iremos utilizar o Husky que é um git hook, e o lint-staged que é similar a um task runner. 

Para instalar o Husky, execute o seguinte comando:

```bash
yarn add husky --dev
```

E logo após executar o comando

```bash
yarn husky init
```

Neste momento o Husky está instalado, podemos seguir com a instalação do lint-staged, para isto basta executar o seguinte comando:

```bash
yarn add lint-staged --dev
```

Todo momento em que um commit ser feito, todos os comandos que estiverem no objeto "lint-staged" no arquivo package.json serão executados

 

```json
{
  "name": "boilerplate",
  "version": "0.1.0",
  "private": true,
  "scripts": {
    "dev": "next dev",
    "build": "next build",
    "start": "next start",
    "lint": "eslint src"
  },
  "lint-staged":{
    "src/**/*": ["yarn lint --fix"]
  },
  "dependencies": {
    "next": "11.1.2",
    "react": "17.0.2",
    "react-dom": "17.0.2"
  },
  "devDependencies": {
    "@types/node": "^16.11.1",
    "@types/react": "^17.0.30",
    "@typescript-eslint/eslint-plugin": "^5.1.0",
    "@typescript-eslint/parser": "^5.1.0",
    "eslint": "7.32.0",
    "eslint-config-next": "11.1.2",
    "eslint-config-prettier": "^8.3.0",
    "eslint-plugin-prettier": "^4.0.0",
    "eslint-plugin-react": "^7.26.1",
    "eslint-plugin-react-hooks": "^4.2.0",
    "husky": "^7.0.4",
    "lint-staged": "^11.2.4",
    "prettier": "2.4.1",
    "typescript": "^4.4.4"
  }
}
```

## 1.8. Instalando e usando o JEST

Jest é uma  ferramenta que nos ajuda a executar testes automáticos em JavaScript, irmos utilizar o Jest para Babel e TypeScript. Logo precisamos instalar com o seguinte comando:

```bash
yarn add --dev jest @babel/preset-typescript @types/jest
```

Logo após a instalação precisamos atualizar o arquivo .*eslinttrc.json,*  adicionando no objeto env o Jest e o Node, logo o conteúdo do nosso arquivo deverá ser:

```json
{
    "env": {
        "browser": true,
        "es2021": true,
        "jest": true,
        "node": true
    },
    "settings": {
        "react": {
            "version": "detect"
        }
    },
    "extends": [
        "eslint:recommended",
        "plugin:react/recommended",
        "plugin:@typescript-eslint/eslint-recommended",
        "plugin:@typescript-eslint/recommended",
        "plugin:prettier/recommended"
    ],
    "parser": "@typescript-eslint/parser",
    "parserOptions": {
        "ecmaFeatures": {
            "jsx": true
        },
        "ecmaVersion": 12,
        "sourceType": "module"
    },
    "plugins": [
        "react",
        "@typescript-eslint",
        "react-hooks"
    ],
    "rules": {
        "react-hooks/rules-of-hooks": "error",
        "react-hooks/exhaustive-deps": "warn",
        "react/prop-types": "off",
        "react/react-in-jsx-scope": "off",
        "@typescript-eslint/explicit-module-boundary-types": "off"
    }
}
```

Precisamos criar um arquivo de configuração do Jest com o nome de *jest.config.js* com a exportação dos módulos, note que precisamos também criar um arquivo de .jest/setup.ts

```json
module.exports = {
  testEnvironment: 'jsdom',
  testPathIgnorePatterns: ['/node_modules/', '/.next/'],
  collectCoverage: true,
  collectCoverageFrom: ['src/**/*.ts(x)'],
  setupFilesAfterEnv: ['<rootDir>/.jest/setup.ts']
}
```

## 1.9. Instalando React Test Library

O React Testing Library nos ajuda a manter componentes React Sustentáveis por meio de testes automáticos. O comando para instalação é:

```bash
yarn add --dev @testing-library/react @testing-library/jest-dom
```

Nós também iramos utilizar o [Jest-Dom matchers](https://github.com/testing-library/jest-dom) que facilitam a  nossa verificação.

Depois de instalados precisamos adicionar a importação da biblioteca no nosso arquivo setup.ts

```bash
import '@testing-library/jest-dom'
```

O react testing library nos trás uma cheat sheet para que a gente possa criar componentes sustentáveis, e como capturar os elementos para teste.

[cheat-sheet.pdf](Estudos%20Curso%20NextJs%20avanc%CC%A7ado%201dae3e762a1a49818fb0d42d8320c39c/cheat-sheet.pdf)

Neste momento, podemos escrever nossos testes no arquivo test.tsx

```jsx
import { render, screen } from '@testing-library/react'

import Main from '.'

describe('<Main />', () => {
  it('should render the heading', () => {
    const { container } = render(<Main />)

    expect(
      screen.getByRole('heading', { name: /react avançado/i })
    ).toBeInTheDocument()

    expect(container.firstChild).toMatchSnapshot()
  })

  it('should render the colors correctly', () => {
    const { container } = render(<Main />)

    expect(container.firstChild).toHaveStyle({ 'background-color': '#06092b' })
  })
})
```

Também é preciso garantir que os comandos estão no nosso package.json

## 1.10. Instalando Styled Components e configurando o SSR

É importante configurar o Server Side Rendering para o Styled componente pois assim evitamos a quebra da estilização da página. Por exemplo, quando acessamos a página e ela está com a estilização quebrada? Isto acontece, pois a renderização não está acontecendo do lado do servidor para os Styled Componets, por este motivo é muito importante configurar antes o SSR. Veja como a seguir:

- Como iremos usar Typescript é muito importante instalar os types para o Style Componentes e também o plugin para o Babbel, e dentro do Plugin do Babbel Teremos o SSR. Pois bem para instalar execute o comando no terminal:

```jsx
yarn add --dev @types/styled-components babel-plugin-styled-components
```

E conforme documentação [https://styled-components.com/docs/tooling](https://styled-components.com/docs/tooling) precisamos atualizar nosso arquivo .babelrc, muito importante configurar o ssr para true

```jsx
{
  "plugins": [
    [
      "babel-plugin-styled-components",
      {
        "ssr": true
      }
    ]
  ],
  "presets": ["next/babel", "@babel/preset-typescript"]
}
```

E logo em seguida, precisamos instalar o styled-components com o comando

```bash
yarn add styled-components
```

Para o SSR funcionar no NextJs precisamos adicionar algumas informações no nosso arquivo _document.js, conforme pode ser visto na documentação [https://styled-components.com/docs/advanced#server-side-rendering](https://styled-components.com/docs/advanced#server-side-rendering) bem como no documento de referência no github [https://github.com/vercel/next.js/blob/master/examples/with-styled-components/pages/_document.js](https://github.com/vercel/next.js/blob/master/examples/with-styled-components/pages/_document.js)

```tsx
import Document, {
  DocumentContext,
  Html,
  Head,
  Main,
  NextScript
} from 'next/document'
import { ServerStyleSheet } from 'styled-components'

export default class MyDocument extends Document {
  static async getInitialProps(ctx: DocumentContext) {
    const sheet = new ServerStyleSheet()
    const originalRenderPage = ctx.renderPage

    try {
      ctx.renderPage = () =>
        originalRenderPage({
          enhanceApp: (App) => (props) =>
            sheet.collectStyles(<App {...props} />)
        })

      const initialProps = await Document.getInitialProps(ctx)
      return {
        ...initialProps,
        styles: (
          <>
            {initialProps.styles}
            {sheet.getStyleElement()}
          </>
        )
      }
    } finally {
      sheet.seal()
    }
  }
  render() {
    return (
      <Html lang="pt-BR">
        <Head />
        <body>
          <Main />
          <NextScript />
        </body>
      </Html>
    )
  }
}
```

## 1.11. Criando estilos globais, createGlobalStyle

Para criar um estilo global nós utilizaremos um helper que pode ser verificado na documentação.

Podemos criar um arquivo _app.tsx do NextJs para facilitar a importação, pois tudo que há neste documento é renderizado em todas as páginas da aplicação. Vide documentação [Advanced Features: Custom `App` | Next.js (nextjs.org)](https://nextjs.org/docs/advanced-features/custom-app)

```tsx
import { AppProps } from 'next/app'
import Head from 'next/head'

import GlobalStyles from 'styles/global'

function App({ Component, pageProps }: AppProps): JSX.Element {
  return (
    <>
      <Head>
        <title>React Avançado - Boilerplate</title>
        <link rel="shortcut icon" href="/img/icon-512.png" />
        <link rel="apple-touch" href="/img/icon-512.png" />
        <meta
          name="description"
          content="A simple project starter to work with TypeScript and React"
        />
      </Head>
      <GlobalStyles />
      <Component {...pageProps} />
    </>
  )
}

export default App
```

Para evitar o uso de pontos nos imports do nosso projeto. or exemplo, é muito comum o uso de *../styles/global* pode ser substituído por *styles/global* para tanto precisamos adicionar uma basURL no nosso arquivo *tsconfig.json*

```json
{
  "compilerOptions": {
    **"baseUrl": "src",**
    "target": "es5",
    "lib": [
      "dom",
      "dom.iterable",
      "esnext"
    ],
    "allowJs": true,
    "skipLibCheck": true,
    "strict": false,
    "forceConsistentCasingInFileNames": true,
    "noEmit": true,
    "esModuleInterop": true,
    "module": "esnext",
    "moduleResolution": "node",
    "resolveJsonModule": true,
    "isolatedModules": true,
    "jsx": "preserve"
  },
  "include": [
    "next-env.d.ts",
    "**/*.ts",
    "**/*.tsx"
  ],
  "exclude": [
    "node_modules"
  ]
}
```

## 1.12. Criando estilos do primeiro componente

Dentro da nossa pasta de src/componetes/Main nós criamos o arquivo *styles.ts* que é nosso arquivo de estilos. 

```tsx
import styled from 'styled-components'

export const Wrapper = styled.main`
  background-color: #06092b;
  color: #fff;
  width: 100%;
  height: 100%;
`

export const Logo = styled.img``

export const Title = styled.h1``

export const Description = styled.h2``

export const Ilustration = styled.img``
```

E para efetivamente utilizar os estilos precisamos importar na nossa Main

```tsx
import * as S from './styles'

const Main = () => (
  <S.Wrapper>
    <h1>React Avançado</h1>
  </S.Wrapper>
)

export default Main
```

Para facilitar a legibilidade do nosso código nós iremos instalar o plugin do Styled Components para o Jest

```tsx
yarn add --dev jest-styled-components
```

E dentro do nosso arquivo .jest/setup.ts, fazemos a importação:

```tsx
import '@testing-library/jest-dom'
import 'jest-styled-components'
```

## 1.13. Instalando e configurando o Storybook

O comando para instalar o Storybook é:

```bash
npx -p @storybook/cli sb init --type react
```

---

E como no nosso projeto utilizamos o Typescript nós precisamos instalar o preset do Typecript(Na versão 6 do storybook, isto não é mais necessário)

```bash
yarn add --dev @storybook/preset-typescrip
```

Após estas configurações uma pasta chamada .storybook será criada com um arquivo main.js com as configurações iniciais e também nossos addons

Precisamos adicionar a pasta de imagens no nosso package.json

```bash
{
  "name": "boilerplate",
  "version": "0.1.0",
  "private": true,
  "scripts": {
    "dev": "next dev",
    "build": "next build",
    "start": "next start",
    "lint": "eslint src",
    "test": "jest",
    "test:watch": "yarn test --watch",
    **"storybook": "start-storybook -s ./public -p 6006",**
    "build-storybook": "build-storybook"
  },
  "lint-staged": {
    "src/**/*": [
      "yarn lint --fix",
      "yarn test --findRelatedTests --bail"
    ]
  },
  "dependencies": {
    "next": "11.1.2",
    "react": "17.0.2",
    "react-dom": "17.0.2",
    "styled-components": "^5.3.3"
  },
  "devDependencies": {
    "@babel/core": "^7.16.0",
    "@babel/preset-typescript": "^7.15.0",
    "@storybook/addon-actions": "^6.3.12",
    "@storybook/addon-essentials": "^6.3.12",
    "@storybook/addon-links": "^6.3.12",
    "@storybook/preset-typescript": "^3.0.0",
    "@storybook/react": "^6.3.12",
    "@testing-library/jest-dom": "^5.14.1",
    "@testing-library/react": "^12.1.2",
    "@types/jest": "^27.0.2",
    "@types/node": "^16.11.1",
    "@types/react": "^17.0.30",
    "@types/styled-components": "^5.1.15",
    "@typescript-eslint/eslint-plugin": "^5.1.0",
    "@typescript-eslint/parser": "^5.1.0",
    "babel-loader": "^8.2.3",
    "babel-plugin-styled-components": "^1.13.3",
    "eslint": "7.32.0",
    "eslint-config-next": "11.1.2",
    "eslint-config-prettier": "^8.3.0",
    "eslint-plugin-prettier": "^4.0.0",
    "eslint-plugin-react": "^7.26.1",
    "eslint-plugin-react-hooks": "^4.2.0",
    "husky": "^7.0.4",
    "jest": "^27.3.1",
    "jest-styled-components": "^7.0.5",
    "lint-staged": "^11.2.4",
    "prettier": "2.4.1",
    "typescript": "^4.4.4"
  }
}
```

## 1.14. Configurando PWA

Para fazer da nossa aplicação NextJs em PWA nós utilizamos a biblioteca Next-PWA [next-pwa - npm (npmjs.com)](https://www.npmjs.com/package/next-pwa) 

Logo, primeiro passo é instalar usando o Yarn

```bash
yarn add next-pwa
```

Após instalado precisamos criar e configurar nosso arquivo next.config.js

```bash
// eslint-disable-next-line @typescript-eslint/no-var-requires
const withPWA = require('next-pwa')
const isProd = process.env.NODE_ENV === 'production'

module.exports = withPWA({
  pwa: {
    dest: 'public',
    disable: !isProd
  }
})
```

Logo após precisamos criar o nosso arquivo de manifest.json no nosso public

```json
{
    "name": "React Avançado - Boilerplate",
    "short_name": "React Avançado",
    "icons": [
        {
            "src": "/img/icon-192.png",
            "type": "image/png",
            "sizes": "192x192"
        },
        {
            "src": "/img/icon-512.png",
            "type": "image/png",
            "sizes": "512x512"
        }
    ],
    "background_color": "#06092B",
    "description": "Boilerlate utilizando Typescript, React, NextJS e Styled Components!",
    "display": "fullscreen",
    "start_url": "/",
    "theme_color": "#06092B"
}
```

Para testar e verificar se os Service Workers estão funcionando como deveriam, basta gerar uma versão de produção, use o comando no terminal

```json
NODE_ENV=production yarn build
```

Logo após

```json
yarn start
```

Inspecione o aplicativo usando o Lighthouse

![Untitled](Estudos%20Curso%20NextJs%20avanc%CC%A7ado%201dae3e762a1a49818fb0d42d8320c39c/Untitled%201.png)