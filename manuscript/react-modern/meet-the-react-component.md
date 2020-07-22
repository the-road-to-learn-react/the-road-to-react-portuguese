## Apresento-lhe um *React Component*

Nosso primeiro componente React está no arquivo *src/App.js*, que deve ser semelhante ao exemplo abaixo. Pode ter leves diferenças, porque o utilitário *create-react-app* às vezes atualiza a estrutura padrão do componente.

{title="src/App.js",lang="javascript"}
~~~~~~~
import React from 'react';
import logo from './logo.svg';
import './App.css';

function App() {
  return (
    <div className="App">
      <header className="App-header">
        <img src={logo} className="App-logo" alt="logo" />
        <p>
          Edit <code>src/App.js</code> and save to reload.
        </p>
        <a
          className="App-link"
          Href="https://reactjs.org"
          target="_blank"
          rel="noopener noreferrer"
        >
          Learn React
        </a>
      </header>
    </div>
  );
}

export default App;
~~~~~~~

Esse arquivo será o nosso foco neste tutorial, até que o contrário seja dito explicitamente. Vamos começar reduzindo o componente à uma versão menor, com menos linhas código geradas pelo *create-react-app* para você entender de início.

{title="src/App.js",lang="javascript"}
~~~~~~~
# leanpub-start-insert
import React from 'react';

function App() {
  return (
    <div>
      <h1>Hello World</h1>
    </div>
  );
}

export default App;
# leanpub-end-insert
~~~~~~~

Primeiramente, esse componente, chamado de "App", nada mais é do que uma função JavaScript. É comumente chamado de **function component**, uma das variações de componentes React (você verá os **tipos de componente** mais tarde). Segundo, o componente *App* ainda não recebe nenhum parâmetro na sua assinatura de função (veremos **props** mais tarde). E, terceiro, o componente *App* retorna código que se assemelha a HTML, chamado de JSX (que também veremos logo mais).

O componente funcional (*function component*) tem detalhes de implementação como qualquer outra função JavaScript. Você os verá em ação, na prática, ao longo da sua jornada com React:

{title="src/App.js",lang="javascript"}
~~~~~~~
import React from 'react';

function App() {
# leanpub-start-insert
  // do something in between
# leanpub-end-insert

  return (
    <div>
      <h1>Hello World</h1>
    </div>
  );
}

export default App;
~~~~~~~

Variáveis definidas no corpo da função serão redefinidas cada vez que ela rodar, como acontece em qualquer função JavaScript:

{title="src/App.js",lang="javascript"}
~~~~~~~
import React from 'react';

function App() {
# leanpub-start-insert
  const title = 'React';
# leanpub-end-insert

  return (
    <div>
      <h1>Hello World</h1>
    </div>
  );
}

export default App;
~~~~~~~

Uma vez que, para definir essa variável, não precisamos de nada que esteja dentro do componente App -- por exemplo, parâmetros na assinatura da função -- podemos defini-la também fora do componente App:

{title="src/App.js",lang="javascript"}
~~~~~~~
import React from 'react';

# leanpub-start-insert
const title = 'React';
# leanpub-end-insert

function App() {
  return (
    <div>
      <h1>Hello World</h1>
    </div>
  );
}

export default App;
~~~~~~~

Iremos utilizar essa variável na próxima seção.

### Exercícios:

* Valide seu [código-fonte da última seção](https://codesandbox.io/s/github/the-road-to-learn-react/hacker-stories/tree/hs/Meet-the-React-Component).
* Se não estiver certo sobre quando utilizar `const`, `let` ou `var` em JavaScript (ou React) para declarações de variáveis, certifique-se de [ler mais sobre as diferenças](https://www.robinwieruch.de/const-let-var).
  * Leia mais sobre [const](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/const).
  * Leia mais sobre [let](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/let).
* Pense a respeito das formas de exibir a variável `title` no HTML retornado do seu componente App. Na próxima seção, iremos colocá-la em uso.