## Instanciação de Componentes React

Na seção a seguir, iremos fazer uma breve explicação sobre classes em JavaScript, com o intuito de ajudar o entendimento sobre componentes React. É importante notar que, tecnicamente, eles não estão relacionados, mas essa é uma analogia que serve para você entender melhor o conceito de componentes.

Classes são, geralmente, utilizadas em linguagens de programação orientadas a objeto. JavaScript, sempre flexível em seus paradigmas de programação, permite que **programação funcional** e **programação orientada a objetos** co-existam, lado a lado. Para recapitular o assunto de classes para programação OO em JavaScript, considere a seguinte classe *Developer*:

{title="Code Playground",lang="javascript"}
~~~~~~~
class Developer {
  constructor(firstName, lastName) {
    this.firstName = firstName;
    this.lastName = lastName;
  }

  getName() {
    return this.firstName + ' ' + this.lastName;
  }
}
~~~~~~~

Cada classe tem um construtor, que recebe argumentos e os atribui à instância da classe. Ela também pode definir funções associadas a um comportamento (ex. `getName`), chamadas de **métodos** ou **métodos de classe**.

Definir a classe *Developer* é apenas parte do trabalho: instanciá-la é a outra. A definição de classe é o projeto, o desenho técnico de suas capacidades, empregadas quando uma instância é criada com a instrução `new`.

{title="Code Playground",lang="javascript"}
~~~~~~~
// class definition
class Developer { ... }

// class instantiation
const robin = new Developer('Robin', 'Wieruch');

console.log(robin.getName());
// "Robin Wieruch"

// another class instantiation
const dennis = new Developer('Dennis', 'Wieruch');

console.log(dennis.getName());
// "Dennis Wieruch"
~~~~~~~

Se existir uma definição de classe JavaScript, pode-se criar múltiplas instâncias dela. Isso acontece de forma similar com um componente React, que possui apenas **uma** definição de componente, mas pode ter **múltiplas instâncias** deste:

{title="src/App.js",lang="javascript"}
~~~~~~~
// definition of App component
function App() {
  return (
    <div>
      <h1>My Hacker Stories</h1>

      <label htmlFor="search">Search: </label>
      <input id="search" type="text" />

      <hr />

      {/* creating an instance of List component */}
      <List />
      {/* creating another instance of List component */}
      <List />
    </div>
  );
}

// definition of List component
function List() { ... }
~~~~~~~

Uma vez que você definiu um **componente**, podemos utilizá-lo como um **elemento** HTML em qualquer lugar do nosso código JSX. O elemento produz uma **instância de componente**, ou, em outras palavras, o componente é instanciado. Você pode criar quantas instâncias desejar, não muito diferente do que acontece com as definições e uso de classes em JavaScript.

### Exercícios:

* Familiarize-se com os termos *definição de componente*, *instância de componente* e *elemento*.
* Experimente criar múltiplas instâncias do componente *List*.
* Pense a respeito de como seria possível dar, para cada instância de *List*, sua própria lista de valores.