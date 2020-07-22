## React e JSX

Como mencionei anteriormente, a saída retornada pelo componente App assemelha-se a HTML. Ela é chamada de JSX, que mistura HTML e JavaScript. Vejamos como funciona para exibir a variável:

{title="src/App.js",lang="javascript"}
~~~~~~~
import React from 'react';

const title = 'React';

function App() {
  return (
    <div>
# leanpub-start-insert
      <h1>Hello {title}</h1>
# leanpub-end-insert
    </div>
  );
}

export default App;
~~~~~~~

Inicie sua aplicação com `yarn start` novamente, observando a variável renderizada no navegador, onde lê-se: "Hello React".

Vamos focar no HTML, que é expressado quase que da mesma maneira em JSX. Um campo de *input* com *label* pode ser definido como a seguir: 

{title="src/App.js",lang="javascript"}
~~~~~~~
import React from 'react';

const title = 'React';

function App() {
  return (
    <div>
      <h1>Hello {title}</h1>

# leanpub-start-insert
      <label htmlFor="search">Search: </label>
      <input id="search" type="text" />
# leanpub-end-insert
    </div>
  );
}

export default App;
~~~~~~~

Nós especificamos três atributos HTML aqui: `htmlFor`, `id` e `type`. Enquanto `id` e `type` deveriam ser familiares para quem conhece HTML nativo, `htmlFor` deve ser uma novidade e reflete o atributo `for` de HTML. JSX substitui um punhado de atributos HTML, sendo possível encontrar todos os [atributos suportados](https://reactjs.org/docs/dom-elements.html#all-supported-html-attributes) na documentação de React, seguindo a convenção de nomes *camelCase*. Espere se deparar com mais atributos específicos de JSX, como `className` e `onClick` em vez de `class` e `onclick`, enquanto você segue aprendendo React.

Iremos revisitar o campo de *input* HTML mais tarde, para maiores detalhes de implementação; por agora, retornemos para o JavaScript no JSX. Definimos uma variável do tipo primitivo *string*, para ser exibido no componente App, sendo possível fazer o mesmo com um objeto JavaScript:

{title="src/App.js",lang="javascript"}
~~~~~~~
import React from 'react';

# leanpub-start-insert
const welcome = {
  greeting: 'Hey',
  title: 'React',
};
# leanpub-end-insert

function App() {
  return (
    <div>
      <h1>
# leanpub-start-insert
        {welcome.greeting} {welcome.title}
# leanpub-end-insert
      </h1>

      <label htmlFor="search">Search: </label>
      <input id="search" type="text" />
    </div>
  );
}

export default App;
~~~~~~~

Lembre-se, tudo o que se encontra entre chaves, em um código JSX, pode ser usado para montar expressões JavaScript (por exemplo, chamadas de função):

{title="src/App.js",lang="javascript"}
~~~~~~~
import React from 'react';

# leanpub-start-insert
function getTitle(title) {
  return title;
}
# leanpub-end-insert

function App() {
  return (
    <div>
# leanpub-start-insert
      <h1>Hello {getTitle('React')}</h1>
# leanpub-end-insert

      <label htmlFor="search">Search: </label>
      <input id="search" type="text" />
    </div>
  );
}

export default App;
~~~~~~~

JSX foi inicialmente inventada para React. Mas, tornou-se útil para outras bibliotecas e *frameworks* modernos, depois de crescer em popularidade. É uma das minhas coisas favoritas em React. Sem nenhuma sintaxe de *templates* a mais (com exceção das chaves), estamos aptos a utilizar JavaScript dentro de HTML. 

### Exercícios:

*  Valide seu [código-fonte referente à seção anterior](https://codesandbox.io/s/github/the-road-to-learn-react/hacker-stories/tree/hs/React-JSX).
  * Cheque as [mudanças feitas na seção anterior](https://github.com/the-road-to-learn-react/hacker-stories/compare/hs/Meet-the-React-Component...hs/React-JSX?expand=1).
* Leia mais sobre [React e JSX](https://reactjs.org/docs/introducing-jsx.html).
* Defina mais dados de tipos primitivos e complexos em JavaScript e renderize-os com JSX.
* Tente renderizar um *array* de JavaScript em JSX. Não se preocupe se achar muito complicado, pois você aprenderá mais sobre isso na próxima seção.
