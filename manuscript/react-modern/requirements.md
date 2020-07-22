## Requisitos

Para seguir este livro, você precisará estar familiarizado com o básico do desenvolvimento *web*, isto é, como utilizar HTML, CSS e JavaScript. Também ajuda se tiver o entendimento sobre [APIs](https://www.robinwieruch.de/what-is-an-api-javascript/), que serão exploradas ao longo do caminho.

### Editor e Terminal

Eu forneci um [guia de configuração de ambiente](https://www.robinwieruch.de/developer-setup/) para lhe preparar para o desenvolvimento *web* no geral. Aqui, para esta experiência de aprendizado, você precisará de um editor de texto (ex.: Sublime Text) e uma ferramenta de linha de comando (ex.: iTerm) ou uma IDE (ex.: Visual Studio Code). Eu recomendo o Visual Studio Code (também chamado de VS Code) para os iniciantes, pois é uma solução completa que provê um editor avançado com uma ferramenta de linha de comando integrada, além de ser uma escolha popular no meio dos desenvolvedores *web*.

Ao longo do texto, estarei utilizando o termo **linha de comando** e seus aqui sinônimos, **ferramenta de linha de comando**, **terminal** e **terminal integrado**. O mesmo se aplica para os termos **editor**, **editor de texto** e **IDE**, dependendo do quê você decidiu utilizar para sua configuração.

Opcionalmente, eu recomendo manter os projetos no GitHub enquanto nós passamos pelos exercícios neste livro, e também forneci um [pequeno guia](https://www.robinwieruch.de/git-essential-commands/) sobre como utilizar essas ferramentas. O GitHub tem um excelente controle de versão, de forma que voc6e pode ver quais mudanças foram feitas, caso cometa um erro ou apenas queira seguir o conteúdo de modo mais direto. Também é um ótimo jeito de compartilhar seu código com outras pessoas, futuramente.

Se você não quiser configurar editor e terminal (ou IDE) em sua máquina local, o [CodeSandbox](https://codesandbox.io/), um editor *online*, é também uma alternativa viável. Contudo, mesmo sendo o CodeSandbox é uma ótima ferramenta para compartilhamento *online* de código, uma configuração na máquina local é melhor para a experiência e aprendizado das diferentes maneiras de criar uma aplicação *web*. Além disso, se você pretende desenvolver aplicações em um nível profissional, um *setup* local é mandatório.

### Node e NPM

Antes de começarmos, você precisará ter [node and npm](https://nodejs.org/) instalados. Ambos são utilizados no gerenciamento de pacotes *node*, os quais você irá precisar ao longo do caminho. Tais pacotes podem ser bibliotecas ou até *frameworks* inteiros. Iremos instalar pacotes *node* externos via *npm* (*node package manager*).

É possível verificar as versões de *node* e *npm* instaladas em seu computador, via linha de comando, utilizando o comando `node --version`. Caso não obtenha nenhuma saída no terminal, indicando qual versão, significa que ambos deverão ser instalados.

{title="Linha de Comando",lang="text"}
~~~~~~~
node --version
*vXX.YY.ZZ
npm --version
*vXX.YY.ZZ
~~~~~~~

Se você já os tiver instalados, certifique-se de que se trata da versão mais recente. Caso *npm* seja algo novo para você, ou se precisar refrescar a memória, este [curso intensivo de npm](https://www.robinwieruch.de/npm-crash-course) que criei irá lhe ajudar a lhe colocar em condições.