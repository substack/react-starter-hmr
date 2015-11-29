# react-starter-hmr

bare-bones [react](https://facebook.github.io/react/) starter
using [babelify](https://npmjs.com/package/babelify) for es6 and jsx
under [browserify](http://browserify.org)/[watchify](https://npmjs.com/package/watchify)
with hot module replacement from [browserify-hmr](https://npmjs.com/package/browserify-hmr)
and [npm run scripts](http://substack.net/task_automation_with_npm_run)

# quick start

```
$ npm install
$ npm start
```

# commands

* `npm start` - start a web server and recompile code for development
* `npm run www` - start a static development web server
* `npm run build` - build for production
* `npm run watch` - automatically recompile during development

# starter code

## main.js

`main.js` is the entry point that sets up the rendering loop. It uses the `ud`
module to replace the `<App />` reference at runtime when any of the files
change.

``` js
var React = require('react')
var ReactDOM = require('react-dom')
var ud = require('ud')
import App from './lib/app.js'

ReactDOM.render(
  React.createElement(ud.defn(module, App), null),
  document.querySelector('#content')
)
```

## lib/app.js

Track a counter `n` as state and increment it when the user clicks a button.

``` js
var React = require('react')
import Times from './times.js'

class App extends React.Component {
  constructor (props) {
    super(props)
    this.state = { n: 0 }
  }
  render () {
    return <div>
      <Times n={this.state.n} />
      <button onClick={this.handleClick.bind(this)}>click me!</button>
    </div>
  }
  handleClick () {
    this.setState({ n: this.state.n + 1 })
  }
}

export default App
```

## lib/times.js

Display the number of clicks.

``` js
var React = require('react')

export default function (props) {
  return <h1>clicked {props.n} times</h1>
}
```

# contributing

If you like what you see, but want to add something more, fork this repo and add
your additional feature to the name of the fork. Try to be specific with the
name of your fork, listing the technologies used plus what features the fork
adds.

# variations

Check out the [list of react-starter-hmr forks](https://github.com/substack/react-starter-hmr/network/members)
and the [list of react-starter forks](https://github.com/substack/react-starter/network/members)
to see how other people have customized this starter repo.

# license

This software is released into the public domain.
