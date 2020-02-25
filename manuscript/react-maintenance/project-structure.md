## React Project Structure

With multiple React components in one file, you might wonder why we didn't put components into different files for the *src/App.js* file from the start. We already have multiple components in the file that can be defined in their own files/folders (also called modules). For learning, it's more practical to keep these components in one place. Once our application grows, we'll consider splitting these components into multiple modules so it scales properly.

Before we restructure our React project, recap [JavaScript's import and export statements](https://www.robinwieruch.de/javascript-import-export). Importing and exporting files are two fundamental concepts in JavaScript you must learn before React. There's no right way to structure a React application, as they evolve naturally along with the project's structure.

We'll complete a simple refactoring for the project's folder/file structure for the sake of learning about the process. Afterward, there will be a few additional options about restructuring this project or React projects in general. You can continue with the restructured project, though we'll continue developing with the *src/App.js* file to keep things simple.

On the command line in your project's folder, navigate into the *src/* folder and create the following component dedicated files:

{title="Command Line",lang="text"}
~~~~~~~
cd src
touch List.js InputWithLabel.js SearchForm.js
~~~~~~~

Move every component from the *src/App.js* file in its own file, except for the List component which has to share its place with the Item component in the *src/List.js* file. Then in every file make sure to import React and to export the component which needs to be used from the file. For instance, in *src/List.js* file:

{title="src/List.js",lang="javascript"}
~~~~~~~
# leanpub-start-insert
import React from 'react';
# leanpub-end-insert

const List = ({ list, onRemoveItem }) =>
  list.map(item => (
    <Item
      key={item.objectID}
      item={item}
      onRemoveItem={onRemoveItem}
    />
  ));

const Item = ({ item, onRemoveItem }) => (
  <div>
    <span>
      <a href={item.url}>{item.title}</a>
    </span>
    <span>{item.author}</span>
    <span>{item.num_comments}</span>
    <span>{item.points}</span>
    <span>
      <button type="button" onClick={() => onRemoveItem(item)}>
        Dismiss
      </button>
    </span>
  </div>
);

# leanpub-start-insert
export default List;
# leanpub-end-insert
~~~~~~~

Since only the List component uses the Item component, we can keep it in the same file. If this changes because the Item component is used elsewhere, we can give the Item component its own file. The SearchForm component in the *src/SearchForm.js* file must import the InputWithLabel component. Like the Item component, we could have left the InputWithLabel component next to the SearchForm; but our goal is to make InputWithLabel component reusable with other components. We'll probably import it eventually.

{title="src/SearchForm.js",lang="javascript"}
~~~~~~~
# leanpub-start-insert
import React from 'react';
# leanpub-end-insert

# leanpub-start-insert
import InputWithLabel from './InputWithLabel';
# leanpub-end-insert

const SearchForm = ({
  searchTerm,
  onSearchInput,
  onSearchSubmit,
}) => (
  <form onSubmit={onSearchSubmit}>
    <InputWithLabel
      id="search"
      value={searchTerm}
      isFocused
      onInputChange={onSearchInput}
    >
      <strong>Search:</strong>
    </InputWithLabel>

    <button type="submit" disabled={!searchTerm}>
      Submit
    </button>
  </form>
);

# leanpub-start-insert
export default SearchForm;
# leanpub-end-insert
~~~~~~~

The App component has to import all the components it needs to render. It doesn't need to import InputWithLabel, because it's only used for the SearchForm component.

{title="src/App.js",lang="javascript"}
~~~~~~~
import React from 'react';
import axios from 'axios';

# leanpub-start-insert
import SearchForm from './SearchForm';
import List from './List';
# leanpub-end-insert

...

const App = () => {
  ...
};

export default App;
~~~~~~~

Components that are used in other components now have their own file. Only if a component (e.g. Item) is dedicated to another component (e.g. List) do we keep it in the same file. If a component should be used as a reusable component (e.g. InputWithLabel), it also receives its own file. From here, there are several strategies to structure your folder/file hierarchy. One scenario is to create a folder for every component:

{title="Project Structure",lang="text"}
~~~~~~~
- List/
-- index.js
- SearchForm/
-- index.js
- InputWithLabel/
-- index.js
~~~~~~~

The *index.js* file holds the implementation details for the component, while other files in the same folder have different responsibilities like styling, testing, and types:

{title="Project Structure",lang="text"}
~~~~~~~
- List/
-- index.js
-- style.css
-- test.js
-- types.js
~~~~~~~

If using CSS-in-JS, where no CSS file is needed, one could still have a separate *style.js* file for all the styled components:

{title="Project Structure",lang="text"}
~~~~~~~
- List/
-- index.js
# leanpub-start-insert
-- style.js
# leanpub-end-insert
-- test.js
-- types.js
~~~~~~~

Sometimes we'll need to move from a **technical-oriented folder structure** to a **domain-oriented folder structure**, especially once the project grows. Universal *shared/* folder is shared across domain specific components:

{title="Project Structure",lang="text"}
~~~~~~~
- Messages.js
- Users.js
- shared/
-- Button.js
-- Input.js
~~~~~~~

If you scale this to the deeper level folder structure, each component will have its own folder in a domain-oriented project structure as well:

{title="Project Structure",lang="text"}
~~~~~~~
- Messages/
-- index.js
-- style.css
-- test.js
-- types.js
- Users/
-- index.js
-- style.css
-- test.js
-- types.js
- shared/
-- Button/
--- index.js
--- style.css
--- test.js
--- types.js
-- Input/
--- index.js
--- style.css
--- test.js
--- types.js
~~~~~~~

There are many ways on how to structure your React project from small to large project: simple to complex folder structure; one-level nested to two-level nested folder nesting; dedicated folders for styling, types and testing next to implementation logic. There is no right way for folder/file structures.

A project's requirements evolve over time and so should its structure. If keeping all assets in one file feels right, then there is no rule against it. Just try to keep the nesting level shallow, otherwise you could get lost deep in folders.

### Exercises:

* Confirm your [source code for the last section](https://codesandbox.io/s/github/the-road-to-learn-react/hacker-stories/tree/hs/React-Folder-Structure).
  * Confirm the [changes from the last section](https://github.com/the-road-to-learn-react/hacker-stories/compare/hs/react-modern-final...hs/React-Folder-Structure?expand=1).
* Read more about [JavaScript's import and export statements](https://www.robinwieruch.de/javascript-import-export).
* Keep the current folder structure if you feel confident. The ongoing sections will omit it, only using the *src/App.js* file.