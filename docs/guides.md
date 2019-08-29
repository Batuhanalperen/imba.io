---
title: Introduction
---

# What is Imba?

Imba is a new programming language for the web that compiles
to performant JavaScript. It is heavily inspired by ruby and python,
but developed explicitly for web programming (both server and client).
It has language level support for defining, extending, subclassing,
instantiating and rendering dom nodes. For a semi-complex application like 
[TodoMVC](http://todomvc.com), it is more than [10 times faster than React](http://somebee.github.io/todomvc-render-benchmark/index.html)
with less code, and a much smaller library.

```imba
var number = 42
var opposite = true
var string = "the answer is {number}"
var regex = /answer is (\d+)/

var info =
    name: 'Imba'
    version: Imba.VERSION
    repository: 'https://github.com/imba/imba'
    inspiration: ['ruby','python','react','coffeescript']
    creator: 'Sindre Aarsaether'
    contributors: [
        'Sindre Aarsaether' # github.com/somebee
        'Magnus Holm' # github.com/judofyr
        'Slee Woo' # github.com/sleewoo
    ]
```

All snippets of code in the documentation are editable inline,
with highlighting and annotations. It is implemented in [scrimbla](http://github.com/somebee/scrimbla) - an experimental web based editor for imba, written in imba. Don't expect it to work perfectly just yet, but have fun.

The Imba compiler is itself written in Imba, using a custom version of the
Jison parser generator. The command-line version of imba is available as a
node.js utility. The compiler itself does not depend on Node, and can be
run in any JavaScript environment, or in the browser.

> Some people might be confused by the comparison to React. React is a framework, Imba is a language - are these two comparable? [see discussion](https://news.ycombinator.com/item?id=10094371)

# Installation

Get [node](http://nodejs.org) and [npm](http://npmjs.org), then install imba
via npm. If your npm installation is global, you might need to use sudo.

    > npm install -g imba

The imba npm package includes the compiler *and* the runtime. When you want
to use tags and other advanced parts of Imba, you must include the imba runtime
as well. To do this, make sure that you have the imba package installed locally
in your project as well. So, in the root directory of your project, type: 

    > npm install imba --save

This will install imba as a dependency, and add it to your package.json if
you have one set up. Then, make sure to `require 'imba'`, usually
the entry point of your application.

# Usage

Once you have installed Imba (globally), you should have access to three command-line utilties.

### imba

Utility for running imba scripts. Acts as a wrapper around node which can run .imba files (including requires).

`> imba sample.imba` will run the file sample.imba

### imbapack

This is a thin wrapper around webpack, and is the recommended way to build your imba projects. It takes all the same options as webpack, but injects the imba-loader and related extensions and module configuration. This means that you could create a plain webpack.config.js and just run `imbapack` instead of `webpack`. The config can include other loaders and plugins, imbapack should be able to inject the additional config correctly.

### imbac

`> imbac src/` will compile all imba files inside src (recursively). By default, Imba will look for a matching lib/ directory, and save the resulting files there. If no such directory exists, it will save the resulting js files in the same directories as their corresponding imba files.

`> imbac -o out.js input.imba` will compile the file input.imba to out.js

`> imbac -w -o lib/ src/` compiles all files in src to lib, and recopmiles when they are modified

All the other options can bee found by calling `> imbac --help`

# Plugins

Support for Atom and other editors is on the roadmap, but currently Sublime Text 3 is the only official editor/ide for Imba.

### [Sublime Text](https://packagecontrol.io/packages/Imba)

The plugin can be installed through [Package Control](https://packagecontrol.io) (it's called Imba). Or you can install it manually by cloning the
[sublime-imba](https://github.com/somebee/sublime-imba) repository into your Sublime Text Packages/ folder.

### [Atom](https://atom.io/packages/language-imba)

There is an [unofficial Atom plugin](https://atom.io/packages/language-imba) that is based on the sublime text plugin. This does not have integrated highlighting of scoped variables etc, but it should work for basic highlighting.

### [Vim](https://github.com/simeng/vim-imba)

Unofficial plugin or vim, Vimba, can be found at [simeng/vim-imba](https://github.com/simeng/vim-imba). It is very much under development.

### VSCode

A plugin for vscode is underway.

# Examples

Since Imba is a new language, there aren't that many open-source examples out in the wild. It is being used in several 100kloc+ commercial projects, so it should definitely be production-ready.

### [Hello World](https://github.com/imba/hello-world-imba)

Tiny application with webpack/imbapack setup.

### [TodoMVC](https://github.com/somebee/todomvc-imba)

The basic Imba implementation of TodoMVC is a good place to start playing around.

### [Imba.io](https://github.com/somebee/imba.io)

This whole website is written in Imba. It uses the same code for server and client. After the initial load, all navigation in the browser is happening with history push/popState, and rendered directly on the client, yet any hard refresh should land you at the same spot when rendered from the server, thanks to using the same logic for routing as well. Grab it over at [github](https://github.com/somebee/imba.io)


# Tutorials

You can find quite a few tutorials and videos at [scrimba.com](https://scrimba.com/search?q=imba)!
