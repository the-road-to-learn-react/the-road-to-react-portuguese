## Configurando um Projeto React

Em "The Road to React", iremos utilizar [create-react-app](https://github.com/facebook/create-react-app) para criar a versão inicial da sua aplicação. Introduzido pelo Facebook em 2016, trata-se de um kit de inicialização que é [recomendado para iniciantes por 96% dos usuários de React](https://twitter.com/dan_abramov/status/806985854099062785). Com *create-react-app*, as ferramentas e configurações 
In the Road to React, we'll use [create-react-app](https://github.com/facebook/create-react-app) to bootstrap your application. It's an opinionated yet zero-configuration starter kit for React introduced by Facebook in 2016, which is [recommended for beginners by 96% of React users](https://twitter.com/dan_abramov/status/806985854099062785). In *create-react-app*, the tools and configurations ficam em segundo plano, enquanto que o foco é a implementação da aplicação em si.

Depois de instalar *Node* e *npm*, use o terminal, digitando o seguinte comando em uma pasta dedicada para seu projeto. Iremos chamá-lo de *hacker-stories*, mas você pode escolher o nome que preferir:  

{title="Linha de Comando",lang="text"}
~~~~~~~
npx create-react-app hacker-stories
~~~~~~~

Quando o *script* inicialização terminar, navegue para a pasta que foi criada:  
Navigate into your new folder after the setup has finished:

{title="Linha de Comando",lang="text"}
~~~~~~~
cd hacker-stories
~~~~~~~

Podemos agora abrir a aplicação em um editor ou IDE. No caso do Visual Studio Code, simplesmente digite `code .` na linha de comando. A seguinte estrutura de pastas (ou uma variação, dependendo da versão do *create-react-app*), deverá ser apresentada:

{title="Estrutura do Projeto",lang="text"}
~~~~~~~
hacker-stories/
--node_modules/
--public/
--src/
----App.css
----App.js
----App.test.js
----index.css
----index.js
----logo.svg
--.gitignore
--package-lock.json
--package.json
--README.md
~~~~~~~

Abaixo, as pastas e arquivos mais importantes que formam a estrutura:

* **README.md:** A extensão *.md* indica que o arquivo é do tipo *markdown*. Markdown é uma linguagem de marcação leve, com sintaxe para formatação de texto simples. Muitos projetos com código-fonte contém um arquivo *README.md*, que dá instruções e informações úteis sobre o projeto. Quando enviamos um projeto para plataformas como GitHub, o arquivo *README.md* geralmente exibe informações sobre o conteúdo do repositório. Por ter usado *create-react-app*, a sua versão desse arquivo é provavelmente igual ao do [repositório oficial do create-react-app no GitHub](https://github.com/facebook/create-react-app).
* **node_modules/:** esta pasta contém todos os pacotes *node* que foram instalados via *npm*. Uma vez que usamos *create-react-app*, um punhado deles já foram adicionados. Não iremos mexer nesta pasta, visto que pacotes *node* são geralmente instalados e removidos com *npm* via linha de comando.
* **package.json:** Este arquivo contém configurações do projeto. Dentre elas, uma lista de pacotes *node* dos quais ele depende.
* **package-lock.json:** Indica como o *npm* irá dividir todas as versões de pacotes *node*. Também não tocaremos neste aquivo.
* **.gitignore:** Exibe todos os arquivos e pastas que não deverão ser adicionados ao seu repositório *git*, quando tais arquivos e pastas devem existir apenas na sua cópia local do projeto. A pasta *node_modules/* é um exemplo, uma vez que é suficiente compartilhar-mos o arquivo *package.json* com outros, para que eles instalem as dependências localmente com `npm install`, sem ter que compartilhar uma pasta inteira.
* **public/:** Pasta contendo arquivos de desenvolvimento do projeto, como *public/index.html*, que é exibido em *localhost:3000* enquanto a aplicação está sendo desenvolvida e em um domínio, quando hospedada em algum lugar. A configuração padrão do projeto relaciona esse *index.html* com todo o código JavaScript da pasta *src/*.

De início, tudo que você precisa está localizado na pasta *src/*. O foco principal está no arquivo *src/App.js*, que é utilizado para implementar componentes React. Será, portanto, utilizado para implementar a sua aplicação. Mais tarde, você poderá querer dividir seus componentes em múltiplos arquivos, cada um contendo um ou mais componentes. 

Adicionalmente, você encontrará um arquivo *src/App.js* para seus testes, e um *src/index.js* como um ponto de entrada para o mundo React. Você irá conhecê-los melhor logo mais, nas próximas seções. Existem também os arquivos *src/index.css* e *src/App.css*, que servem para estilizar sua aplicação e componentes, criado já com o estilo padrão, como pode ser visto quando você os abre. Você também irá modificá-los mais tarde.

Depois de aprender sobre a estrutura de arquivos e pastas do seu projeto React, vamos dar uma olhada nos comandos disponíveis para fazê-lo rodar. Todos os comandos específicos do seu projeto podem ser encontrados no arquivo *package.json*, sob a propriedade *scripts*. Deverão parecer mais ou menos assim:

{title="package.json",lang="javascript"}
~~~~~~~
{
  ...
  },
  "scripts": {
    "start": "react-scripts start",
    "build": "react-scripts build",
    "test": "react-scripts test",
    "eject": "react-scripts eject"
  },
  ...
}
~~~~~~~

Tais *scripts* são executados com o comando `npm run <script>` em um terminal integrado da sua IDE ou na linha de comando. Para os *scripts* `start` e `test`, a palavra `run` pode ser omitida. Veja logo abaixo:

{title="Linha de Comando",lang="text"}
~~~~~~~
# Executa a aplicação em http://localhost:3000
npm start

# Executa os testes
npm test

# Prepara a aplicação para produção
npm run build
~~~~~~~

Outro comando da lista, chamado `eject`, não deve ser utilizando nesta nossa jornada de aprendizado. É um caminho sem volta. Uma vez que você ejete seu projeto, não pode desfazê-lo. Em essência, esse comando está lá para tornar acessíveis todas as ferramentas e configurações do *create-react-app*, para o caso de você não estar satisfeito com as escolhas que foram feitas e quiser mudar alguma coisa. Todavia, aqui manteremos todas as configurações padrão.

### Exercícios:

* Leia um pouco mais a respeito da [documentação da ferramenta create-react-app](https://github.com/facebook/create-react-app) e seu [guia de início rápido](https://create-react-app.dev/docs/getting-started).
  * Leia mais sobre [as funcionalidades de JavaScript suportadas pelo create-react-app](https://create-react-app.dev/docs/supported-browsers-features).
* Leia mais sobre [a estrutura de pastas no create-react-app](https://create-react-app.dev/docs/folder-structure).
  * Navegue através das pastas e arquivos do seu projeto React, um a um.
* Leia mais sobre [os scripts no create-react-app](https://create-react-app.dev/docs/available-scripts).
  * Execute sua aplicação com `npm start` na linha de comando e confira-a funcionando no navegador.
    * Termine a execução na linha de comando, pressionando `Control + C`.
  * Execute o *script* `npm test`.
  * Execute o *script* `npm run build` e confira se uma pasta chamada *build/* foi adicionada ao seu projeto (você pode removê-la, logo em seguida). Note que essa pasta será utilizada mais tarde, para [implantar sua aplicação](https://www.robinwieruch.de/deploy-applications-digital-ocean/).
* Sempre que fizermos alguma mudança de código daqui para frente, não deixe de conferir o resultado no navegador, a fim de ter *feedback* visual.