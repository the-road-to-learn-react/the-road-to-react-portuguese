# React's Legacy

React has changed a lot since 2013. The iterations of its library, how React applications are written, and especially its components have all changed drastically. However, many React applications were built over the last few years, so not everything was created with the current status quo in mind. This section of the book covers React's legacy.

I won't cover all that's considered legacy in React, because some features have been revamped more than once. You may see the previous iteration of the feature in older React applications, but will probably be different than the current.

Throughout this section we will compare a [modern React application](https://codesandbox.io/s/github/the-road-to-learn-react/hacker-stories/tree/hs/react-modern-final) to its [legacy version](https://codesandbox.io/s/github/the-road-to-learn-react/hacker-stories/tree/hs/react-legacy). We'll discover that most differences between modern and legacy React are due to class components versus function components.

## React Class Components

React components have undergone many changes, from **createClass components** over **class components**, to **function components**. Going through a React application today, it's likely that we'll see class components next to the modern function components.

{title="Code Playground",lang="javascript"}
~~~~~~~
class InputWithLabel extends React.Component {
  render() {
    const {
      id,
      value,
      type = 'text',
      onInputChange,
      children,
    } = this.props;

    return (
      <>
        <label htmlFor={id}>{children}</label>
        &nbsp;
        <input
          id={id}
          type={type}
          value={value}
          onChange={onInputChange}
        />
      </>
    );
  }
}
~~~~~~~

A typical class component is a JavaScript class with a mandatory **render method** that returns the JSX. The class extends from a `React.Component` to inherit ([class inheritance](https://en.wikipedia.org/wiki/Inheritance_(object-oriented_programming))) all React's component features (e.g. state management for state, lifecycle methods for side-effects). React props are accessed via the class instance (`this`).

For a while class components were the popular choice for writing React applications. Eventually, function components were added, and both co-existed with their distinct purposes side by side:

{title="Code Playground",lang="javascript"}
~~~~~~~
const InputWithLabel = ({
  id,
  value,
  type = 'text',
  onInputChange,
  children,
}) => (
  <>
    <label htmlFor={id}>{children}</label>
    &nbsp;
    <input
      id={id}
      type={type}
      value={value}
      onChange={onInputChange}
    />
  </>
);
~~~~~~~

If no side-effects and no state were used in legacy apps, we'd use a function component instead of a class component. Before 2018--before React Hooks were introduced--React's function components couldn't handle side-effects (`useEffect` hooks) or state (`useState`/`useReducer` hooks). As a result, these components were known as **functional stateless components**,  there only to input props and output JSX. To use state or side-effects, it was necessary to refactor from a function component to a class component. When neither state nor side-effects were used, we used class components or the more lightweight function component.

With the addition of React Hooks, function components worked the same as class components, with state and side-effects. And since there was no longer any practical difference between them, the community chose function components since they are more lightweight.

### Exercises:

* Read more about [JavaScript Classes](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes).
* Read more about [how to refactor from a class component to a function component](https://www.robinwieruch.de/react-hooks-migration).
* Learn more about a different [class component syntax](https://github.com/the-road-to-learn-react/react-alternative-class-component-syntax) which wasn't popular but more effective.
* Read more about [class components in depth](https://reactjs.org/docs/react-component.html).
* Read more about [other legacy and modern component types in React](https://www.robinwieruch.de/react-component-types).

## React Class Components: State

Before React Hooks, class components were superior to function components because they could be stateful. With a class constructor, we can set an initial state for the component. Also, the component's instance (`this`) gives access to the current state (`this.state`) and the component's state updater method (`this.setState`):

{title="Code Playground",lang="javascript"}
~~~~~~~
class App extends React.Component {
  constructor(props) {
    super(props);

# leanpub-start-insert
    this.state = {
      searchTerm: 'React',
    };
# leanpub-end-insert
  }

  render() {
# leanpub-start-insert
    const { searchTerm } = this.state;
# leanpub-end-insert

    return (
      <div>
        <h1>My Hacker Stories</h1>

        <SearchForm
          searchTerm={searchTerm}
# leanpub-start-insert
          onSearchInput={() => this.setState({
            searchTerm: event.target.value
          })}
# leanpub-end-insert
        />
      </div>
    );
  }
}
~~~~~~~

If the state has more than one property in its state object, the `setState` method performs only a shallow update. Only the properties passed to `setState` are overwritten, and all other properties in the state object stay intact. Since state management is important for frontend applications, there was no way around class components without hooks for function components.

In a React class component, there are two dedicated APIs (`this.state` and `this.setState`) to manage a component's state. In a function component, React's useState and useReducer hooks handle this. Related items are packed into one state hook, while a class component must use a general state API. This was one of the major reasons to introduce React Hooks, and move away from class components.

### Exercises:

* Write a stateful class component (e.g. Input).

## Imperative React

In a React function component, React's useRef Hook is used mostly for imperative programming. Throughout React's history, the *ref* and its usage had a few versions:

* String Refs (deprecated)
* Callback Refs
* createRef Refs (exclusive for Class Components)
* useRef Hook Refs (exclusive for Function Components)

Recently, the React team introduced **React's createRef** as the  latest equivalent to a function component's useRef hook:

{title="Code Playground",lang="javascript"}
~~~~~~~
class InputWithLabel extends React.Component {
  constructor(props) {
    super(props);

# leanpub-start-insert
    this.inputRef = React.createRef();
# leanpub-end-insert
  }

  componentDidMount() {
    if (this.props.isFocused) {
# leanpub-start-insert
      this.inputRef.current.focus();
# leanpub-end-insert
    }
  }

  render() {
    ...

    return (
      <>
        ...
        <input
# leanpub-start-insert
          ref={this.inputRef}
# leanpub-end-insert
          id={id}
          type={type}
          value={value}
          onChange={onInputChange}
        />
      </>
    );
  }
}
~~~~~~~

With the helper function, the ref is created in the class' constructor, applied in the JSX for the `ref` attributed, and here used in a lifecycle method. The ref can also be used elsewhere, like focusing the input field on a button click.

Where createRef is used in React's class components, React's useRef Hook is used in React function components. As React shifts towards function components, today its common practice to use the useRef hook exclusively to manage refs and apply imperative programming principles.

### Exercises:

* Read more about [the different ref techniques in React](https://reactjs.org/docs/refs-and-the-dom.html).