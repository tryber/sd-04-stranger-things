# Boas vindas ao repositório do projeto Stranger Things!

Você já usa o GitHub diariamente para desenvolver os exercícios, certo? Agora, para desenvolver os projetos, você deverá seguir as instruções a seguir. Fique atento a cada passo, e se tiver qualquer dúvida, nos envie por Slack! #vqv 🚀

Aqui você vai encontrar os detalhes de como estruturar o desenvolvimento do seu projeto a partir deste repositório, utilizando uma branch específica e um Pull Request para colocar seus códigos.

---

## Instruções para entregar seu projeto:

### ANTES DE COMEÇAR A DESENVOLVER:

1. Clone os **dois** repositórios

- `git clone https://github.com/tryber/sd-0x-stranger-things-backend.git`.
- `git clone https://github.com/tryber/sd-0x-stranger-things-frontend.git`.

2. Navegue entre as pastas dos repositórios que você acabou de clonar

- `cd sd-0x-stranger-things-backend`
- `cd sd-0x-stranger-things-frontend`

3. Instale as dependências dos dois projetos

- `npm install`

3. Para rodar localmentes os projetos, execute o script de start do `package.json`.

- `npm start`

4. Crie uma branch a partir da branch `master` para cada um dos repositórios.

- Verifique que você está na branch `master`
  - Exemplo: `git branch`
- Se não estiver, mude para a branch `master`
  - Exemplo: `git checkout master`
- Agora crie uma branch à qual você vai submeter os `commits` dos seus projetos
  - Você deve criar uma branch no seguinte formato: `nome-de-usuario-nome-do-projeto`
  - Exemplo:
    - `git checkout -b joaozinho-sd-0x-stranger-things-backend`
    - `git checkout -b joaozinho-sd-0x-stranger-things-frontend`

1. Clone o repositório
  * `git clone https://github.com/betrybe/sd-0x-stranger-things.git`.
  * Entre na pasta do repositório que você acabou de clonar:
    * `cd sd-0x-stranger-things`

4. Adicione as mudanças ao _stage_ do Git e faça um `commit`
  * Verifique que as mudanças ainda não estão no _stage_
    * Exemplo: `git status` (deve aparecer listada a pasta _joaozinho_ em vermelho)
  * Adicione o novo arquivo ao _stage_ do Git
      * Exemplo:
        * `git add .` (adicionando todas as mudanças - _que estavam em vermelho_ - ao stage do Git)
        * `git status` (deve aparecer listado o arquivo _joaozinho/README.md_ em verde)
  * Faça o `commit` inicial
      * Exemplo:
        * `git commit -m 'iniciando o projeto x'` (fazendo o primeiro commit)
        * `git status` (deve aparecer uma mensagem tipo _nothing to commit_ )

5. Adicione a sua branch com o novo `commit` ao repositório remoto

  - Usando o exemplo anterior:
    - `git push -u origin joaozinho-sd-0x-stranger-things-backend`
    - `git push -u origin joaozinho-sd-0x-stranger-things-frontend`

6. Crie um novo `Pull Request` _(PR)_
  * Vá até a página de _Pull Requests_ do [repositório no GitHub](https://github.com/tryber/sd-0x-stranger-things/pulls)
  * Clique no botão verde _"New pull request"_
  * Clique na caixa de seleção _"Compare"_ e escolha a sua branch **com atenção**
  * Clique no botão verde _"Create pull request"_
  * Adicione uma descrição para o _Pull Request_ e clique no botão verde _"Create pull request"_
  * **Não se preocupe em preencher mais nada por enquanto!**
  * Volte até a [página de _Pull Requests_ do repositório](https://github.com/tryber/sd-0x-stranger-things/pulls) e confira que o seu _Pull Request_ está criado

---

# Entregáveis

Para entregar o seu projeto você deverá criar um Pull Request em **cada um destes** repositórios:

- [Repositório com o frontend](https://github.com/tryber/sd-0x-stranger-things-frontend);

- [Repositório com o backend](https://github.com/tryber/sd-0x-stranger-things-backend).

Lembre-se que você pode consultar nosso conteúdo sobre [Git & GitHub](https://course.betrybe.com/intro/git/) sempre que precisar!

---

## O que deverá ser desenvolvido

Você vai adaptar e configurar os projetos descritos nesse README para que seja feito o deploy deles. Você vai colocar os projetos frontend e backend no ar com o `Heroku`, utilizando o `PM2` para gerenciar e monitorar os processos. Além disso, você vai alterar alguns comportamentos aplicando os conceitos vistos no conteúdo.

---

## Deploy - Stranger Things

Esse repositório contém as instruções e os requisitos para o projeto de Deploy com Heroku e PM2. O código base para o desenvolvimento do projeto está dividido em duas partes: uma API de backend utilizando Node.js e Express e um frontend com React. Abaixo estão disponíveis os links de acesso aos respectivos repositórios:

- [Repositório com o frontend](https://github.com/tryber/sd-0x-stranger-things-frontend);

- [Repositório com o backend](https://github.com/tryber/sd-0x-stranger-things-backend).

A seguir, temos algumas explicações sobre a estrutura base e alguns comportamentos dessas aplicações. Você explorará esses pontos durante o projeto, alterando o código preexistente.

Lembre-se de que tratam-se de projetos base. Sendo assim, ao longo do desenvolvimento, você vai identificar pontos a serem alterados com o objetivo de aplicar as práticas que vimos durante o curso. Mas não se preocupe, pois no README deste repositório esses pontos estão especificados.

### Backend

O Backend possui a seguinte estrutura:

```
├── README.md
├── index.js
├── data
│  ├── dataset
│  │  └── stranger-things-characters.json
│  └── repository
│     └── StrangerThings.js
├── services
│  └── StrangerThings.js
├── package-lock.json
└── package.json
```

#### API

A API consiste em um serviço simples com um endpoint `/` que retorna uma listagem com os personagens da série **Stranger Things**.

#### Resposta

A lista de personagem possui os seguintes campos:

- **name**: Nome do personagem;

- **status**: se o personagem está vivo ou não na série. Os valores possíveis são `alive`, `deceased` ou `unknown`;

- **origin**: o local de origem do personagem.

A resposta é em formato `JSON`, e o retorno é sempre um array de objetos. Abaixo, um exemplo:

```JSON
[
  {
    "name": "Will",
    "status": "Alive",
    "origin": "Byers Family"
  }
]
```

#### Filtros

Todos os campos da estrutura de retorno da resposta podem ser utilizados como filtros. Para isso, basta passar na `query string` o filtro desejado. No exemplo abaixo, estamos filtrando pelo _nome_ do personagem:

> localhost:3000?name=el

Os filtros são feitos utilizando uma `regex`, buscando pelo texto passado na `query string` em qualquer parte do campo, sem diferenciar maiúsculas de minúsculas.

Nesse caso o retorno seria:

```JSON
[
  {
    "name":"Russell",
    "status":"Alive",
    "origin":"Hawkings Middle School"
  },
  {
    "name":"Eleven",
    "status":"Alive",
    "origin":"Hopper Family"
  }
]
```

#### Modo `upside down` - Backend

Na API, no arquivo `index.js`, há a seguinte variável de controle:

```javascript
const hereIsTheUpsideDown = true;
```

Caso ela seja `true`, a API ativará o modo "Mundo Invertido", conforme a série, e começará a responder desta forma:

```JSON
[
  {
    "name":"llǝssnᴚ",
    "origin":"looɥɔS ǝlppᴉW sƃuᴉʞʍɐH",
    "status":"ǝʌᴉl∀"
  },
  {
    "name":"uǝʌǝlƎ",
    "origin":"ʎlᴉɯɐℲ ɹǝddoH",
    "status":"ǝʌᴉl∀"
  }
]
```

### Frontend

O frontend consiste em um projeto simples utilizando React, que renderizará o seguinte layout:

<img src="assets/frontend.png" width="800px" >

Trata-se de um frontend bem simples que vai se comunicar com a nossa API. Ele possui as seguintes funcionalidades:

- Uma tabela para exibição da resposta da nossa API;

- Um campo de pesquisa para filtro de **nome**;

- Botões de navegação para paginação;

- Um botão para ativar o modo `Mundo Invertido` no frontend.

Todas essas funcionalidades estão implementadas no componente `StrangerThings`.

#### Comunicação com o backend

Na estrutura do projeto, temos um diretório `services`. Nesse diretório, há um arquivo `charactersAPI.js`, onde são feitas as chamadas `HTTP` para a nossa API, utilizando o `axios`.

O service é uma classe que espera receber a URL da nossa API e um timeout para a requisição:

```javascript
{
  url: 'localhost:3003',
  timeout: 30000
}
```

Esses parâmetros estão pré-programados de maneira fixa no componente (alteraremos esse comportamento durante o projeto):

```javascript
const strangerThingsConfig = {
  url: 'localhost:3002',
  timeout: 30000,
};

const upsideDownConfig = {
  url: 'localhost:3003',
  timeout: 30000,
};

const charactersService = new CharactersService(strangerThingsConfig);
const charactersUpsideDownService = new CharactersService(upsideDownConfig);
```

#### Modo `upside down` - Frontend

Assim como no backend, o frontend também possui um modo "Mundo Invertido". Esse modo é ativado e desativado com o botão "Mudar de Realidade".

A ideia é a seguinte: inicialmente, o frontend possui uma imagem de background e utiliza o service instanciado com a configuração contida na variável `strangerThingsConfig`. Ao ativar o Mundo Invertido, a imagem de background é alterada e passamos a utilizar o serviço instanciado com a configuração `upsideDownConfig`.

Desse modo, ao "alternar entre os universos", vamos realizar chamadas a API's diferentes.

No exemplo pré-programado, em um dos "universos", chamamos um serviço na porta `3002` e o outro serviço na porta `3003`. Exploraremos esse comportamento durante o projeto.

#### Monitoramento

Para monitorar sua aplicaçao no heroku usando o dashboard do PM2, siga os passos abaixo:

1.Crie um novo `bucket` no dashboard de monitoramento web do `PM2`. Em seguida, pelo dashboard, adicione as chaves criadas aos `apps` do Heroku criados anteriomente.

2.Deverão ser adicionadas três variáveis para cada app:

   - O nome do server. No caso, utilizaremos um nome diferente para cada um dos apps;

   - Chave pública;

   - Chave privada.

3.Verifique no Dashboard se os processos estão sendo exibidos e monitorados.

## Desenvolvimento

O código não está utilizando variáveis de ambiente. Você vai configurá-lo para utilizá-las, tornando parametrizáveis a porta e o _modo upside down_.

Em seguida, você deverá adicionar o modulo `PM2` ao projeto utilizando o arquivo `ecosystem`, fazendos as adaptações necessárias no `package.json`.

Você vai realizar o deploy do projeto (frontend e backend) no _Heroku_. Para isso, você deverá prepará-los, adicionando os respectivos `Procfiles`. Eles deverão apontar para os scripts adicionados ao `package.json` que utilizam o `PM2`. Por último, você deverá realizar o deploy do projeto, conforme requisitos, no _Heroku_. Os comandos utilizados deverão ser adicionados no README.md de cada projeto. Para mais informações sobre - [Procfiles](https://app.betrybe.com/course/back-end/infrastructure/deploy/heroku#introducao-ao-heroku) e [ecosystem](https://app.betrybe.com/course/back-end/infrastructure/deploy/process-manager#ecosystem-file) visite o Coruse.

Todos esses passos estão detalhados nos requisitos abaixos.

## Requisitos do projeto

Os requisitos estão agrupados por `frontend` e `backend`. Realize as alterações nos respectivos diretórios [disponbilizados para você](#Deploy---Stranger-Things).

### Backend

#### 1 - Variáveis de ambiente

Altere o backend para utilizar variáveis de ambiente para contrololar os seguintes comportamentos:

   1. A porta que a API escutará, essa variável deve ter, nescessáriamente, o nome PORT.

   2. O modo "upsideDown". Essa variável espera um valor boleano e deverá se chamar UPSIDEDOWM_MODE. Lembre-se que as variáveis de ambinte são `strings`.

   O que será testado:
   - Se existe a variável de ambiente PORT.
   - Se a variável de ambiente UPSIDEDOWN_MODE existe e se ela é um boleano.

**Importante**: Para esse projeto, as variáveis de ambiente devem ser definidas em um arquivo .env e o arquivo deve ser enviando no seu PR(Pull Request). ISSO NÃO É UMA PRÁTICA DE MERCADO, o arquivo .env deve ser sempre incluido do .gitignore pois contém informações sensíveis, aqui será enviado apenas por motivo de avaliação.

#### 2 - Módulo PM2

Adicione o módulo PM2 à API.

O que será testado:
 - Se o modulo pm2 esta instalado nas dependências de desenvolvimento.

#### 3 - Ecosystem

Adicione o [arquivo](https://app.betrybe.com/course/back-end/infrastructure/deploy/process-manager#ecosystem-file) `ecosystem.config.yml`. O arquivo deverá realizar as seguintes configurações:

  1. Ativar o Modo Cluster;

  2. Subir duas instâncias do processo;

  3. Não assistir à alterações no diretório (modo`watch` desativado);

  4. Reiniciar o processo caso ele consuma mais de 200MB de memória.

  **importante**: O arquivo `ecosystem` deve ter a extensão yml e não yaml.

  O que será testado:
  - Se o ecosystem tem a propriedade name
  - Se o script a ser executado é o index.js.
  - Se o modo de execução está configurado para cluster.
  - Se o numero de instancias está definido como 2.
  - Se o modo watch esta configurado para estar desativado.
  - Se a reiniciação de memória máxima esta configurada como 200M.

#### 4 - Scripts package.json

Adicione/altere dois `scripts` no `package.json`:

  1. `start`: Deverá iniciar o server utilizando o módulo do `PM2` e apontando para o arquivo `ecosystem` criado;

  2. `start:dev`: Deverá iniciar o server utilizando o módulo do `PM2`, **sem** apontar para o arquivo `ecosystem` e com o parâmetro para "observar alterações no diretório" **ativado**.

Execute ambos em sua máquina para validar se o comportamento é o esperado.

O que será testado:
  - Se o comando `start` inicia o server com pm2 e se usa o ecosystem.
  - Se o comando `start:dev` inicia o server com pm2, se não usa o ecosystem e abre em watchMode.

#### 5 - Procfile

Defina um [arquivo](https://app.betrybe.com/course/back-end/infrastructure/deploy/heroku#introducao-ao-heroku) `Procfile`, utilizando a mesma configuração do script `start` do `package.json`: iniciar o server utilizando o módulo do `PM2`, apontando para o arquivo `ecosystem` criado anteriormente.

Lembre-se: como nossos serviços receberão acessos HTTP externos, precisamos definir os `Dynos` como sendo do tipo `web`.

O que será testado:
- Se o dyno é do tipo web.
- Se o script inicia o server com pm2 e se usa o ecosystem.

#### 6 - Deploy no Heroku

**IMPORTANTE**: Uma variável de ambiente com o nome GITHUB_USER deverá ser criada com o seu usuário do github.

1. Crie dois `apps` do Heroku a partir do mesmo código fonte (código da API). O nome do seu app no heroku deverá conter seu nome de usuário no github seguido de "-hawkins-back" ou "-upside-down-back". Por exemplo, se seu nome de usuário no github for "student" seus app deverão ter o nome:

   - student-hawkins-back;

   - student-upside-down-back.

2. Configure a variável de ambiente criada para controlar o modo `upsideDown`. Cada um dos `apps` deverá ter valores distintos, da seguinte maneira:

   - O app `hawkins` deverá ter o valor `false`;

   - O app `upside-down` deverá ter o valor `true`.

3. Utilizando o `git`, faça o deploy de ambos os `apps` no Heroku.

Acesse os URLs geradas e valide se ambas as API's estão no ar e funcionando como esperado.
**Importante**: As URLS deverão ser geradas pelo heroku e não devem ser modificadas.

O que será testado:
  - Se ao fazer uma requisição do tipo GET para o endpoint da api Hawkins serão retornadas as informações corretas.
  - Se ao fazer uma requisição do tipo GET para o endpoint da api upsideDown serão retornadas as informações corretas.

### Frontend

#### 8 - Variáveis de Ambiente

Altere o frontend para utilizar variáveis de ambiente para controlar as **URLs** e **Timeouts** de comunicação com a API.

Perceba que o código está esperando por duas **APIs**. Uma para o modo `upside-down` e a outra para o modo normal.

O nome das variáveis deve ser o seguinte:
- REACT_APP_HAWKINS_URL e REACT_APP_HAWKINS_TIMEOUT para a URL e o TIMEOUT do seu backend hawkins.
- REACT_APP_UPSIDEDOWN_URL e REACT_APP_UPSIDEDOWN_TIMEOUT para a URL e o TIMEOUT do seu backend UPSIDEDOWN.

O que será testado:
- Se existem as 4 variáveis de ambiente citadas acima.

**Importante**: Para esse projeto, as variáveis de ambiente devem ser definidas em um arquivo .env e o arquivo deve ser enviando no seu PR(Pull Request). ISSO NÃO É UMA PRÁTICA DE MERCADO, o arquivo .env deve ser sempre incluido do .gitignore pois contém informações sensíveis, aqui será enviado apenas por motivo de avaliação.

#### 9 - Deploy do frontend no Heroku
**IMPORTANTE**: Assim como no backend, a variável de ambiente GITHUB_USER

deverá ser criada com o seu usuário do github.

Faça o deploy do front-end:

   1. Crie um app do Heroku com o front-end. Não é necessário a criação do `Procfile` aqui. Vamos deixar o Heroku utilizar as configurações padrões. No momento de criar o app do Heroku, utilize o `buildpack` descrito abaixo, em **Dicas**.

   2. O nome do seu app no heroku deve ser seu nome de usuário do github seguido de "-st-frontend". Por exemplo, se o seu usuário do github for "student", o nome do seu app será "student-st-frontend" e a url ***precisar ser*** https://student-st-frontend.herokuapp.com/.

   2. Configure as variáveis de ambiente do app para apontar para as API's publicadas.

   3. Faça o deploy com o git.

**Dicas**:

Para publicar seu frontend React, utilize o buildpack [mars/create-react-app](https://elements.heroku.com/buildpacks/mars/create-react-app-buildpack).

Lembre-se de que é possível testar o comportamento definindo as variáveis de ambiente em sua máquina. Você pode fazê-las apontar tanto para o backend rodando localmente em sua máquina, quanto para as APIs já publicadas nos requisitos anteriores.

O que será testado:
  - Se ao visitar sua pagina no heroku, o botão de mudar de realidade existe.
  - Se a pesquisa funciona como deveria, fazendo chamada a API externa.
  - Se o botão de mudar de realidade funciona.
  - Se os botões de proxima pagina e pagina anterior funcionam.  

### Bônus

### 10 - Multi-ambientes e Development Mode.

Utilize a estratégia de multi-ambientes no frontend. Para isso:

   - Renomeie o remote atual para `development`;

   - Faça o deploy do novo ambiente, conforme [requisito 9](#9---Deploy-Heroku).

   - O nome do seu novo app no heroku deve ser seu nome de usuário do github seguido de "-st-frontend-prod". Por exemplo, se o seu usuário do github for "student", o nome do seu app será "student-st-frontend-prod" e a url ***precisar ser*** https://student-st-frontend-prod.herokuapp.com/.

   - Adicione um item ao frontend que identifique o layout como rodando em modo de "desenvolvimento". Esse tag item **deve** conter o o texto "Em desenvolvimento"

   - Lembre-se de criar uma variável de ambiente para controlar esse comportamento, e configurá-la nos apps publicados.

O que será testado:
 - Se ao acessar o frontend de desenvolvimento, haverá a tag com o texto "em desenvolvimento"
 - Se ao acessar o frontend de produção, não haverá a tag.

---

### DURANTE O DESENVOLVIMENTO

* Faça `commits` das alterações que você fizer no código regularmente

* Lembre-se de sempre após um (ou alguns) `commits` atualizar o repositório remoto

* Os comandos que você utilizará com mais frequência são:
  1. `git status` _(para verificar o que está em vermelho - fora do stage - e o que está em verde - no stage)_
  2. `git add` _(para adicionar arquivos ao stage do Git)_
  3. `git commit` _(para criar um commit com os arquivos que estão no stage do Git)_
  4. `git push -u nome-da-branch` _(para enviar o commit para o repositório remoto na primeira vez que fizer o `push` de uma nova branch)_
  5. `git push` _(para enviar o commit para o repositório remoto após o passo anterior)_

---

### DEPOIS DE TERMINAR O DESENVOLVIMENTO (OPCIONAL)

Para sinalizar que o seu projeto está pronto para o _"Code Review"_ dos seus colegas, faça o seguinte:

* Vá até a página **DO SEU** _Pull Request_, adicione a label de _"code-review"_ e marque seus colegas:

  * No menu à direita, clique no _link_ **"Labels"** e escolha a _label_ **code-review**;

  * No menu à direita, clique no _link_ **"Assignees"** e escolha **o seu usuário**;

  * No menu à direita, clique no _link_ **"Reviewers"** e digite `students`, selecione o time `tryber/students-sd-0x`.

Caso tenha alguma dúvida, [aqui tem um video explicativo](https://vimeo.com/362189205).

---

### REVISANDO UM PULL REQUEST

Use o conteúdo sobre [Code Review](https://course.betrybe.com/real-life-engineer/code-review/) para te ajudar a revisar os _Pull Requests_.

#VQV
