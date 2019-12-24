# React Code Editor

This repo has been migrated to my Projects monorepo here: https://github.com/hamlim/projects/tree/master/packages/react-code-editor.

`@matthamlin/react-code-editor` is an opinionated package built on top of React Hooks and react-simple-code-editor.

It implements a lightweight code editor component that supports the following enhancements:

- Line commenting via `Cmd + /` or `Ctrl + /`
- Format on Save via `Cmd + s` or `Ctrl + s`
- maybe more soon???

## Usage

```jsx
import React from 'react'
import Editor from '@matthamlin/react-code-editor'
import { highlight, languages } from 'prismjs/components/prism-core'
import 'prismjs/components/prism-clike'
import 'prismjs/components/prism-javascript'
import prettier from 'prettier/standalone'
import babelPlugin from 'prettier/parser-babylon'

const code = `import React from "react";
import ReactDOM from "react-dom";
function App() {
  return (
    <h1>Hello world</h1>
  );
}
ReactDOM.render(<App />, document.getElementById("root"));`

function App() {
  return (
    <Editor
      initialValue={code}
      highlight={code => highlight(code, languages.jsx)}
      padding={10}
      style={{
        fontFamily: '"Fira code", "Fira Mono", monospace',
        fontSize: 12,
      }}
      formatOnSave
      formatCode={code =>
        prettier.format(code, { parser: 'babel', plugins: [babelPlugin] })
      }
    />
  )
}
```
