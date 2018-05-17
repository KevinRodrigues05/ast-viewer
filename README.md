# ast-viewer

Hosted at `TODO FILL IN`, the ast viewer allows users to quickly parse Python, SQL (Postgres + Transact) and Shell code and inspect the resulting parse trees and abstract syntax trees. This makes development of parsing grammars ([example]) easier, but can also help when writing SCTs to figure out which ASTs are being generated for different submissions.

The AST viewer features 2 modes:

- Editor, where you can add commands in the editor. When clicking 'Submit', your code will be parsed and the corresponding trees are displayed. Mostly for interactive usage and figuring out how to write SCTs.
- Gallery, where you can drop in YAML files with a format like [this one](https://github.com/datacamp/antlr-plsql/blob/master/tests/v0.2.yml). The app will parse all the commands in the YAML file with the specified parser, and generate and display all trees. Mostly for development purposes (visually verify that all parsing still happens correctly after a change is made).

## Run locally

The `ast-viewer` has a front-end in JS (Vue) and a back-end in Python. Both use the grammars generated by [antlr-plsql](https://github.com/datacamp/antlr-plsql) and [antlr-tsql](https://github.com/datacamp/antlr-tsql); the back-end also depends on Osh and `shellwhat`. Because of the myriad dependencies and intricacies with grammar files needing to be in certain places, it is advised to use Docker to run the app.

```
docker build -t sqlwhat-viewer .
docker run -p 3000:3000 sqlwhat-viewer
```

You can now visit http://localhost:3000/static/index.html#/editor and start experimenting with SQL, Python and Shell code. Make sure to update the parser accordingly.

## Running tests

Currently, there are no tests
