# bootprint-openapi 

[![NPM version](https://badge.fury.io/js/bootprint-openapi.svg)](http://badge.fury.io/js/bootprint-openapi)
[![Build Status](https://travis-ci.org/nknapp/bootprint-openapi.svg)](https://travis-ci.org/nknapp/bootprint-openapi)
[![Coverage Status](https://img.shields.io/coveralls/nknapp/bootprint-openapi.svg)](https://coveralls.io/r/nknapp/bootprint-openapi)

> Converts a openapi-definition into a static html page

## Overview

This package contains a template, partials and styles for [bootprint](http://npmjs.com/bootprint) to convert
OpenAPI-Specifications into a static HTML-page.

This package was formerly known as `bootprint-swagger` and has been renamed, because 
Swagger-Specification has been renamed to OpenAPI-Specification
## Installation

In order to use `bootprint-openapi` from the command line
you have to install `bootprint` and `bootprint-openapi` globally:

```bash
npm install -g bootprint
npm install -g bootprint-openapi
```

**Check this out:** You can now [try out the new bootprint-openapi playground](http://bootprint.knappmeier.de/).
Just paste a OpenAPI-specification and make it readable. 


## Usage

```
bootprint openapi http://petstore.swagger.io/v2/swagger.json target
```

The directory "target" should now contain a file `index.html` and `main.css` which contain a readable
form of the [Swagger-Petstore-Example](http://petstore.swagger.io/).

For details about command line parameters, please refer to the
[documentation of Bootprint](https://github.com/nknapp/bootprint)

`bootprint-openapi` is just a template-module for `bootprint`. That means, it contains
[LessCss-file](less), [Handlebars-partials](handlebars/partials) and a
[preprocessor](lib/preprocessor.js) that converts
[an OpenAPI-Specification](http://openapis.org) into the JSON actually needed by the templates.

### Create a single file.

If you want to have a single HTML-file, not one HTML and one CSS, you can use substack's [html-inline](https://github.com/substack/html-inline)
package to generate a self-cotnained file:

```
npm -g install html-inline
html-inline target/index.html
```



### Javascript-Usage

The does essentially the same, just in a the above command line, just in JavaScript (i.e. `node`)

```js
// Load bootprint
require('bootprint')
  // Load bootprint-swagger
  .load(require('bootprint-openapi'))
  // Customize configuration, override any options
  .merge({ /* Any other configuration */})
  // Specify build source and target
  .build('http://petstore.swagger.io/v2/swagger.json', 'target')
  // Generate swagger-documentation into "target" directory
  .generate()
  .done(console.log)
```

## API

The API of `bootprint-openapi` consists of Handlebars-partials that can be overridden and
LessCss-Definitions, that can be adapted.

### Handlebars partials
                                               
About 26 Handlebars partials are used to render this openapi-html-page.
The following documentation is not final yet and there are a lot of partials without real documentation, but you may already have a look
at it: The [partials documentation](handlebars-partials.md) describes the partials in use
and the order in which they are called. You can override these partials in a
[Bootprint configuration file](https://github.com/nknapp/bootprint/blob/master/doc/config.md#overriding-and-adding-partials).


## License

`bootprint-openapi` is published under the MIT-license.
See []() for details.

Some of the example specs have been provided by contributors who opened issues on github,
those files are in the `test/*`-directories.

* **test/all-of/swagger.json** [msh321](https://github.com/msh321) (issue #35)
* **test/missing-items/swagger.json** [yewton](https://github.com/yewton) (issue #44)
* **test/path-parameters/swagger.json** [asieira](https://github.com/asieira) (issue #18)
* **test/read-only-property/swagger.json** [asieira](https://github.com/asieira) (issue #28)

## Release-Notes
 
For release notes, see [CHANGELOG.md](CHANGELOG.md)
 
## Contributing guidelines

See [CONTRIBUTING.md](CONTRIBUTING.md).