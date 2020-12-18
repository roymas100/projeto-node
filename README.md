# Projeto-node
###### Criado no intuito de ser um guia para futuros projetos


Tabela de conteúdos
====================
<!--ts-->
   * [Pre-requisitos](#ancora1)
   * [Configurando estrutura](#ancora2)

<!--te-->

<a id="ancora1"></a>
# Pre-requisitos

Antes de começar, você vai precisar ter instalado em sua máquina as seguintes ferramentas:

* <b> [Git](https://git-scm.com),
* [Node.js](https://nodejs.org/en/),
* [yarn](https://classic.yarnpkg.com/en/docs/install/#windows-stable).
</b>

Além disto é bom ter um editor para trabalhar com o código como:
* <b>[VSCode](https://code.visualstudio.com/)</b>.


<a id="ancora2"></a>
# Configurando estrutura / express, typescript

## Passo 1 - Baixar dependencias

```
yarn add express
```
```
yarn add typescript @types/express -D
```
```
yarn tsc --init
```

###### Obs.: Quando tiver alguma dependencia que não está sendo lida, tente " @type/xxxx -D ".

## Passo 2 - Configurar 'tsconfig.json'

#### Em 'tsconfig.json', descomente as duas linhas 'outDir' e 'rootDir', e deixe como está abaixo:

```
    "outDir": "./dist",
    "rootDir": "./src",
```

## Passo 3 - Configurar scripts no 'package.json'

### Instale a dependencia como desenvolvimento:

```
yarn add ts-node-dev -D
```

### Vá ao "package.json" e adicione os scripts conforme abaixo:

```
{
  ...
  "scripts": {
    "build": "tsc",
    "dev:server": "ts-node-dev --transpile-only --ignore-watch node_modules src/server.ts"
  },
  ...
}
```

## Configurando EditorConfig, ESlint e Prettier

* [EditorConfig, ESlint e Prettier](https://www.notion.so/Padr-es-de-projeto-com-ESLint-Prettier-e-EditorConfig-0b57b47a24724c859c0cf226aa0cc3a7)
