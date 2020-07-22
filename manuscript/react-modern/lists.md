## Listas em React

Até o momento, nós renderizamos algumas variáveis primitivas em JSX. A seguir, iremos trabalhar com uma lista de itens. De início, utilizaremos uma amostra de dados e, depois, aplicaremos o que aprendemos com dados obtidos de uma API remota. Vamos, primeiro, definir o *array* como uma variável. Como mostrado anteriormente, podemos definir variáveis dentro ou fora do componente. No código a seguir, optou-se por defini-la fora:

{title="src/App.js",lang="javascript"}
~~~~~~~
import React from 'react';

# leanpub-start-insert
const list = [
  {
    title: 'React',
    url: 'https://reactjs.org/',
    author: 'Jordan Walke',
    num_comments: 3,
    points: 4,
    objectID: 0,
  },
  {
    title: 'Redux',
    url: 'https://redux.js.org/',
    author: 'Dan Abramov, Andrew Clark',
    num_comments: 2,
    points: 5,
    objectID: 1,
  },
];
# leanpub-end-insert

function App() { ... }

export default App;
~~~~~~~

Usei os três pontos (`...`) no final para ajudar a manter o trecho de código pequeno (sem os detalhes de implementação do componente App) e focado nas partes essenciais (a variável `list` fora do componente). Usarei `...` ao longo do livro como um substituto para blocos de código que foram acrescentados em exercícios anteriores. Caso se perca, sempre será possível comparar o seu código com os *links* de CodeSandbox que eu provejo no final da maioria das seções.

Cada item na lista tem um título, uma url, um autor, um identificador (`objectID`), pontos -- que indicam a popularidade de um item -- e uma contagem de comentários. A seguir, renderizamos a lista dentro do código JSX dinamicamente:

{title="src/App.js",lang="javascript"}
~~~~~~~
function App() {
  return (
    <div>
# leanpub-start-insert
      <h1>My Hacker Stories</h1>
# leanpub-end-insert

      <label htmlFor="search">Search: </label>
      <input id="search" type="text" />

# leanpub-start-insert
      <hr />
# leanpub-end-insert

# leanpub-start-insert
      {/* render the list here */}
# leanpub-end-insert
    </div>
  );
}
~~~~~~~

Você pode utilizar o [método map, nativo de arrays JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map), para iterar sobre cada item da lista e retornar uma nova versão de cada:

{title="Code Playground",lang="javascript"}
~~~~~~~
const numbers = [1, 4, 9, 16];

const newNumbers = numbers.map(function(number) {
  return number * 2;
});

console.log(newNumbers);
// [2, 8, 18, 32]
~~~~~~~

No nosso caso, não iremos utilizar *map* para transformar de um tipo de dados JavaScript em outro. Em vez disso, retornaremos um fragmento JSX que renderiza cada item da lista:

{title="src/App.js",lang="javascript"}
~~~~~~~
function App() {
  return (
    <div>
      ...

      <hr />

# leanpub-start-insert
      {list.map(function(item) {
        return <div>{item.title}</div>;
      })}
# leanpub-end-insert
    </div>
  );
}
~~~~~~~

Na realidade, um dos meus primeiros momentos "arrá!" com React foi quando, para mapear uma lista de objetos para elementos HTML, utilizei apenas JavaScript puro, sem qualquer sintaxe com substituição de *templates* ou coisa parecida. É apenas JavaScript com HTML.

![](images/jsx-mapping.png)

React irá exibir cada item agora, mas ainda é possível melhorar seu código, para que ele consiga lidar com listas dinâmicas de forma mais "graciosa". Especificando-se um atributo `key` para cada elemento de "item da lista", React poderá identificar itens modificados mesmo se a lista sofrer alguma outra mudança (por exemplo, reordenação). Felizmente, os itens da nossa lista possuem um identificador:

{title="src/App.js",lang="javascript"}
~~~~~~~
function App() {
  return (
    <div>
      ...

      <hr />

      {list.map(function(item) {
# leanpub-start-insert
        return (
          <div key={item.objectID}>
# leanpub-end-insert
            {item.title}
# leanpub-start-insert
          </div>
        );
# leanpub-end-insert
      })}
    </div>
  );
}
~~~~~~~

Evitamos, se possível, utilizar o índice de cada item do array, para garantir que o atributo *key* é um identificador um pouco mais estável. Caso contrário, se a ordem da lista fosse modificada, React não teria condições de identificar os itens propriamente:

{title="Code Playground",lang="javascript"}
~~~~~~~
// don't do this
{list.map(function(item, index) {
  return (
    <div key={index}>
      ...
    </div>
  );
})}
~~~~~~~

Até agora, apenas o título do item é exibido. Vamos experimentar exibir mais de uma propriedade de cada um:

{title="src/App.js",lang="javascript"}
~~~~~~~
function App() {
  return (
    <div>
      ...

      <hr />

# leanpub-start-insert
      {list.map(function(item) {
        return (
          <div key={item.objectID}>
            <span>
              <a href={item.url}>{item.title}</a>
            </span>
            <span>{item.author}</span>
            <span>{item.num_comments}</span>
            <span>{item.points}</span>
          </div>
        );
      })}
# leanpub-end-insert
    </div>
  );
}
~~~~~~~

A função *map* é colocada *inline* de forma concisa no seu código JSX. Dentro dela, temos acesso a cada item e suas propriedades. A propriedade `url` de cada item é utilizada como um atributo `href` dinâmico para cada *anchor tag*. Não apenas é possível JavaScript ser utilizado no JSX para a exibição de itens, como também para preencher dinamicamente o valor de atributos HTML. 

### Exercícios:

* Veja o [código-fonte da seção anterior](https://codesandbox.io/s/github/the-road-to-learn-react/hacker-stories/tree/hs/Lists-in-React).
  * Confirme as [mudanças em relação à seção passada](https://github.com/the-road-to-learn-react/hacker-stories/compare/hs/React-JSX...hs/Lists-in-React?expand=1).
* Leia sobre a motivação do atributo *key* ([0](https://dev.to/jtonzing/the-significance-of-react-keys---a-visual-explanation--56l7), [1](https://www.robinwieruch.de/react-list-key), [2](https://reactjs.org/docs/lists-and-keys.html)). Não se preocupe se não entender ainda a implementação, apenas concentre-se no problema que pode ocorrer com listas dinâmicas.
* Faça uma revisão sobre [os métodos nativos de array em JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/) -- especialmente *map*, *filter*, e *reduce* -- disponíveis no JavaScript nativo.
* O que acontece no caso de você retornar `null`, ao invés de código JSX?
* Incremente a lista com mais alguns itens, fazendo o exemplo parecer mais realista.
* Pratique o uso diferentes expressões JavaScript em JSX.