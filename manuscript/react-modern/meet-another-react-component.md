## Apresentando *outro* componente React

Até o momento, utilizamos apenas o componente *App* para criarmos nossa aplicação. Fizemos isso, na seção anterior, expressando tudo o que era preciso para renderizar nossa lista em JSX. Eventualmente, o componente irá escalar, de acordo com suas necessidades, para lidar com tarefas mais complexas. Para facilitar nossa vida, iremos separar algumas responsabilidades em um componente *List* separado:

{title="src/App.js",lang="javascript"}
~~~~~~~
const list = [ ... ];

function App() { ... }

# leanpub-start-insert
function List() {
  return list.map(function(item) {
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
  });
}
# leanpub-end-insert
~~~~~~~

Opcional: Se lhe parecer estranho o fato de que a instrução mais externa do código JSX retornado é escrita em JavaScript, é possível envolvê-la com um elemento HTML, como mostra o código abaixo. Todavia, seguiremos com o código da primeira forma.

{title="src/App.js",lang="javascript"}
~~~~~~~
function List() {
# leanpub-start-insert
  return (
    <div>
      {list.map(function(item) {
# leanpub-end-insert
        return (... );
# leanpub-start-insert
      })}
    </div>
  );
# leanpub-end-insert
}
~~~~~~~

O novo componente *List* pode agora ser utilizado no componente *App*:

{title="src/App.js",lang="javascript"}
~~~~~~~
function App() {
  return (
    <div>
      <h1>My Hacker Stories</h1>

      <label htmlFor="search">Search: </label>
      <input id="search" type="text" />

      <hr />

# leanpub-start-insert
      <List />
# leanpub-end-insert
    </div>
  );
}
~~~~~~~

Você acaba de criar seu primeiro componente React! Com base nesse exemplo, podermos enxergar como funcionam, em aplicações React maiores, componentes que encapsulam tarefas com sentido próprio.

![](images/component-tree.png)

Aplicações React de larga escala possuem uma **hierarquia de componentes** (também chamada de **árvore de componentes**). Costuma haver um componente principal, como **ponto de entrada** (por exemplo, *App*), que "desenrola" a árvore de componentes abaixo dele.  *App* é o **componente pai** da lista e, sendo assim, *List* é um **componente filho** de *App*.

Pensando na árvore de componentes, *App* é também o **componente raiz**, e os componentes que não renderizam nenhum outro são chamados de **componentes folha** (ex. *Item*). *App* pode ter múltiplos filhos, assim como também pode *List*. Se *App* tiver outro componente filho, este será chamado de **componente irmão** de *List*.

### Exercícios:

* Valide seu [código fonte da última seção](https://codesandbox.io/s/github/the-road-to-learn-react/hacker-stories/tree/hs/Meet-another-React-Component).
  * Valide as [mudanças da última seção](https://github.com/the-road-to-learn-react/hacker-stories/compare/hs/Lists-in-React...hs/Meet-another-React-Component?expand=1).
* Estenda a árvore de componentes, obtida no final deste capítulo, com outros possíveis componentes. Tente imaginar que outras partes podem ser extraídas como componentes autônomos.
* Se um componente *Search* é utilizado no componente *App*, quais são as vantagens deste ser um componente irmão de *List*, e não um componente pai ou filho?
* Pergunte a si mesmo: que problemas podem surgir, se continuarmos tratando `list` como uma variável global? Iremos mostrar como tratar esses problemas nas próximas seções do livro.
