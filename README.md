# generator-express-no-stress

![](https://img.shields.io/badge/status-stable-green.svg) [![Codacy Badge](https://api.codacy.com/project/badge/Grade/56c006ccc44c47f49d12b6b35fcf35da)](https://www.codacy.com/app/cdimascio/generator-express-no-stress?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=cdimascio/generator-express-no-stress&amp;utm_campaign=Badge_Grade) ![](https://img.shields.io/badge/license-MIT-blue.svg)

Create awesome [Express.js](www.expressjs.com) applications with best of breed tech including ES.next via [Babel.js](https://babeljs.io/), structured logging with [Pino](https://github.com/pinojs/pino), API validation and interactive documentation via [Swagger](http://swagger.io/), environment based config with [dotenv](https://github.com/motdotla/dotenv), linting with [ESLint](http://eslint.org/), and [Backpack](https://github.com/palmerhq/backpack) powered builds. 

![](https://raw.githubusercontent.com/cdimascio/generator-express-no-stress/master/assets/swagger_node.jpeg)

generator-express-no-stress gets you up and running in seconds. It's ridiculously easy to configure. Heck, just take the defaults. Start it. Write code.

This generator scaffolds a fully functioning REST API server complete with interactive documentation, API validation, structured logging, environment driven config, and more. Simply run the generator and smile :-D


## Install
*Requires Node 6 or greater*

`npm install -g yo generator-express-no-stress`

## Scaffold

`yo express-no-stress myapp`

## Run
#### Run in *development* mode:

```
cd myapp
npm run dev
```

#### Run in *production* mode:

```
npm run compile
npm start
```

#### Deploy to the Cloud
e.g. CloudFoundry

```
cf push myapp
```

## Test

```
npm test
```

## Debug

Run `npm run debug` and attach your favourite inspector!

# Try it!

- Interactive API doc at [http://localhost:3000/api-explorer](http://localhost:3000/api-explorer)
- Landing page at [http://localhost:3000](http://localhost:3000)


## Use Yarn

```
# scaffold
yo express-no-stress myapp --yarn 

# start
cd myapp
npm start
```

## CLI Options

```shell
yo express-no-stress [appname] [--yarn] [--docker]
```

| Option | default | Description |
| --- | --- | --- |
| `appname` | myapp | The application folder |
| `--yarn` | | Use the [`yarn`](https://yarnpkg.com) package manager, instead of `npm` |
| `--docker` | | Install [Docker](https://www.docker.com/) artifacts including a Dockerfile |

## What you get!

- [Express.js](www.expressjs.com) - Fast, unopinionated
, minimalist web framework for Node.js
- [Babel.js](https://babeljs.io/) - Use new syntax, right now without waiting for support
- [Pino](https://github.com/pinojs/pino) - Extremely fast node.js logger, inspired by Bunyan. It also includes a shell utility to pretty-print its log files
- [dotenv](https://github.com/motdotla/dotenv) - Loads environment variables from .env for nodejs projects
- [Backpack](https://github.com/palmerhq/backpack) -  a minimalistic build system for Node.js projects.
- [ESLint](http://eslint.org/) - a pluggable linting utility for JavaScript and JSX
- [Swagger](http://swagger.io/) - is a simple yet powerful representation of your RESTful API.
- [SwaggerUI](http://swagger.io/) - dynamically generate beautiful documentation and sandbox from a Swagger-compliant API


### API Validation

Simply describe your APIs with Swagger and automagically get for free:
- Interactive documentation
- API validation

#### Interactive API Doc
![](https://raw.githubusercontent.com/cdimascio/generator-express-no-stress/master/assets/interactive-doc1.png)


#### API Validation!
Oops! I the API caller forgot to pass a `name` field, no stress, we've got this!

![](https://raw.githubusercontent.com/cdimascio/generator-express-no-stress/master/assets/api-validation.png)



### Structured Logging

Structured logging out of the box! 

#### raw

![](https://raw.githubusercontent.com/cdimascio/generator-express-no-stress/master/assets/logging-raw.png)

#### pretty

Structured logging pretty printed by default - great for dev!

![](https://raw.githubusercontent.com/cdimascio/generator-express-no-stress/master/assets/logging-pretty.png)

### API Validation Example

Simply describe your APIs with Swagger and automatically get:
- API request validation
- Interactive documentation

### example

#### Swagger API spec

```yaml
swagger: "2.0"
info:
  version: 1.0.0
  title: myapp
  description: My cool app
basePath: /api/v1
tags:
  - name: Examples
    description: Simple example endpoints
  - name: Specification
    description: The swagger API specification

consumes:
  - application/json
produces:
  - application/json

definitions:
  ExampleBody:
    type: object
    title: example
    required:
      - name
    properties:
      name:
        type: string
        description: The example name

paths:
  /examples:
    get:
      tags:
        - Examples
      description: Fetch all examples
      responses:
        200:
          description: Returns all examples
    post:
      tags:
        - Examples
      description: Create a new example
      parameters:
        - name: example
          in: body
          description: number of items to skip
          required: true
          schema: 
            $ref: "#/definitions/ExampleBody"
      responses:
        200:
          description: Returns all examples

  /examples/{id}:
    get:
      tags:
        - Examples
      parameters:
        - name: id
          in: path
          required: true
          description: The id of the entity to retrieve
          type: integer
      responses:
        200:
          description: Return the example with the specified id
        404:
          description: Example not 

  /spec:
    get:
      tags:
        - Specification
      responses:
        200:
          description: Return the API specification
```

#### Invoke a POST request via the Interactive doc

![](https://raw.githubusercontent.com/cdimascio/generator-express-no-stress/master/assets/interactive-doc.png)


### Linting

express-no-stress uses [ESLint](http://eslint.org/) with a slightly modified AirBnb [base](https://github.com/airbnb/javascript/tree/master/packages/eslint-config-airbnb-base) configuration. See `.eslintrc.json` to make modifications.

## License

MIT
