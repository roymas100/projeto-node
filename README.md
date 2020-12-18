# Projeto-node
###### Criado no intuito de ser um guia para futuros projetos


Tabela de conteúdos
====================
<!--ts-->
  * [Pre-requisitos](#ancora1)
  * [Configurando estrutura](#ancora2)
      * [Passo 1 - Baixar dependencias](#ancora2.1)
      * [Passo 2 - Configurar 'tsconfig.json'](#ancora2.2)
      * [Passo 3 - Configurar scripts no 'package.json'](#ancora2.3)
  * [Configurando EditorConfig, ESlint e Prettier](#ancora3)
      * [Configurando EditorConfig](#ancora3.1)
      * [Configurando ESLint](#ancora3.2)
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

<a id="ancora2.1"></a>
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

<a id="ancora2.1Obs"></a>
###### Obs.: Quando tiver alguma dependencia que não está sendo lida, tente " @type/xxxx -D ".

<a id="ancora2.2"></a>
## Passo 2 - Configurar 'tsconfig.json'

#### Em 'tsconfig.json', descomente as duas linhas 'outDir' e 'rootDir', e deixe como está abaixo:

```
    "outDir": "./dist",
    "rootDir": "./src",
```

<a id="ancora2.3"></a>
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

<a id="ancora3"></a>
# Configurando EditorConfig, ESlint e Prettier

Tutorial do Notion - Imagens também de sua autoria.
* [EditorConfig, ESlint e Prettier](https://www.notion.so/Padr-es-de-projeto-com-ESLint-Prettier-e-EditorConfig-0b57b47a24724c859c0cf226aa0cc3a7)

<a id="ancora3.1"></a>
## Configurando EditorConfig

#### Procure nas extensões do VSCode, a extensão ```EditorConfig for VS Code```, assim como a imagem abaixo:

![alt text](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F2184e361-42b6-4019-9d21-0ac456021f02%2Fi1.png?table=block&id=ad3f8cf0-d41f-4f2a-a46f-ddbb1b16c603&width=2750&userId=&cache=v2)

#### Depois de instalada, ao clicar com o botão direito sobre o explorador de arquivos do projeto vamos selecionar a opção ```Generate .editorconfig```

![alt text](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/633a1f68-af6a-4eaf-849e-66f6cc1acae7/editorConfig.gif?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20201218%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20201218T120758Z&X-Amz-Expires=86400&X-Amz-Signature=b547492f1347bf173328cd2a51c299d7ce9e297475648a398a31e9871d1ab524&X-Amz-SignedHeaders=host)

#### Modifique o arquivo gerado, 'editorconfig', como está abaixo:

```bash
root = true

[*]
indent_style = space
indent_size = 2
charset = utf-8
trim_trailing_whitespace = true
insert_final_newline = true
end_of_line = lf
```

<a id="ancora3.2"></a>
## Configurando ESLint

#### Baixe a dependencia eslint

```bash
yarn add eslint -D
```

#### Inicialize a configuração

```bash
yarn eslint --init
```

1. To check syntax, find problems and enforce code style
2. Javascript modules (import/export)
3. None of these
4. Yes (for TypeScript)
5. Node
6. Use a popular style guide
7. Airbnb
8. JSON
9. No (já que usamos yarn)

#### Adiocione as depedencias manualmente já que não é instalado pelo npm

```bash
yarn add @typescript-eslint/eslint-plugin@latest eslint-config-airbnb-base@latest eslint-plugin-import@^2.21.2 @typescript-eslint/parser@latest -D
```

#### Crie um arquivo na raiz do projeto ```.eslintignore````

```bash
/*.js
node_modules
dist
```

#### No ```.eslintrc.json```:

##### Adicione em ```extends```

```
"plugin:@typescript-eslint/recommended"
```

##### Adicione depois de ```rules```

```
"settings": {
	    "import/resolver": {
	      "typescript": {}
	    }
	  }
```

##### Adicione em ```rules```

```
"import/extensions": [
	      "error",
	      "ignorePackages",
	      {
	        "ts": "never"
	      }
	    ]
```

##### Exemplo:

```
{
    "env": {
        "es2020": true,
        "node": true
    },
    "extends": [
        "airbnb-base",
				"plugin:@typescript-eslint/recommended"
    ],
    "parser": "@typescript-eslint/parser",
    "parserOptions": {
        "ecmaVersion": 2018,
        "sourceType": "module"
    },
    "plugins": [
        "@typescript-eslint"
    ],
    "rules": {
	   	"import/extensions": [
	      "error",
	      "ignorePackages",
	      {
	        "ts": "never"
	      }
	    ]
	  },
	  "settings": {
	    "import/resolver": {
	      "typescript": {}
	    }
	  }
}
```

<a id="ancora3.3"></a>
## Configurando Prettier

#### Instale as dependencias do prettier com eslint

```
yarn add prettier eslint-config-prettier eslint-plugin-prettier -D
```

#### Modifique o arquivo ```.eslintconfig```, na sessão ```extends```

```
"prettier/@typescript-eslint",
"plugin:prettier/recommended"
```

#### E em ```plugins```

```
"prettier"
```

#### Em ```rules```

```
"prettier/prettier": "error"
```

#### Exemplo:

```
{
	...
  "extends": [
		...
    "prettier/@typescript-eslint",
    "plugin:prettier/recommended"
  ],
  ...
  "plugins": [
    ...
    "prettier"
  ],
  "rules": {
    ...
		"prettier/prettier": "error"
  },
  ...
}
```

#### Crie um ```prettier.config.js``` e adicione:

```
module.exports = {
  singleQuote: true,
  trailingComma: 'all',
	arrowParens: 'avoid',
}
```

