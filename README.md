# tjsx

[![Build Status](https://travis-ci.org/fabiosantoscode/tjsx.svg?branch=master)](https://travis-ci.org/fabiosantoscode/tjsx)

Use React without a transpiler!

## Features

 - No transpilation required! ES6 tagged template string literals are a part of the language!
 - Works on client, server and native.
 - Interops with your existing JSX code. No need to rush!
 - Tiny codebase - you can hope to understand it if you have any problems, and there's a smaller chance of there being bugs.
 - `xml:id` and other XML namespaced attributes simply work! Also SVG namespaced tags such as `<xlink:href>` just work.

## Example

```javascript
const tjsx = require('tjsx')

// Look ma, no transpilers!
function YourComponent({ kind }) {
  const className = `foo foo__${kind}`
  return tjsx`<div className=${className} onClick=${(e) => this.onClick(e)} />`
}
```

## Interpolating strings

```javascript
const tjsx = require('tjsx')

function AmazingTitle({ name = 'Fábio' }) {
  return tjsx`
    <h1>Hello, ${name}</h1>
  `
}
```

## Using other components

```javascript
const tjsx = require('tjsx')
const OneComponent = require('react-some-component')

function AnotherComponent() {
  return tjsx`<div>foo!</div>`
}

function ParentComponent(props) {
  return tjsx`
    <div>
      <${OneComponent} prop1="foo">
        ${props.children}
      </>
      <${AnotherComponent} />
    </div>
  `
}
```
