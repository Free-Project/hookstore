# hookstore-error

[![NPM version](https://img.shields.io/npm/v/hookstore-error.svg?style=flat)](https://npmjs.org/package/hookstore-error)
[![Build Status](https://img.shields.io/travis/react-kit/hookstore.svg?style=flat)](https://travis-ci.org/react-kit/hookstore)
[![Coverage Status](https://img.shields.io/coveralls/react-kit/hookstore.svg?style=flat)](https://coveralls.io/r/react-kit/hookstore)
[![NPM downloads](http://img.shields.io/npm/dm/hookstore-error.svg?style=flat)](https://npmjs.org/package/hookstore-error)

error handler middeware for [hookstore](https://github.com/react-kit/hookstore.git)

## Install

```bash
$ npm install hookstore-error
# or
$ yarn add hookstore-error
```

## Usage

```javascript
import { Provider, applyMiddlewares } from 'hookstore';
import errorHandler from 'hookstore-error';

const model = {
  name: 'foo',
  state: {},
  actions: {},
};

function App() {
  // App component code
}

function Root = () => {
  const middlewares = [
    errorHandler(),
    // add other middlewares
  ];

  applyMiddlewares(middlewares);

  return <Provider model={model}><App /></Provider>;
}

ReactDOM.render(<Root />, document.querySelector('app'));
```

Custom error handle function for yourself:

```javascript
function handleError(err) {
  const { name, action, state } = this.ctx;

  console.error(`${name}/${action} error`, err);
}

const middlewares = [
  errorHandler({ error: handleError }),
  // add other middlewares
];
applyMiddlewares(middlewares);
```

Injoy it!
