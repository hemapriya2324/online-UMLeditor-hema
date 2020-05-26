# online-UML-hema
building a online UML editor
A Vue.js, javascript web project
UML online demo client editor
# PlantUML Editor

> A Vue.js, Vuex project

![PlantUML Editor](public1/static1/favicon-60.png)　PlantUML online demo client

![PlantUML Editor](public1/static1/capture1_20170809.png)

[![Netlify Status](https://api.netlify.com/api/v1/badges/0e9c5e9a-b38a-483f-887d-18e4927af717/deploy-status)](https://app.netlify.com/sites/plantuml-editor/deploys)

## Features

- multiple PlantUML templates
- cheat sheet
- snippet
- zoom & scroll
- supports SVG & PNG
- save texts
- create gists
- support markdown
- download image
- print HTML

## Build Setup

```
# install dependencies
npm install

# install flow-typed
npm run flow-typed

# serve with hot reload at localhost:8080
npm run serve

# build for production with minification
npm run build

# run unit tests
npm run test:unit

# run e2e tests
npm run test:e2e
```

## For development

[PlantUML Server with Docker]
PlantUML Server
==============
Requirements
============
 * jre/jdk 1.6.0 or above
 * apache maven 3.0.2 or above
How to run the server
=====================

Just run:

```
mvn jetty:run
```
In this way the server is run on an embedded jetty server.

You can specify the port at which it runs:

```
mvn jetty:run -Djetty.port=9999
```

How to run the server with Docker
=================================

You can run Plantuml with jetty or tomcat container
```
docker run -d -p 8080:8080 plantuml/plantuml-server:jetty
docker run -d -p 8080:8080 plantuml/plantuml-server:tomcat
```


To run plantuml using different base url, change the `docker-compose.yml` file:
~~~
args:
  BASE_URL: plantuml
~~~

And run `docker-compose up --build`. This will build a modified version of the image using
the base url `/plantuml`,

How to set PlantUML options
=================================

You can apply some option to your PlantUML server with environement variable.

If you run the directly the jar, you can pass the option with `-D` flag
```
java -D THE_ENV_VARIABLE=THE_ENV_VALUE -Djetty.contextpath=/ -jar target/dependency/jetty-runner.jar target/plantuml.war
```
or
```
mvn jetty:run -D THE_ENV_VARIABLE=THE_ENV_VALUE -Djetty.port=9999
```

If you use docker, you can use the `-e` flag:
```
docker run -d -p 8080:8080 -e THE_ENV_VARIABLE=THE_ENV_VALUE plantuml/plantuml-server:jetty
```

You can set all  the following variables:

* `PLANTUML_LIMIT_SIZE`
    * Limits image width and height
    * Default value: `4096`
* `GRAPHVIZ_DOT`
    * Link to 'dot' executable
    * Default value: `/usr/local/bin/dot` or `/usr/bin/dot`
* `HTTP_AUTHORIZATION`
    * when calling the `proxy` endpoint, the value of `HTTP_AUTHORIZATION` will be used to set the HTTP Authorization header
    * Default value: `null`
* `ALLOW_PLANTUML_INCLUDE`
    * Enables `!include` processing which can read files from the server into diagrams. Files are read relative to the current working directory.
    * Default value: `false`


How to generate the war
=======================

To build the war, just run:

```
mvn package
```

at the root directory of the project to produce plantuml.war in the target/ directory.


```
docker run -d -p 4000:8080 plantuml/plantuml-server:jetty
```

> **Notice:** The specification of the port number follows `.env.development`
demo link:http://www.plantuml.com/plantuml
