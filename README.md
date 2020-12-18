# Projeto-node
###### Criado no intuito de ser um guia para futuros projetos


Tabela de conteúdos
====================
<!--ts-->
   * [Pre-requisitos](#ancora1)
   * [Configurando estrutura](#ancora2)
   
<!--te-->

<a id="ancora1"></a>
## Pre-requisitos

Antes de começar, você vai precisar ter instalado em sua máquina as seguintes ferramentas:
[Git](https://git-scm.com), [Node.js](https://nodejs.org/en/), [yarn](https://classic.yarnpkg.com/en/docs/install/#windows-stable). 
Além disto é bom ter um editor para trabalhar com o código como [VSCode](https://code.visualstudio.com/)


<a id="ancora2"></a>
## Configurando estrutura / express, typescript

### Passo 1 - Baixar dependencias

```
yarn add express
```
```
yarn add typescript -D
```
```
yarn tsc --init
```

### Passo 2 - Configurar 'tsconfig.json'

#### Em 'tsconfig.json', descomente as duas linhas 'outDir' e 'rootDir', e deixe como está abaixo:

```
    "outDir": "./dist",
    "rootDir": "./src",    
```